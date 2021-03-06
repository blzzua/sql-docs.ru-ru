---
title: "Возможности, поддерживаемые различными выпусками SQL Server 2016 | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/23/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
keywords: 
  - "Выпуск SQL"
ms.assetid: 5da61ff5-12b9-48e6-b3c8-0dacca1751c4
caps.latest.revision: 175
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
---
# Возможности, поддерживаемые различными выпусками SQL Server 2016
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  В этом разделе подробно описаны функции, поддерживаемые различными выпусками [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].  
  
 Выпуск SQL Server Evaluation доступен для ознакомления в течение 180 дней.  
  
 Актуальные заметки о выпуске и сведения о новых возможностях содержатся в следующих разделах:
- [Заметки о выпуске для SQL Server 2016](../sql-server/sql-server-2016-release-notes.md)
- [Что нового в SQL Server 2016](../sql-server/what-s-new-in-sql-server-2016.md)

    
 **Оцените SQL Server 2016!**    
    
 > [![Скачать на странице центра оценки](../analysis-services/media/download.png)](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016) **[Скачайте SQL Server 2016 на странице центра оценки](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016)**    
    
> ![Значок виртуальной машины Azure](../analysis-services/media/azure-virtual-machine-small.png) **[Разверните виртуальную машину с уже установленным SQL Server 2016](https://azure.microsoft.com/en-us/marketplace/partners/microsoft/sqlserver2016rtmenterprisewindowsserver2012r2/?wt.mc_id=sqL16_vm)**    
    
  
 Компоненты, поддерживаемые выпусками Evaluation и Developer, перечислены в разделе SQL Server Enterprise Edition.  
  
##  <a name="a-namecross-boxscalelimitsa-scale-limits"></a><a name="Cross-BoxScaleLimits"></a> Ограничения масштабирования  
  
|Компонент|Enterprise|Standard Edition|Web Edition|Express с дополнительными службами|Express| 
|-------------|----------------|--------------|---------|------------------------------------|------------------------|
|Максимальная вычислительная мощность, используемая одним экземпляром, — [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]<sup>1</sup>|Максимум, поддерживаемый операционной системой|Ограничение: меньшее из 4 процессоров и 24 ядер|Ограничение: меньшее из 4 процессоров и 16 ядер|Ограничение: меньшее из 1 процессора и 4 ядер|Ограничение: меньшее из 1 процессора и 4 ядер| 
|Максимальная вычислительная мощность, используемая одним экземпляром, — [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] или [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]|Максимум, поддерживаемый операционной системой|Ограничение: меньшее из 4 процессоров и 24 ядер|Ограничение: меньшее из 4 процессоров и 16 ядер|Ограничение: меньшее из 1 процессора и 4 ядер|Ограничение: меньшее из 1 процессора и 4 ядер|  
|Максимальный объем памяти для буферного пула на экземпляр [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]|Максимум, поддерживаемый операционной системой|128 ГБ|64 ГБ|1410 МБ|1410 МБ|
|Максимальный объем памяти для кэша сегмента Columnstore на экземпляр [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]|Неограниченная память| 32 ГБ<sup>2</sup>| 16 ГБ<sup>2</sup>| 352 ГБ<sup>2</sup>| 352 ГБ<sup>2</sup>|  
|Максимальный размер данных, оптимизированных для памяти, на базу данных в [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]|Неограниченная память| 32 ГБ<sup>2</sup>| 16 ГБ<sup>2</sup>| 352 ГБ<sup>2</sup>| 352 ГБ<sup>2</sup>|  
|Максимальный объем используемой памяти на экземпляр [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]|Максимум, поддерживаемый операционной системой|Табличный: 16 ГБ<br /><br /> MOLAP: 64 ГБ|Недоступно|Недоступно|Недоступно|  
|Максимальный объем используемой памяти на экземпляр [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]|Максимум, поддерживаемый операционной системой|64 ГБ|64 ГБ|4 ГБ|Недоступно|
|Максимальный размер реляционной базы данных|524 ПБ|524 ПБ|524 ПБ|10 ГБ|10 ГБ|  
  
 1. Использование выпуска Enterprise Edition с лицензированием по принципу "лицензия на сервер и клиентские лицензии (Server+CAL)" (недоступно для новых соглашений) ограничено максимум 20 ядрами в расчете на экземпляр SQL Server. В модели лицензирования по числу ядер никаких ограничений нет. Дополнительные сведения см. в разделе [Compute Capacity Limits by Edition of SQL Server](../sql-server/compute-capacity-limits-by-edition-of-sql-server.md).  
  
<sup>2</sup> Применимо к [!INCLUDE[ssSQL15](../includes/sssql15-md.md)] с пакетом обновления 1 (SP1). 

##  <a name="a-namerdbmshaa-rdbms-high-availability"></a><a name="RDBMSHA"></a> Высокий уровень доступности реляционной СУБД  
  
|Компонент|Enterprise|Standard Edition|Web Edition|Express с дополнительными службами|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|Поддержка Server Core <sup>1</sup>|Да|Да|Да|Да|Да|  
|доставка журналов;|Да|Да|Да|Нет|Нет|  
|Зеркальное отображение базы данных|Да|Да<br /><br /> Только полная безопасность|Только следящий сервер|Только следящий сервер|Только следящий сервер| 
|Сжатие резервных копий|Да|Да|Нет|Нет|Нет| 
|Моментальный снимок базы данных|Да|Да <sup>3</sup>|Да <sup>3</sup>|Да <sup>3</sup>|Да <sup>3</sup>|
|Экземпляры отказоустойчивого кластера AlwaysOn|Да<br /><br /> Количество узлов равно максимуму, поддерживаемому операционной системой|Да<br /><br /> Поддержка 2 узлов|Нет|Нет|Нет|  
|Группы доступности AlwaysOn|Да<br /><br /> До 8 вторичных реплик, включая 2 синхронные вторичные реплики|Нет|Нет|Нет|Нет|
|Базовые группы доступности <sup>2</sup>|Нет|Да<br /><br /> Поддержка 2 узлов|Нет|Нет|Нет|
|Директор соединений|Да|Нет|Нет|Нет|Нет|
|Восстановление страниц и файлов в режиме «в сети»|Да|Нет|Нет|Нет|Нет|
|Индексирование в сети|Да|Нет|Нет|Нет|Нет|
|Изменение схемы в режиме «в сети»|Да|Нет|Нет|Нет|Нет|
|Быстрое восстановление|Да|Нет|Нет|Нет|Нет|
|Зеркальные резервные копии|Да|Нет|Нет|Нет|Нет|
|Поддержка памяти и ЦП с "горячей" заменой|Да|Нет|Нет|Нет|Нет|
|Помощник по восстановлению базы данных|Да|Да|Да|Да|Да|
|Зашифрованная резервная копия|Да|Да|Нет|Нет|Нет|
|Гибридное резервное копирование в Microsoft Azure (резервное копирование на URL-адрес)|Да|Да|Нет|Нет|Нет|  
  
 <sup>1</sup> Дополнительные сведения об установке SQL Server 2016 на Server Core см. в разделе [Установка SQL Server 2016 на Server Core](../database-engine/install-windows/install-sql-server-2016-on-server-core.md). 

<sup>2</sup> Дополнительные сведения о базовых группах доступности см. в разделе [Базовые группы доступности](../database-engine/availability-groups/windows/basic-availability-groups-always-on-availability-groups.md).  

<sup>3</sup> Область применения: [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] 2016 с пакетом обновления 1 (SP1).
  
##  <a name="a-namerdbmsspa-rdbms-scalability-and-performance"></a><a name="RDBMSSP"></a> Масштабируемость и производительность реляционной СУБД  
  
|Компонент|Enterprise|Standard Edition|Web Edition|Express с дополнительными службами|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------| 
|Columnstore <sup>1</sup>|Да|Да <sup>2</sup>|Да <sup>2</sup>|Да<sup>2</sup>|Да<sup>2</sup>|  
|Выполняющаяся в памяти OLTP <sup>1</sup>|Да|Да <sup>2</sup>|Да <sup>2</sup>|Да <sup>2</sup>, <sup>3</sup>|Да <sup>2</sup>|
|База данных Stretch|Да|Да|Да|Да|Да|
|Постоянная основная память|Да|Да|Да|Да|Да|
|Поддержка нескольких экземпляров|50|50|50|50|50|
|Секционирование таблиц и индексов|Да|Да <sup>2</sup>|Да <sup>2</sup>|Да <sup>2</sup>|Да <sup>2</sup>|  
|Сжатие данных|Да|Да <sup>2</sup>|Да <sup>2</sup>|Да <sup>2</sup>|Да <sup>2</sup>|
|Регулятор ресурсов|Да|Нет|Нет|Нет|Нет|  
|Параллелизм секционированных таблиц|Да|Нет|Нет|Нет|Нет|
|Несколько контейнеров файлового потока|Да|Да <sup>2</sup>|Да <sup>2</sup>|Да <sup>2</sup>|Да <sup>2</sup>|
|Поддержка NUMA, выделение памяти больших страниц и массива буфера|Да|Нет|Нет|Нет|Нет|
|Расширение буферного пула|Да|Да|Нет|Нет|Нет|
|Управление ресурсами ввода-вывода|Да|Нет|Нет|Нет|Нет|  
|Отложенная устойчивость|Да|Да|Да|Да|Да|

<sup>1</sup> Размер данных выполняющейся в памяти OLTP и кэша сегмента Columnstore ограничены объемом памяти, указанным в выпуске в разделе "Ограничения масштабирования". Максимальная степень параллелизма ограничена. Степень параллелизма процесса (DOP) для построения индекса ограничена значением 2 для выпуска Standard и 1 для выпусков Express и Web. Это относится к индексам columnstore, созданным на основе таблиц на диске и оптимизированных для памяти таблиц.

<sup>2</sup> Применимо к [!INCLUDE[ssSQL15](../includes/sssql15-md.md)] с пакетом обновления 1 (SP1). 

<sup>3</sup> Эта функция не включена в вариант установки LocalDB.
##  <a name="a-namerdbmssa-rdbms-security"></a><a name="RDBMSS"></a> Безопасность реляционной СУБД  
  
|Компонент|Enterprise|Standard Edition|Web|Express|Express с дополнительными службами|  
|-------------|----------------|--------------|---------|-------------|------------------------------------| 
|Безопасность на уровне строк|Да|Да|Да <sup>1</sup>|Да <sup>1</sup>|Да <sup>1</sup>|  
|Постоянное шифрование|Да|Да <sup>1</sup>|Да <sup>1</sup>|Да <sup>1</sup>|Да <sup>1</sup>| 
|Динамическое маскирование данных|Да|Да|Да <sup>1</sup>|Да <sup>1</sup>|Да <sup>1</sup>|   
|Основные возможности аудита|Да|Да|Да|Да|Да| 
|Аудит мелких фрагментов данных|Да|Да <sup>1</sup>|Да <sup>1</sup>|Да <sup>1</sup>|Да <sup>1</sup>| 
|Прозрачное шифрование в базе данных|Да|Нет|Нет|Нет|Нет|   
|Расширенное управление ключами (Extensible Key Management)|Да|Нет|Нет|Нет|Нет| 
|Определяемые пользователем роли|Да|Да|Да|Да|Да| 
|Автономные базы данных|Да|Да|Да|Да|Да| 
|Шифрование для резервного копирования|Да|Да|Нет|Нет|Нет|  

<sup>1</sup> Область применения: [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] 2016 с пакетом обновления 1 (SP1).  
##  <a name="a-namereplicationa-replication"></a><a name="Replication"></a> Репликация  
  
|Компонент|Enterprise|Standard Edition|Web Edition|Express с дополнительными службами|Express|   
|-------------|----------------|--------------|---------|------------------------------------|------------------------| 
|Разнородные подписчики|Да|Да|Нет|Нет|Нет|  
|Репликация слиянием|Да|Да|Да (только подписчик)|Да (только подписчик)|Да (только подписчик)|   
|публикация Oracle|Да|Нет|Нет|Нет|Нет| 
|Одноранговая репликация транзакций|Да|Нет|Нет|Нет|Нет|   
|репликация моментальных снимков;|Да|Да|Да (только подписчик)|Да (только подписчик)|Да (только подписчик)|   
|Отслеживание изменений в SQL Server|Да|Да|Да|Да|Да| 
|Репликация транзакций|Да|Да|Да (только подписчик)|Да (только подписчик)|Да (только подписчик)|   
|Репликация транзакций в Azure|Да|Да|Да|Нет|Нет|   
|Обновляемая подписка репликации транзакций|Да|Нет|Нет|Нет|Нет|  
  
##  <a name="a-namessmsa-management-tools"></a><a name="SSMS"></a> Средства управления  
  
|Компонент|Enterprise|Standard Edition|Web Edition|Express с дополнительными службами|Express| 
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|Объекты SMO|Да|Да|Да|Да|Да|  
|Диспетчер конфигурации SQL Server|Да|Да|Да|Да|Да|   
|SQL CMD (программа командной строки)|Да|Да|Да|Да|Да|      
|Распределенное воспроизведение — средство администрирования|Да|Да|Да|Да|Нет|  
|Распределенное воспроизведение — клиент|Да|Да|Да|Нет|Нет|  
|Распределенное воспроизведение — контроллер|Да (до 16 клиентов)|Да (1 клиент)|Да (1 клиент)|Нет|Нет|   
|SQL Profiler|Да|Да|Нет <sup>1</sup>|Нет <sup>1</sup>|Нет <sup>1</sup>|  
|SQL Server, агент|Да|Да|Да|Нет|Нет| 
|Пакет управления Microsoft System Center Operations Manager|Да|Да|Да|Нет|Нет|  
|Помощник по настройке ядра СУБД (DTA)|Да|Да <sup>2</sup>|Да <sup>2</sup>|Нет|Нет|      
  
 <sup>1</sup> Для выпусков SQL Server Web Edition, SQL Server Express, SQL Server Express с инструментами и SQL Server, экспресс-выпуск с дополнительными службами, поддерживается профилирование с помощью выпусков SQL Server Standard Edition и SQL Server Enterprise Edition.  
  
 <sup>2</sup> Настройка включена только для компонентов выпуска Standard Edition.  
  
##  <a name="a-namerdbmsma-rdbms-manageability"></a><a name="RDBMSM"></a> Управление реляционной СУБД  
  
|Компонент|Enterprise|Standard Edition|Web Edition|Express с дополнительными службами|Express|   
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|Пользовательские экземпляры|Нет|Нет|Нет|Да|Да| 
|LocalDB|Нет|Нет|Нет|Да|Нет| 
|Выделенное административное соединение|Да|Да|Да|Да, с помощью флага трассировки|Да, с помощью флага трассировки|   
|Поддержка скриптов PowerShell|Да|Да|Да|Да|Да| 
|Поддержка SysPrep <sup>1</sup>|Да|Да|Да|Да|Да| 
|Поддержка операций с компонентами приложения уровня данных — извлечение, развертывание, обновление, удаление|Да|Да|Да|Да|Да| 
|Автоматизация политики (проверка по расписанию и изменение)|Да|Да|Да|Нет|Нет|   
|Сборщик данных производительности|Да|Да|Да|Нет|Нет| 
|Возможность регистрации в качестве управляемого экземпляра в среде управления несколькими экземплярами|Да|Да|Да|Нет|Нет|   
|Стандартный производительности отчет|Да|Да|Да|Нет|Нет| 
|Структуры планов и закрепление плана для структур планов|Да|Да|Да|Нет|Нет|   
|Прямой запрос индексированных представлений (с использованием указания NOEXPAND)|Да|Да|Да|Да|Да| 
|Автоматическое сопровождение индексированного представления|Да|Да|Да|Нет|Нет| 
|Распределенные секционированные представления|Да|Нет|Нет|Нет|Нет| 
|Параллельные операции с индексами|Да|Нет|Нет|Нет|Нет|  
|Автоматическое использование индексированного представления оптимизатором запросов|Да|Нет|Нет|Нет|Нет| 
|Проверка согласованности параллелизма|Да|Нет|Нет|Нет|Нет| 
|Точка управления служебной программой SQL Server|Да|Нет|Нет|Нет|Нет|    
|Расширение буферного пула|Да|Да|Нет|Нет|Нет| 
  
 <sup>1</sup> Дополнительные сведения см. в разделе [Вопросы по установке SQL Server с помощью SysPrep](../database-engine/install-windows/considerations-for-installing-sql-server-using-sysprep.md).  
 
<sup>2</sup> Область применения: [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] 2016 с пакетом обновления 1 (SP1). 
  
##  <a name="a-namedevtoolsa-development-tools"></a><a name="DevTools"></a> Средства разработки  
  
|Компонент|Enterprise|Standard Edition|Web Edition|Express с дополнительными службами|Express| 
|-------------|----------------|--------------|---------|------------------------------------|------------------------| 
|Интеграция со средой Microsoft Visual Studio|Да|Да|Да|Да|Да| 
|Технология IntelliSense (Transact-SQL и многомерные выражения)|Да|Да|Да|Да|Да| 
|SQL Server Data Tools (SSDT)|Да|Да|Да|Да|Нет|    
|Средства изменения, отладки и проектирования многомерных выражений|Да|Да|Нет|Нет|Нет|   
  
##  <a name="a-nameprogrammabilitya-programmability"></a><a name="Programmability"></a> Программирование  
  
|Компонент|Enterprise|Standard Edition|Web Edition|Express с дополнительными службами|Express 
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|Базовая интеграция R|Да|Да|Да|Да|Нет|   
|Продвинутая интеграция R|Да|Нет|Нет|Нет|Нет| 
|R Server (Standalone)|Да|Нет|Нет|Нет|Нет|   
|Вычислительный узел PolyBase|Да|Да <sup>1</sup>|Да <sup>1</sup>, <sup>2</sup>|Да <sup>1</sup>, <sup>2</sup>|Да <sup>1</sup>, <sup>2</sup>| 
|Головной узел PolyBase|Да|Нет|Нет|Нет|Нет| 
|JSON|Да|Да|Да|Да|Да|   
|Хранилище запросов|Да|Да|Да|Да|Да|   
|Temporal|Да|Да|Да|Да|Да|   
|Интеграция со средой CLR|Да|Да|Да|Да|Да|   
|Собственная поддержка XML|Да|Да|Да|Да|Да| 
|Индексирование XML|Да|Да|Да|Да|Да| 
|Возможности MERGE & UPSERT|Да|Да|Да|Да|Да|   
|поддержка FILESTREAM|Да|Да|Да|Да|Да| 
|FileTable|Да|Да|Да|Да|Да| 
|Типы данных даты и времени|Да|Да|Да|Да|Да|  
|Поддержка международного использования|Да|Да|Да|Да|Да| 
|Семантический поиск и полнотекстовый поиск|Да|Да|Да|Да|Нет| 
|Определение языка в запросе|Да|Да|Да|Да|Нет|   
|Компонент Service Broker (сообщения)|Да|Да|Нет (только клиент)|Нет (только клиент)|Нет (только клиент)|   
|конечные точки в языке Transact-SQL|Да|Да|Да|Нет|Нет| 

<sup>1</sup> Для масштабного развертывания с несколькими вычислительными узлами требуется головной узел.

<sup>2</sup> Область применения: [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] 2016 с пакетом обновления 1 (SP1).
  
## <a name="a-nameisa-integration-services"></a><a name="IS"></a> Службы Integration Services

Сведения о функциях служб Integration Services (SSIS), поддерживаемых различными выпусками [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)], см. в статье [Функции, поддерживаемые различными выпусками SQL Server 2016](Integration%20Services%20Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.md).

