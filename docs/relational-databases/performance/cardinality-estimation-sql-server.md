---
title: "Оценка количества элементов (SQL Server) | Документация Майкрософт"
ms.custom: 
ms.date: 09/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: performance
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- cardinality estimator
- CE (cardinality estimator)
- estimating cardinality
ms.assetid: baa8a304-5713-4cfe-a699-345e819ce6df
caps.latest.revision: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: c87819c3d2802e6ded39885e540b0a3fd050aae8
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="cardinality-estimation-sql-server"></a>Оценка количества элементов (SQL Server)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  
В этой статье показано, как оценить и выбрать оптимальную конфигурацию оценки количества элементов (CE) для вашей системы SQL. В большинстве систем используется последняя версия CE, поскольку она наиболее точна. CE прогнозирует количество строк, которое скорее всего будет возвращено запросом. Прогноз кратности используется оптимизатором запросов для создания оптимального плана запроса. Чем точнее оценки, тем, как правило, оптимальнее план запроса.  
  
В системе приложения, возможно, существовал важный запрос, план обработки которого был изменен на более медленный с учетом нового CE. Такой запрос может представлять собой следующее:  
  
- Запрос OLTP (оперативной обработки транзакций), который выполняется настолько часто, что несколько экземпляров этого запроса выполняются параллельно.  
- Инструкция SELECT с существенной статистической обработкой, которая выполняется в рабочие часы OLTP.  
  
У вас есть методы определения запроса, который с учетом новых данных CE выполняется медленнее. И у вас есть несколько способов решения проблемы производительности.  
  
  
## <a name="versions-of-the-ce"></a>Версии CE  
  
 В 1998 году основное обновление CE входило в состав Microsoft SQL Server 7.0. Уровень совместимости компонента был равен 70. Последующие обновления выпущены вместе с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] с уровнем совместимости 120 и выше. Обновления CE для уровней 120 и выше включают допущения и алгоритмы, которые хорошо сочетаются с современными хранилищами данных и рабочими нагрузками OLTP.  
  
 **Уровень совместимости:** чтобы убедиться, что база данных находится на определенном уровне, используйте следующий код на языке Transact-SQL для [COMPATIBILITY_LEVEL](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md).  

```sql  
SELECT ServerProperty('ProductVersion');  
go  
  
ALTER DATABASE <yourDatabase>  
    SET COMPATIBILITY_LEVEL = 130;  
go  
  
SELECT d.name, d.compatibility_level  
    FROM sys.databases AS d  
    WHERE d.name = 'yourDatabase';  
go  
```  
  
 В базах данных SQL Server с уровнем совместимости 120 или выше при активации [флага трассировки 9481](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) система принудительно использует CE версии 70.  
  
 **Устаревшая CE**: для базы данных SQL Server с уровнем совместимости 120 или выше CE версии 70 может быть активирована на уровне базы данных с помощью инструкции [ALTER DATABASE SCOPED CONFIGURATION](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md).
  
```sql  
ALTER DATABASE
    SCOPED CONFIGURATION  
        SET LEGACY_CARDINALITY_ESTIMATION = ON;  
go  
  
SELECT name, value  
    FROM sys.database_scoped_configurations  
    WHERE name = 'LEGACY_CARDINALITY_ESTIMATION';  
```  
 
 Или, начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] с пакетом обновления 1 (SP1), используется [указание запроса](../../t-sql/queries/hints-transact-sql-query.md) `USE HINT ('FORCE_LEGACY_CARDINALITY_ESTIMATION')`.
 
 ```sql  
SELECT CustomerId, OrderAddedDate  
    FROM OrderTable  
    WHERE OrderAddedDate >= '2016-05-01'; 
    OPTION (USE HINT ('FORCE_LEGACY_CARDINALITY_ESTIMATION'));  
```
 
 **Хранилище запросов**: появившееся в [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] хранилище запросов является удобным инструментом для анализа производительности запросов. В среде [!INCLUDE[ssManStudio](../../includes/ssManStudio-md.md)] откройте **обозреватель объектов**. Затем откройте узел вашей базы данных; если хранилище запросов включено, вы увидите узел **Хранилище запросов**.  
  
