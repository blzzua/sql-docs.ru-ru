---
title: Пользовательский интерфейс текстового конструктора запросов (построитель отчетов) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: ''
ms.component: report-data
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- "10010"
helpviewer_keywords:
- query designers, text-based
ms.assetid: 89fddca5-bd96-4128-9072-5348d1b6e02c
caps.latest.revision: 15
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: a7ec1e4a1b2b9f96dc14e7190ac2212254a5c5ff
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/09/2018
---
# <a name="text-based-query-designer-user-interface-report-builder"></a>Пользовательский интерфейс текстового конструктора запросов (построитель отчетов)
  Текстовый конструктор запросов предназначен для ввода запроса на языке запросов, поддерживаемом источником данных, его выполнения и просмотра результатов во время разработки. Можно указать несколько инструкций, запросов или команд языка [!INCLUDE[tsql](../../includes/tsql-md.md)] для создания собственных модулей обработки данных, а также указать запросы, заданные как выражения. Поскольку текстовый конструктор запросов не выполняет предварительную обработку запроса и позволяет использовать любой синтаксис запросов, он представляет собой стандартное средство конструктора запросов для источников данных многих типов.  
  
> [!IMPORTANT]  
>  При создании и выполнении запросов пользователи получают доступ к источникам данных. Следует предоставить минимальные разрешения на источники данных, например разрешение только на чтение.  
  
 В окне текстового конструктора запросов отображаются панель инструментов и следующие две области.  
  
-   **Запрос** Показывает текст запроса, имя таблицы или имя хранимой процедуры, в зависимости от типа запроса. Не все типы запросов поддерживаются всеми типами источников данных. Например, имя таблицы поддерживается только для типа источника данных OLE DB.  
  
-   **Результат** Показывает результаты выполнения запроса во время разработки.  
  
## <a name="text-based-query-designer-toolbar"></a>Панель инструментов текстового конструктора запросов  
 Текстовый конструктор запросов предоставляет одну панель инструментов для всех типов команд. В следующей таблице перечислены все кнопки панели инструментов и их функции.  
  
|Кнопка|Description|  
|------------|-----------------|  
|**Редактировать как текст**|Переключиться из текстового конструктора запросов в графический и обратно. Не все источники данных поддерживают графические конструкторы запросов.|  
|**Импорт**|Импорт существующего запроса из файла или отчета. Поддерживаются только SQL-файлы и RDL-файлы.|  
|![Выполнить запрос](../../reporting-services/report-data/media/rsqdicon-run.gif "Выполнить запрос")|Выполнить запрос и показать результирующий набор в панели результатов.|  
|**Тип команды**|Выберите **Text**, **StoredProcedure**или **TableDirect**. Если хранимая процедура имеет параметры, при нажатии на панели инструментов кнопки **Выполнить** появится диалоговое окно **Определение параметров запроса** , в котором можно ввести значения параметров. Поддержка типов команд зависит от типа источника данных. Например, **TableDirect**поддерживают только OLE DB и ODBC.<br /><br /> Примечание. Если хранимая процедура возвращает несколько результирующих наборов, для заполнения набора данных значениями используется только первый из них.|  
  
### <a name="command-type-text"></a>Тип команды Text  
 При создании набора данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] конструктор реляционных запросов открывается по умолчанию. Чтобы переключиться в текстовый конструктор запросов, нажмите кнопку переключателя **Редактировать как текст** на панели инструментов. В окне текстового конструктора запросов отображаются две панели: панель запросов и область результатов. На следующем рисунке показана каждая панель.  
  
 ![Конструктор универсальных запросов с запросом реляционных данных](../../reporting-services/report-data/media/rsqd-dsaw-sql-generic.gif "Конструктор универсальных запросов с запросом реляционных данных")  
  
 В следующей таблице описываются функции каждой панели.  
  