##  <a name="a-namemdsa-master-data-services"></a><a name="MDS"></a> Службы Master Data Services  
 Сведения о функциях [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] и служб Data Quality Services, поддерживаемых различными выпусками [!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)], см. в разделе [Функции Master Data Services и Data Quality Services, поддерживаемые различными выпусками SQL Server 2016](../master-data-services/master data services and data quality services features support.md). 

  
##  <a name="a-namedwa-data-warehouse"></a><a name="DW"></a> Хранилище данных  
  
|Компонент|Enterprise|Standard Edition|Web Edition|Express с дополнительными службами|Express|   
|-------------|----------------|--------------|---------|------------------------------------|------------------------| 
|Создание кубов без базы данных|Да|Да|Нет|Нет|Нет |   
|Автоматическое создание промежуточных схем и схем хранилища данных|Да|Да|Нет|Нет|Нет| 
|Система отслеживания измененных данных|Да|Да <sup>1</sup>|Да <sup>1</sup>|Нет|Нет| 
|Оптимизация запросов с соединением типа «звезда»|Да|Нет|Нет|Нет|Нет| 
|Масштабируемая конфигурация служб Analysis Services, доступная только для чтения|Да|Нет|Нет|Нет|Нет| 
|Параллельная обработка запросов для секционированных таблиц и индексов|Да|Нет|Нет|Нет|Нет|   
|Глобальная статистическая обработка пакета|Да|Нет|Нет|Нет|Нет| 