```sql  
ALTER DATABASE <yourDatabase>  
    SET QUERY_STORE = ON;  
go  
  
SELECT  
        q.actual_state_desc AS [actual_state_desc-ofQueryStore],  
        q.desired_state_desc,  
        q.query_capture_mode_desc  
    FROM  
        sys.database_query_store_options  AS q;  
go  
  
ALTER DATABASE <yourDatabase>  
    SET QUERY_STORE CLEAR;  
```  
  
 > [!TIP] 
 > Рекомендуется установить последний выпуск [Management Studio](http://msdn.microsoft.com/library/mt238290.aspx) и регулярно обновлять его.  
  
 Другой способ отслеживания процесса оценки кратности (CE) подразумевает использование расширенного события с именем **query_optimizer_estimate_cardinality**. Следующий пример кода T-SQL выполняется в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Он записывает XEL-файл в папку C:\Temp\ (хотя этот путь можно изменить). При открытии XEL-файла в [!INCLUDE[ssManStudio](../../includes/ssManStudio-md.md)] отображаются подробные сведения об этом файле.  
  
```sql  
DROP EVENT SESSION Test_the_CE_qoec_1 ON SERVER;  
go  
  
CREATE EVENT SESSION Test_the_CE_qoec_1  
    ON SERVER  
    ADD EVENT sqlserver.query_optimizer_estimate_cardinality  
    (  
        ACTION (sqlserver.sql_text)  
            WHERE (  
                sql_text LIKE '%yourTable%'  
                and sql_text LIKE '%SUM(%'  
            )  
    )  
    ADD TARGET package0.asynchronous_file_target   
        (SET  
            filename = 'c:\temp\xe_qoec_1.xel',  
            metadatafile = 'c:\temp\xe_qoec_1.xem'  
        );  
go  
  
ALTER EVENT SESSION Test_the_CE_qoec_1  
    ON SERVER  
    STATE = START;  --STOP;  
go  
```  
  
 Сведения о расширенных событиях, адаптированных для [!INCLUDE[ssSDS](../../includes/sssds-md.md)], см. в разделе [Расширенные события в базе данных SQL](http://azure.microsoft.com/documentation/articles/sql-database-xevent-db-diff-from-svr/).  
  
  
## <a name="steps-to-assess-the-ce-version"></a>Процедура оценки версии CE  
  
 Далее приводятся пошаговые инструкции, позволяющие оценить, не выполняется ли какой-нибудь из важных запросов медленнее с учетом последних данных CE. Для выполнения некоторых шагов нужно выполнить пример кода из предыдущего раздела.  
  
1.  Откройте [!INCLUDE[ssManStudio](../../includes/ssManStudio-md.md)]. Убедитесь, что для базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] задан наивысший доступный уровень совместимости.  
  
2.  Выполните следующие подготовительные действия:  
  
    1.  Откройте [!INCLUDE[ssManStudio](../../includes/ssManStudio-md.md)].  
  
    2.  Запустите T-SQL, чтобы убедиться, что для базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] задан наивысший доступный уровень совместимости.  
  
    3.  Убедитесь, что для базы данных отключена конфигурация `LEGACY_CARDINALITY_ESTIMATION`.  
  
    4.  ОЧИСТИТЕ хранилище запросов. Убедитесь, что хранилище запросов включено.  
  
    5.  Выполните инструкцию `SET NOCOUNT OFF;`.  
  
3.  Выполните инструкцию `SET STATISTICS XML ON;`.  
  
4.  Выполните свой важный запрос.  
  
5.  На вкладке **Сообщения** в области результатов обратите внимание на фактическое число затронутых строк.  
  