|Панель|Компонент|  
|----------|--------------|  
|Запрос|Отображает текст запроса [!INCLUDE[tsql](../../includes/tsql-md.md)] . Используйте эту панель, чтобы написать или изменить запрос [!INCLUDE[tsql](../../includes/tsql-md.md)] .|  
|Результат|Отображает результаты запроса. Чтобы выполнить запрос, щелкните правой кнопкой мыши любую область и выберите команду **Выполнить**либо нажмите кнопку **Выполнить** на панели инструментов.|  
  
#### <a name="example"></a>Пример  
 Следующий запрос возвращает список имен из таблицы **ContactType** базы данных AdventureWorks2014 для схемы **Person** :  
  
```  
SELECT Name FROM Person.ContactType  
```  
  
 При нажатии кнопки **Выполнить** на панели инструментов выполняется команда на панели **Запрос** , а результаты выводятся на панели **Результат** . Результирующий набор отображает список из 20 типов контактов, например владельца или агента по продажам.  
  
### <a name="command-type-storedprocedure"></a>Тип команды StoredProcedure  
 Если выбран **Тип команды StoredProcedure**, то текстовый конструктор запросов содержит две панели: панель запросов и область результатов. Введите имя хранимой процедуры в области «Запрос» и нажмите кнопку **Выполнить** на панели инструментов. Если хранимые процедуры используют параметры, откроется диалоговое окно **Определение параметров запроса** . Введите значения параметров для хранимой процедуры. Параметр отчета создается для каждого входного параметра хранимой процедуры.  
  
 На следующем рисунке показаны области «Запрос» и «Результаты» при выполнении хранимой процедуры. В данном случае входные параметры являются константами.  
  
 ![Хранимая процедура в конструкторе текстовых запросов](../../reporting-services/report-data/media/rs-relational-text-sp.gif "Хранимая процедура в конструкторе текстовых запросов")  
  
 В следующей таблице описываются функции каждой панели.  
  
|Панель|Компонент|  
|----------|--------------|  
|Запрос|Отображает имя хранимой процедуры и все входные параметры.|  
|Результат|Отображает результаты запроса. Чтобы выполнить запрос, щелкните правой кнопкой мыши любую область и выберите команду **Выполнить**либо нажмите кнопку **Выполнить** на панели инструментов.|  
  
#### <a name="example"></a>Пример  
 Следующий запрос вызывает хранимую процедуру **uspGetWhereUsedProductID**AdventureWorks2014. При запуске этого запроса необходимо задать значение параметра с идентификационным номером продукта.  
  
```  
uspGetWhereUsedProductID  
```  
  
 Нажмите кнопку **Выполнить** (**!**). При получении запроса на ввод параметров введите значения из следующей таблицы.  
  
|||  
|-|-|  
|*@StartProductID*|820|  
|*@CheckDate*|20010115|  
  
 Для указанной даты результирующий набор отображает список из 13 идентификаторов продуктов, которые используют указанный номер компонента.  
  
### <a name="command-type-tabledirect"></a>Тип команды TableDirect  
 Если выбран **Тип команды TableDirect**, то текстовый конструктор запросов содержит две панели: панель запросов и область результатов. Если ввести имя таблицы и нажать кнопку **Выполнить** , возвращаются все столбцы этой таблицы.  
  
#### <a name="example"></a>Пример  
 Для типа источника данных OLE DB следующий запрос к набору данных возвращает результирующий набор для всех типов контактов в базе данных AdventureWorks2014.  
  
 `Person.ContactType`  
  
 Ввод имени таблицы Person.ContactType эквивалентен созданию на языке [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкции `SELECT * FROM Person.ContactType`.  
  
## <a name="see-also"></a>См. также:  
 [Пользовательский интерфейс конструктора реляционных запросов (построитель отчетов)](../../reporting-services/report-data/relational-query-designer-user-interface-report-builder.md)   
 [Конструкторы запросов (построитель отчетов)](http://msdn.microsoft.com/library/553f0d4e-8b1d-4148-9321-8b41a1e8e1b9)  
  
  