<sup>1</sup> Применимо к [!INCLUDE[ssSQL15_md](../includes/sssql15-md.md)] с пакетом обновления 1 (SP1).  
##  <a name="a-namessasa-analysis-services"></a><a name="SSAS"></a> Службы Analysis Services  
  
Сведения о функциях служб Analysis Services, поддерживаемых различными выпусками [!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)], см. в разделе [Функции служб Analysis Services, поддерживаемые различными выпусками SQL Server 2016](../analysis-services/analysis-services-features-supported-by-the-editions-of-sql-server-2016.md). 
  
##  <a name="a-namebimda-bi-semantic-model-multi-dimensional"></a><a name="BIMD"></a> Семантическая модель бизнес-аналитики (многомерная)  
  
Сведения о функциях служб Analysis Services, поддерживаемых различными выпусками [!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)], см. в разделе [Функции служб Analysis Services, поддерживаемые различными выпусками SQL Server 2016](../analysis-services/analysis-services-features-supported-by-the-editions-of-sql-server-2016.md).
   
##  <a name="a-namebita-bi-semantic-model-tabular"></a><a name="BIT"></a> Семантическая модель бизнес-аналитики (табличная)  
  
Сведения о функциях служб Analysis Services, поддерживаемых различными выпусками [!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)], см. в разделе [Функции служб Analysis Services, поддерживаемые различными выпусками SQL Server 2016](../analysis-services/analysis-services-features-supported-by-the-editions-of-sql-server-2016.md).
  