6.  На вкладке **Результаты** в области результатов дважды щелкните ячейку, которая содержит статистику в формате XML. Отобразится графический план запроса.  
  
7.  Щелкните правой кнопкой мыши первое поле в графическом плане запроса и нажмите **Свойства**.  
  
8.  Для последующего сравнения с другой конфигурацией обратите внимание на значения следующих свойств:  
  
    -   **CardinalityEstimationModelVersion**.  
  
    -   **Предполагаемое количество строк**.  
  
    -   **Предполагаемые затраты на ввод/вывод**и несколько аналогичных *предполагаемых* свойств, которые имеют отношение к фактической производительности, а не прогнозу числа строк.  
  
    -   **Логическая операция** и **Физическая операция**. *Параллелизм* — хорошее значение.  
  
    -   **Фактический режим выполнения**. *Пакет* — хорошее значение (лучше чем *Строка*).  
  
9. Сравните предполагаемое количество строк с фактическим. Значение CE неточно на 1 % (в любом направлении) или на 10 %?  
  
10. Выполните `SET STATISTICS XML OFF;`.  
  
11. Запустите T-SQL, чтобы снизить уровень совместимости вашей базы данных на 1 (например, со 130 до 120).  
  
12. Повторно выполните все шаги, кроме подготовительных.  
  
13. Сравните значения свойства CE в обоих прогонах.  
  
    - Процент точности с новым CE ниже, чем со старым?  
  
14. Наконец, сравните различные значения свойств производительности в обоих прогонах.  
  
    -   Ваш запрос обрабатывался по двум разным планам из-за того, что оценочные значения CE различались?  
  
    -   Ваш запрос выполнялся медленнее с последним CE?  
  
    -   В большинстве случаев следует использовать последний CE. Исключение составляют ситуации, когда при использовании старого CE запрос обрабатывался быстрее и по другому плану.  
  
    -   В этом случае нужно назначить в системе принудительное использование плана более быстрой обработки и игнорирование CE. Так вы сможете использовать новейший CE во всех операциях, а важный запрос будет выполняться быстрее.  
  
## <a name="how-to-activate-the-best-query-plan"></a>Активация оптимального плана запроса  
  
Допустим, что при использовании нового CE в системе создается план более медленной обработки запроса. Ниже дается несколько рекомендаций, позволяющих активировать план более быстрой обработки.  
  
Можно установить более низкий уровень совместимости (не самый высокий из доступных) для всей базы данных.  
  
- В этом случае активируется старая CE, однако для обработки всех запросов будет использоваться прежнее, менее точное значение CE.  
  
- Кроме того, в этом случае вы не сможете воспользоваться всеми усовершенствованиями, реализованными в оптимизаторе запросов.  
  
Можно использовать команду `LEGACY_CARDINALITY_ESTIMATION`, чтобы задать принудительное использование прежнего значения CE или только конкретного запроса всей базой данных и при этом реализовать усовершенствования оптимизатора запросов.  
  
Для осуществления еще более точного контроля можно назначить *принудительное* использование системой SQL плана, составленного с более старым значением CE во время тестирования. После *закрепления* выбранного плана можно настроить всю базу данных для использования самого высокого уровня совместимости и последнего CE. Далее этот вариант рассматривается более подробно.  
  
### <a name="how-to-force-a-particular-query-plan"></a>Настройка принудительного использования определенного плана запросов  
  
Хранилище запросов предоставляет различные способы для настройки принудительного использования определенного плана запросов в системе:  
  
- Выполните команду **sp_query_store_force_plan**.  
  
- В [!INCLUDE[ssManStudio](../../includes/ssManStudio-md.md)] разверните узел **Хранилище запросов**, щелкните правой кнопкой мыши **Ключевые узлы — потребители ресурсов**, а затем щелкните **Просмотр ключевых узлов — потребителей ресурсов**. На дисплее отображаются кнопки **Принудительное использование плана** и **Отменить принудительное использование плана**.  
  
 Дополнительные сведения о хранилище запросов см. в разделе [Мониторинг производительности с использованием хранилища запросов](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md).  
  
  
