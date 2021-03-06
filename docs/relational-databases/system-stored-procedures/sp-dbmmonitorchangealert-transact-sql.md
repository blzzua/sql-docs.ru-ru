---
title: "sp_dbmmonitorchangealert (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/09/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_dbmmonitorchangealert_TSQL
- sp_dbmmonitorchangealert
dev_langs:
- TSQL
helpviewer_keywords:
- sp_dbmmonitorchangealert
- database mirroring [SQL Server], monitoring
ms.assetid: 1b29f82b-9cf8-4539-8d5c-9a1024db8a50
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 41132fa5fd69036e9bc504628cd353d809d6a0bf
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="spdbmmonitorchangealert-transact-sql"></a>sp_dbmmonitorchangealert (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Добавляет или изменяет пороговое значение предупреждения для указанной метрики производительности зеркального отображения баз данных.  

  
 
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_dbmmonitorchangealert database_name   
    , alert_id   
    , alert_threshold   
    , enabled   
```  
  
## <a name="arguments"></a>Аргументы  
 *database_name*  
 Указывает базу данных, для которой нужно добавить или изменить пороговое значение предупреждения.  
  
 *alert_id*  
 Целочисленное значение, которое определяет добавляемое или изменяемое предупреждение. Укажите одно из следующих значений.  
  
|Значение|Метрика производительности|Пороговое значение предупреждения|  
|-----------|------------------------|-----------------------|  
|1|Самая старая неотправленная транзакция|Указывает количество транзакций за минуту, которые могут накопиться в очереди передачи перед тем, как будет сформировано предупреждение в экземпляре основного сервера. Это предупреждение помогает измерять возможную потерю данных за период времени. Это особенно уместно в режиме высокой производительности. Однако это предупреждение также уместно в режиме высокой безопасности, когда зеркальное отображение приостановлено или прекращено, потому что участники были разъединены.|  
|2|Неотправленный журнал|Указывает, какое количество килобайтов (КБ) неотправленного журнала формирует предупреждение в экземпляре основного сервера. Это предупреждение помогает измерять возможную потерю данных в КБ. Это особенно уместно в режиме высокой производительности. Однако это предупреждение также уместно в режиме высокой безопасности, когда зеркальное отображение приостановлено или прекращено, потому что участники были разъединены.|  
|3|Невосстановленный журнал|Указывает, какое количество килобайтов (КБ) невосстановленного журнала формирует предупреждение в экземпляре зеркального сервера. Это предупреждение помогает вычислить время отработки отказа. *Время отработки отказа* в основном состоит из времени, необходимого бывшему зеркальному серверу для наката всех журналов, оставшихся в его очереди повторов, и небольшого дополнительного времени.|  
|4|Затраты на фиксирование изменений на зеркальном сервере|Указывает количество миллисекунд средней задержки транзакции, которая допустима перед формированием предупреждения на основном сервере. Задержка — это объем дополнительной нагрузки во время ожидания экземпляром основного сервера экземпляра зеркального сервера для добавления записи журнала транзакции в очередь повтора. Это значение уместно только в режиме высокой безопасности.|  
|5|Срок хранения|Метаданные, управляющие длительностью хранения строк в таблице состояния зеркального отображения базы данных.|  
  
 Сведения об идентификаторах событий, соответствующих предупреждениям см. в разделе [пороговых значений предупреждений и оповещений в метриках производительности зеркального отображения &#40; SQL Server &#41; ](../../database-engine/database-mirroring/use-warning-thresholds-and-alerts-on-mirroring-performance-metrics-sql-server.md).  
  
 *alert_threshold*  
 Пороговое значение для предупреждения. Если при обновлении состояния зеркального отображения возвращено значение выше данного порога, в журнал событий Windows будет внесена запись. Это значение, в зависимости от метрики производительности, представлено в KБ, минутах или миллисекундах.  
  
> [!NOTE]  
>  Чтобы просмотреть текущие значения, выполните [sp_dbmmonitorresults](../../relational-databases/system-stored-procedures/sp-dbmmonitorresults-transact-sql.md) хранимой процедуры.  
  
 *включен*  
 Включены ли предупреждения?  
  
 0 = предупреждения отключены.  
  
 1 = предупреждения включены.  
  
> [!NOTE]  
>  Срок хранения всегда включен.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 Нет  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  
  
## <a name="permissions"></a>Разрешения  
 Необходимо членство в предопределенной роли сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
 В следующем примере устанавливаются пороги для каждой метрики производительности и срок хранения для базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]. В следующей таблице представлены значения, использованные в этом примере.  
  
|*alert_id*|Метрика производительности|Пороговое значение предупреждения|Включены ли предупреждения?|  
|-----------------|------------------------|-----------------------|-----------------------------|  
|1|Самая старая неотправленная транзакция|30 минут|Да|  
|2|Неотправленный журнал|10 000 КБ|Да|  
|3|Невосстановленный журнал|10 000 КБ|Да|  
|4|Затраты на фиксирование изменений на зеркальном сервере|1 000 миллисекунд|нет|  
|5|Срок хранения|8 часов|Да|  
  
```  
EXEC sp_dbmmonitorchangealert AdventureWorks2012, 1, 30, 1 ;  
EXEC sp_dbmmonitorchangealert AdventureWorks2012, 2, 10000, 1 ;  
EXEC sp_dbmmonitorchangealert AdventureWorks2012, 3, 10000, 1 ;  
EXEC sp_dbmmonitorchangealert AdventureWorks2012, 4, 1000, 0 ;  
EXEC sp_dbmmonitorchangealert AdventureWorks2012, 5, 8, 1 ;  
```  
  
## <a name="see-also"></a>См. также  
 [Мониторинг зеркального отображения базы данных (SQL Server)](../../database-engine/database-mirroring/monitoring-database-mirroring-sql-server.md)   
 [sp_dbmmonitorhelpalert &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorhelpalert-transact-sql.md)   
 [sp_dbmmonitordropalert (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-dbmmonitordropalert-transact-sql.md)  
  
  
