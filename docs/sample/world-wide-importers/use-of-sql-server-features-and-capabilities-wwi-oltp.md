---
title: Использование SQL Server функций и возможностей | Документы Microsoft
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: ''
ms.component: samples
ms.technology:
- samples
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 06f89721-8478-4abc-8ada-e9c73b08bf51
caps.latest.revision: 2
author: BarbKess
ms.author: barbkess
manager: craigg
robots: noindex,nofollow
ms.workload: Inactive
ms.openlocfilehash: 34535db5b43311e13d21fd663f5302327b24978e
ms.sourcegitcommit: 094c46e7fa6de44735ed0040c65a40ec3d951b75
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/07/2018
---
# <a name="use-of-sql-server-features-and-capabilities"></a>Использование компонентов SQL Server и возможности
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
WideWorldImporters использовать SQL Server функций и возможностей базы данных OLTP.

WideWorldImporters предназначен для демонстрации многие из основных возможностей SQL Server, включая последние функции, представленные в SQL Server 2016. Ниже приведен список компонентов SQL Server и возможности и как они используются в WideWorldImporters описание.

|Компонент SQL Server или возможность использования|Используйте в WideWorldImporters|
|-----------------------------|---------------------|
|Темпоральные таблицы|Существует много временных таблиц, включая все ссылочные таблицы подстановки стиль и основной сущности, такие как StockItems, клиентами и поставщиками. Использование временных таблиц позволяет для удобного отслеживания истории этих сущностей.|
|Вызовы AJAX для JSON|Приложение часто использует вызовы AJAX для запроса этих таблиц: лиц, клиенты, поставщики и StockItems. Вызовы возвращают полезные данные JSON (т. е. данные, возвращаемые форматируется как данные JSON). См., например хранимой процедуры `Website.SearchForCustomers`.|
|Контейнеры JSON свойство значение|Несколько таблиц имеют столбцов, содержащих данные JSON для расширения реляционных данных в таблице. Например `Application.SystemParameters` имеется столбец для параметров приложения и `Application.People` содержит столбец для настройки записей пользователя. Используйте эти таблицы `nvarchar(max)` столбца, чтобы записать данные JSON, а также ограничение CHECK, с помощью встроенной функции `ISJSON` для обеспечения столбец значений, допустимых данных JSON.|
|Безопасность на уровне строк (RLS)|Безопасность на уровне строк (RLS) используется для ограничения доступа к таблице Customers, на основе членства в роли. Каждой территории продаж имеет роли и пользователь. Чтобы увидеть это в действии, используйте соответствующих сценариев в образце script.zip, являющейся частью из [версии образца](http://go.microsoft.com/fwlink/?LinkID=800630).|
|операционной аналитике в режиме реального времени|(Полная версия базы данных) В таблицах транзакций ядра `Sales.InvoiceLines` и `Sales.OrderLines` имеют с некластеризованным индексом для поддержки эффективного выполнения аналитических запросов в транзакционной базе данных с минимальным влиянием на рабочей нагрузки. Выполнение транзакции и аналитика в той же базе данных, также называют [обработки транзакций и Analytical гибридное (HTAP)](https://wikipedia.org/wiki/Hybrid_Transactional/Analytical_Processing_(HTAP)). Чтобы увидеть это в действии, используйте соответствующих сценариев в образце script.zip, являющейся частью из [версии образца](http://go.microsoft.com/fwlink/?LinkID=800630).|
|PolyBase|Для просмотра этого PolyBase в действии, с помощью внешней таблицы с открытый набор данных, размещенные в хранилище Azure блога, используется соответствующий скрипт образец script.zip, являющейся частью из [версии образца](http://go.microsoft.com/fwlink/?LinkID=800630).|
|In-Memory OLTP|(Полная версия базы данных) Табличные типы являются все оптимизированные для памяти, таким образом, возвращающих табличные значения параметров с все преимущества оптимизации памяти.<br/><br/>Две таблицы мониторинга `Warehouse.VehicleTemperatures` и `Warehouse.ColdRoomTemperatures`, являются оптимизированными для памяти. Это позволяет ColdRoomTemperatures таблицы для заполнения с большей скоростью, чем традиционные дисковой таблицы. В таблице VehicleTemperatures содержит полезные данные JSON и пригоден для расширения к IoT сценариев. В таблице VehicleTemperatures пригоден для сценариев, включая EventHubs, Stream Analytics и Power BI.<br/><br/>Хранимая процедура `Website.RecordColdRoomTemperatures` скомпилирован с целью повышения производительности записи холодного температуры комнаты.<br/><br/>Пример In-Memory OLTP в действии см драйвер vehicle расположения рабочей нагрузки в drivers.zip от рабочей нагрузки, которая входит из [версии образца](http://go.microsoft.com/fwlink/?LinkID=800630).|
|Кластеризованный индекс columnstore|(Полная версия базы данных) Таблица `Warehouse.StockItemTransactions` используется в кластеризованном индексе. Ожидаемое число строк в этой таблице может увеличиться, и кластеризованный индекс columnstore значительно уменьшает размер на диске таблицы и повышает производительность запросов. Изменения в этой таблице, доступны только для вставки — нет без обновления и удаления для этой таблицы в рабочей нагрузке интерактивной - и выполняет кластеризованный индекс для вставки рабочих нагрузок.|
|Динамическое маскирование данных|В схеме базы данных маскировки данных, примененных к сведения о банке, удерживаемых для поставщиков, в таблице `Purchasing.Suppliers`. Персонал без прав администратора не будет доступа к этим сведениям.|
|Постоянное шифрование|Демонстрация для постоянного шифрования входит в загружаемый samples.zip, являющейся частью из [версии образца](http://go.microsoft.com/fwlink/?LinkID=800630)... Демонстрация создает ключ шифрования таблицы с помощью шифрования конфиденциальных данных и небольшой образец приложения, который вставляет данные в таблицу.|
|База данных Stretch|`Warehouse.ColdRoomTemperatures` Таблицы реализован как временная таблица и оптимизированными для памяти в полной версии образца базы данных. В архивную таблицу на диске и можно увеличить в Azure.|
|Полнотекстовые индексы|Полнотекстовые индексы улучшают осуществляет поиск сотрудников, клиентов и StockItems. Индексы применяются к запросам, только в том случае, если у вас есть полнотекстовое индексирование, установленных на экземпляре SQL Server. Непостоянные вычисляемый столбец используется для создания данных, который создан полнотекстовый индекс в таблице StockItems.<br/><br/>`CONCAT` используется для объединения поля для создания SearchData, полнотекстовый индекс.<br/>Чтобы включить использование полнотекстовых индексов в образце выполните следующую инструкцию в базе данных:<br/><br/>    `EXECUTE [Application].[Configuration_ConfigureFullTextIndexing]`<br/><br/>В процедуре создается полнотекстовый каталог по умолчанию если один еще не существует, а затем заменяет представления поиска полнотекстового версиями этих представлений).<br/><br/>Обратите внимание, что полнотекстовые индексы для использования в SQL Server требуется, при выборе параметра полнотекстового во время установки. База данных SQL Azure не требуется и конкретной конфигурации, чтобы включить полнотекстовые индексы.|
|Индексированные материализованные вычисляемые столбцы|Индексировать материализованные вычисляемые столбцы, используемые в SupplierTransactions и CustomerTransactions.|
|Проверочные ограничения|— Сравнительно сложная проверочное ограничение в `Sales.SpecialDeals`. Это гарантирует, что один и только один из DiscountAmount DiscountPercentage, и настроить UnitPrice.|
|Ограничения уникальности|Многие многие конструкции (и ограничения уникальности) были настроены для Warehouse.StockItemStockGroups.|
|Секционирование таблиц|(Полная версия базы данных) Таблицы `Sales.CustomerTransactions` и `Purchasing.SupplierTransactions` секционируются по годам, используя функцию секционирования `PF_TransactionDate` и схему секционирования `PS_TransactionDate`. Секционирование позволяет повысить управляемость больших таблиц.|
|Обработка списков|Тип таблицы пример `Website.OrderIDList` предоставляется. Он используется пример процедуры `Website.InvoiceCustomerOrders`. Процедура использует обобщенные табличные выражения (CTE), TRY/CATCH, JSON_MODIFY, XACT_ABORT, NOCOUNT, THROW и XACT_STATE для демонстрирует возможности по обработке список заказов, а не только один заказ, чтобы свести к минимуму циклов приема-передачи из приложения с компонентом database engine.|
|Сжатие GZip|`Warehouse.VehicleTemperature`Показаний датчиков данных содержит таблицу s, но если эти данные старого несколько месяцев, сжимается в целях экономии места, с помощью этой функции COMPRESS, который использует сжатие GZip.<br/><br/>Представление `Website.VehicleTemperatures` функция DECOMPRESS при получении данных, который был сжат.|
|Хранилище запросов|Хранилище запросов включено в базе данных. После выполнения нескольких запросов, открыть базу данных в среде Management Studio, откройте узел хранилища запросов, который находится в базе данных, и Топ ресурсоемких запросов для выполнения запросов и планов для запросов, которые вы только что запустил отчет.|
|STRING_SPLIT|Столбец `DeliveryInstructions` в таблице `Sales.Invoices`имеет значение с разделителями запятыми, который может использоваться для демонстрации STRING_SPLIT.|
|Аудит|Подсистема аудита SQL Server можно включить для этого образца базы данных, выполнив следующую инструкцию в базе данных:<br/><br/>    `EXECUTE [Application].[Configuration_ApplyAuditing]`<br/><br/>В базе данных SQL Azure, аудит включен через [портал Azure](https://portal.azure.com/).<br/><br/>Операции обеспечения безопасности, связанных с именами входа, ролей и разрешений регистрируются во всех системах, где включен аудит (в том числе системы выпуска standard edition). Аудита направляется в журнал приложений, поскольку они доступны во всех системах и не требует дополнительных разрешений. Предупреждение указывает, что для более высокого уровня защиты, он должен перенаправляться в журнал безопасности или в файл в защищенную папку. Приводятся ссылки для описания требуется дополнительная настройка.<br/><br/>Для систем, evaluation и developer или enterprise edition аудите доступа ко всем данным финансовых транзакций.|