## <a name="examples-of-ce-improvements"></a>Примеры улучшения CE  
  
В этом разделе описываются примеры запросов, которые лучше обрабатываются с использованием преимуществ, реализованных в последних выпусках CE. Это справочная информация, не требующая от вас никаких действий.  
  
### <a name="example-a-ce-understands-maximum-value-might-be-higher-than-when-statistics-were-last-gathered"></a>Пример А. Расчет CE выполняется с тем допущением, что максимальное значение может быть больше, чем на момент сбора статистики  
  
Допустим, сбор статистики по параметру OrderTable последний раз выполнялся 30 апреля 2016 года, когда максимальное значение параметра OrderAddedDate было 2016-04-30. Расчет CE для уровня совместимости 120 (и выше) выполняется с допущением, что столбцы в таблице OrderTable с данными *по возрастанию* содержали значения, превышающие записанный в статистике максимум. Исходя из этого план обработки запросов для объектов SQL SELECT оптимизируется следующим образом.  
  
```sql  
SELECT CustomerId, OrderAddedDate  
FROM OrderTable  
WHERE OrderAddedDate >= '2016-05-01';  
```  
  
### <a name="example-b-ce-understands-that-filtered-predicates-on-the-same-table-are-often-correlated"></a>Пример Б. Расчет CE выполняется с допущением, что фильтрованные предикаты в одной и той же таблице часто коррелируют  
  
В следующем примере выполнения инструкции SELECT мы видим фильтрованные предикаты для Model и ModelVariant. Мы интуитивно понимаем, что если Model имеет значение "Xbox", есть вероятность, что ModelVariant имеет значение "One", учитывая, что у "Xbox" был вариант "One".  
  
На уровне 120 расчет CE выполняется с тем допущением, что, возможно, существует корреляция между двумя столбцами одной и той же таблицы: Model и ModelVariant. CE более точно оценивает, сколько строк будет возвращено запросом, а оптимизатор запросов создает оптимизированный план.  
  
```sql  
SELECT Model, Purchase_Price  
FROM dbo.Hardware  
WHERE Model  = 'Xbox'  AND  
      ModelVariant = 'One';  
```  
  
### <a name="example-c-ce-no-longer-assumes-any-correlation-between-filtered-predicates-from-different-tables"></a>Пример В. При расчете CE мы более не допускаем никаких корреляций между фильтрованными предикатами из разных таблиц 
Если провести новое исследование с актуальными рабочими нагрузками и фактическими бизнес-данными, обнаружится, что фильтры предикатов из разных таблиц, как правило, не коррелируют друг с другом. В следующем запросе при расчете CE предполагается, что между s.type и r.date нет никакой корреляции. Следовательно, CE оценивает, что число возвращаемых строк будет меньше.  
  
```sql  
SELECT s.ticket, s.customer, r.store  
FROM dbo.Sales    AS s  
CROSS JOIN dbo.Returns  AS r  
WHERE s.ticket = r.ticket  AND  
      s.type   = 'toy'     AND  
      r.date   = '2016-05-11';  
```  
  
  
## <a name="see-also"></a>См. также:  
 [Наблюдение и настройка производительности](../../relational-databases/performance/monitor-and-tune-for-performance.md)   
 [Оптимизация планов запроса с помощью средства оценки кратности SQL Server 2014](http://msdn.microsoft.com/library/dn673537.aspx)  
 [Указания запросов](../../t-sql/queries/hints-transact-sql-query.md)    
 [Monitoring Performance By Using the Query Store](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)    
 [Руководство по архитектуре обработки запросов](../../relational-databases/query-processing-architecture-guide.md)   