##  <a name="a-nameppspa-power-pivot-for-sharepoint"></a><a name="PPSP"></a> Power Pivot для SharePoint  
  
Сведения о функциях Power Pivot для SharePoint, поддерживаемых различными выпусками [!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)], см. в разделе [Функции служб Analysis Services, поддерживаемые различными выпусками SQL Server 2016](../analysis-services/analysis-services-features-supported-by-the-editions-of-sql-server-2016.md).
  
##  <a name="a-namedma-data-mining"></a><a name="DM"></a> Интеллектуальный анализ данных  
  
Сведения о функциях интеллектуального анализа данных, поддерживаемых различными выпусками [!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)], см. в разделе [Функции служб Analysis Services, поддерживаемые различными выпусками SQL Server 2016](../analysis-services/analysis-services-features-supported-by-the-editions-of-sql-server-2016.md).
  
##  <a name="a-namessrsa-reporting-services"></a><a name="SSRS"></a> Службы Reporting Services  
  
Сведения о функциях служб Reporting Services, поддерживаемых различными выпусками [!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)], см. в разделе [Функции служб Reporting Services, поддерживаемые различными выпусками SQL Server 2016](../reporting-services/reporting-services-features-supported-by-the-editions-of-sql-server-2016.md).

##  <a name="a-namebica-business-intelligence-clients"></a><a name="BIC"></a> Клиенты бизнес-аналитики  

