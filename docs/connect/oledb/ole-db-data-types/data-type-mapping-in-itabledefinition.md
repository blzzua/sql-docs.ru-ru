---
title: Сопоставление типов данных в интерфейсе ITableDefinition | Документы Microsoft
description: Сопоставление типов данных в интерфейсе ITableDefinition
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-data-types
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- mapping data types [OLE DB]
- OLE DB Driver for SQL Server, data types
- ITableDefinition interface
- DBCOLUMNDESC structure
- data types [OLE DB]
- CreateTable function
- OLE DB, data types
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e4cdcbbc5fdb0ac5efc6e8090213dd06475695b3
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2018
---
# <a name="data-type-mapping-in-itabledefinition"></a>Сопоставление типов данных в интерфейсе ITableDefinition
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  При создании таблицы с помощью **ITableDefinition::CreateTable** функции, можно указать драйвер OLE DB для SQL Server потребителя [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] типы данных в *pwszTypeName* членом Массив структуры DBCOLUMNDESC, который передается. Если потребитель указывает тип данных столбца по имени, тип данных OLE DB сопоставление, представленное *wType* структуры DBCOLUMNDESC, учитывается.  
  
 При указании новых типов данных столбцов с типами данных OLE DB с помощью структуры DBCOLUMNDESC *wType* член, драйвер OLE DB для SQL Server сопоставляет типы данных OLE DB, как показано ниже.  
  
|Тип данных OLE DB|SQL Server<br /><br /> тип данных|Дополнительные сведения|  
|----------------------|------------------------------|----------------------------|  
|DBTYPE_BOOL|**бит**||  
|DBTYPE_BYTES|**двоичный**, **varbinary**, **изображения,** или **varbinary(max)**|Драйвер OLE DB для SQL Server проверяет *ulColumnSize* структуры DBCOLUMNDESC. На основе значения и версию [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] экземпляра, драйвер OLE DB для SQL Server выполняется сопоставление типа **изображения**.<br /><br /> Если значение *ulColumnSize* меньше, чем максимальная длина **двоичных** тип данных столбца, то драйвер OLE DB для SQL Server проверяет структуры DBCOLUMNDESC *rgPropertySets*член. Если значение DBPROP_COL_FIXEDLENGTH равно VARIANT_FALSE, драйвер OLE DB для SQL Server сопоставляет тип для **двоичных**. Если значение свойства равно VARIANT_FALSE, драйвер OLE DB для SQL Server сопоставляет тип для **varbinary**. В любом случае структуры DBCOLUMNDESC *ulColumnSize* определяет ширину создаваемого столбца SQL Server.|  
|DBTYPE_CY|**money**||  
|DBTYPE_DBTIMESTAMP|**datetime**||  
|DBTYPE_GUID|**uniqueidentifier**||  
|DBTYPE_I2|**smallint**||  
|DBTYPE_I4|**int**||  
|DBTYPE_NUMERIC|**numeric**|Драйвер OLE DB для SQL Server проверяет элемент DBCOLUMDESC *bPrecision* и *bScale* членов, чтобы определить точность и масштаб для **числовое** столбца.|  
|DBTYPE_R4|**real**||  
|DBTYPE_R8|**float**||  
|DBTYPE_STR|**char**, **varchar**, **текста,** или **varchar(max)**|Драйвер OLE DB для SQL Server проверяет *ulColumnSize* структуры DBCOLUMNDESC. На основе значения и версию [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] экземпляра, драйвер OLE DB для SQL Server выполняется сопоставление типа **текст**.<br /><br /> Если значение *ulColumnSize* меньше, чем максимальная длина столбца типа данных Многобайтовый символ, то драйвер OLE DB для SQL Server проверяет структуры DBCOLUMNDESC *rgPropertySets* член. Если значение DBPROP_COL_FIXEDLENGTH равно VARIANT_FALSE, драйвер OLE DB для SQL Server сопоставляет тип для **char**. Если значение свойства равно VARIANT_FALSE, драйвер OLE DB для SQL Server сопоставляет тип для **varchar**. В любом случае структуры DBCOLUMNDESC *ulColumnSize* определяет ширину [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] создан столбец.|  
|DBTYPE_UDT|**UDT**|Следующие сведения используются в **DBCOLUMNDESC** структуры по **ITableDefinition::CreateTable** при необходимы столбцы определяемого пользователем ТИПА:<br /><br /> *pwSzTypeName* учитывается.<br /><br /> *rgPropertySets* должен включать **DBPROPSET_SQLSERVERCOLUMN** свойства, как это описано в разделе на **DBPROPSET_SQLSERVERCOLUMN**в [Using User-Defined типы ](../../oledb/features/using-user-defined-types.md).|  
|DBTYPE_UI1|**tinyint**||  
|DBTYPE_WSTR|**nchar**, **nvarchar**, **ntext,** или **nvarchar(max)**|Драйвер OLE DB для SQL Server проверяет *ulColumnSize* структуры DBCOLUMNDESC. Драйвер OLE DB для SQL Server на основе значения, сопоставляет тип для **ntext**.<br /><br /> Если значение *ulColumnSize* меньше, чем максимальная длина столбец типа данных символов Юникода, то драйвер OLE DB для SQL Server проверяет структуры DBCOLUMNDESC *rgPropertySets* член. Если значение DBPROP_COL_FIXEDLENGTH равно VARIANT_FALSE, драйвер OLE DB для SQL Server сопоставляет тип для **nchar**. Если значение свойства равно VARIANT_FALSE, драйвер OLE DB для SQL Server сопоставляет тип для **nvarchar**. В любом случае структуры DBCOLUMNDESC *ulColumnSize* определяет ширину [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] создан столбец.|  
|DBTYPE_XML|**XML**||  
  
> [!NOTE]  
>  При создании новой таблицы, драйвер OLE DB для SQL Server сопоставляет только OLE DB данных типа перечисления значения, указанные в предыдущей таблице. Попытка создать таблицу со столбцом любого другого типа данных OLE DB приводит к ошибке.  
  
## <a name="see-also"></a>См. также:  
 [Типы данных & #40; OLE DB & #41;](../../oledb/ole-db-data-types/data-types-ole-db.md)  
  
  