Сведения о функциях клиента бизнес-аналитики, поддерживаемых различными выпусками [!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)], см. в разделе [Функции служб Analysis Services, поддерживаемые различными выпусками SQL Server 2016](../analysis-services/analysis-services-features-supported-by-the-editions-of-sql-server-2016.md) или [Возможности служб Reporting Services, поддерживаемые различными выпусками SQL Server 2016](../reporting-services/reporting-services-features-supported-by-the-editions-of-sql-server-2016.md).
  
##  <a name="a-nameslsa-spatial-and-location-services"></a><a name="SLS"></a> Пространственные службы и службы определения местоположения  
  
|Имя функции|Enterprise|Standard Edition|Web Edition|Express с дополнительными службами|Express|  
|------------------|----------------|--------------|---------|------------------------------------|------------------------|
|Пространственные индексы|Да|Да|Да|Да|Да|   
|Плоский и геодезический типы данных|Да|Да|Да|Да|Да| 
|Дополнительные пространственные библиотеки|Да|Да|Да|Да|Да|   
|Импорт-экспорт стандартных форматов пространственных данных|Да|Да|Да|Да|Да|   
  
##  <a name="a-nameadsa-additional-database-services"></a><a name="ADS"></a> Дополнительные службы базы данных  
  
|Имя функции|Enterprise|Standard Edition|Web Edition|Express с дополнительными службами|Express|   
|------------------|----------------|--------------|---------|------------------------------------|------------------------| 
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Помощник по миграции|Да|Да|Да|Да|Да|   
|Компонент Database Mail|Да|Да|Да|Нет|Нет| 
  
##  <a name="a-nameothera-other-components"></a><a name="Other"></a> Другие компоненты  
  
|Имя функции|Enterprise|Standard Edition|Web Edition|Express с дополнительными службами|Express|   
|------------------|----------------|--------------|---------|------------------------------------|------------------------|  
|StreamInsight|StreamInsight Premium Edition|StreamInsight Standard Edition|StreamInsight Standard Edition|Нет|Нет| 
|StreamInsight HA|StreamInsight Premium Edition|Нет|Нет|Нет|Нет|   
  
> [![Скачать SSMS](../analysis-services/media/download.png)](https://msdn.microsoft.com/library/mt238290.aspx) **[Скачайте последнюю версию SQL Server Management Studio](https://msdn.microsoft.com/library/mt238290.aspx)**    
  
## <a name="see-also"></a>См. также:  
 [Спецификации SQL Server 2016](../Topic/Product%20Specifications%20for%20SQL%20Server%202016.md)   
 [Установка SQL Server 2016](../database-engine/install-windows/installation-for-sql-server-2016.md)  
  
  