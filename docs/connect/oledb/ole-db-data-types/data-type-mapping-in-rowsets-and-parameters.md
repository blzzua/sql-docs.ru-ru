---
title: Сопоставление типов данных в наборах строк и параметры | Документы Microsoft
description: Сопоставление типов данных в наборах строк и параметры
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
- DBTYPE_SQLVARIANT data type
- OLE DB Driver for SQL Server, data types
- rowsets [OLE DB], data type mapping
- data types [OLE DB]
- GetColumnInfo function
- parameters [OLE DB]
- SSPROP_ALLOWNATIVEVARIANT property
- GetParameterInfo function
- OLE DB, data types
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0470053bebdfd79275afeb629ae54a86a9b2f59e
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2018
---
# <a name="data-type-mapping-in-rowsets-and-parameters"></a>Сопоставление типов данных в наборах строк и параметрах
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  В наборах строк и, как значения параметров, драйвер OLE DB для SQL Server представляет [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] данных с помощью следующей OLE DB определенных типов данных, сообщаемых в функциях **IColumnsInfo::GetColumnInfo** и  **ICommandWithParameters::GetParameterInfo**.  
  
|Тип данных SQL Server|Тип данных OLE DB|  
|--------------------------|----------------------|  
|**bigint**|DBTYPE_I8|  
|**binary**|DBTYPE_BYTES|  
|**бит**|DBTYPE_BOOL|  
|**char**|DBTYPE_STR|  
|**datetime**|DBTYPE_DBTIMESTAMP|  
|**datetime2**|DBTYPE_DBTIME2|  
|**decimal**|DBTYPE_NUMERIC|  
|**float**|DBTYPE_R8|  
|**image**|DBTYPE_BYTES|  
|**int**|DBTYPE_I4|  
|**money**|DBTYPE_CY|  
|**nchar**|DBTYPE_WSTR|  
|**ntext**|DBTYPE_WSTR|  
|**numeric**|DBTYPE_NUMERIC|  
|**nvarchar**|DBTYPE_WSTR|  
|**real**|DBTYPE_R4|  
|**smalldatetime**|DBTYPE_DBTIMESTAMP|  
|**smallint**|DBTYPE_I2|  
|**smallmoney**|DBTYPE_CY|  
|**sql_variant**|DBTYPE_VARIANT, DBTYPE_SQLVARIANT|  
|**sysname**|DBTYPE_WSTR|  
|**text**|DBTYPE_STR|  
|**timestamp**|DBTYPE_BYTES|  
|**tinyint**|DBTYPE_UI1|  
|**UDT**|DBTYPE_UDT|  
|**uniqueidentifier**|DBTYPE_GUID|  
|**varbinary**|DBTYPE_BYTES|  
|**varchar**|DBTYPE_STR|  
|**XML**|DBTYPE_XML|  
  
 Драйвер OLE DB для SQL Server поддерживает данные, запрашиваемые потребителем преобразования, как показано на рисунке.  
  
 **Sql_variant** объектов может содержать данные любого [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] тип данных, кроме text, ntext, изображение, varchar(max), nvarchar(max), varbinary(max), xml, timestamp и Microsoft .NET Framework общеязыковая среда выполнения (CLR) определяемые пользователем типы. Экземпляр данных sql_variant не может также иметь sql_variant в качестве базового типа данных. Например, столбец может содержать **smallint** значения для некоторых строк **float** значения в других строках и **char**/**nchar**значения Далее.  
  
> [!NOTE]  
>  **Sql_variant** тип данных похож на тип данных Variant в Microsoft Visual Basic® и DBTYPE_VARIANT, DBTYPE_SQLVARIANT в OLEDB.  
  
 Когда **sql_variant** данные получены как DBTYPE_VARIANT, они размещаются в структуре VARIANT в буфере. Но подтипы в структуре VARIANT могут не соответствовать подтипам, определенным в **sql_variant** тип данных. **Sql_variant** данных затем должны быть выбраны как DBTYPE_SQLVARIANT в порядке все подтипы для сопоставления.  
  
## <a name="dbtypesqlvariant-data-type"></a>Тип данных DBTYPE_SQLVARIANT  
 Для поддержки **sql_variant** тип данных, драйвер OLE DB для SQL Server предоставляет тип поставщика данных, называемый DBTYPE_SQLVARIANT. Когда **sql_variant** данные доставляются в как DBTYPE_SQLVARIANT, он хранится в структуре SSVARIANT конкретного поставщика. Структура SSVARIANT содержит все подтипы, сопоставленные с подтипами **sql_variant** тип данных.  
  
 Свойство сеанса SSPROP_ALLOWNATIVEVARIANT должно быть равно true.  
  
## <a name="provider-specific-property-sspropallownativevariant"></a>Специфическое для поставщика свойство SSPROP_ALLOWNATIVEVARIANT  
 При выборке данных можно явно указать разновидность типа данных, которые должны быть возвращены для столбца или для параметра. **IColumnsInfo** также можно получить сведения о столбце и использовать их для привязки. Когда **IColumnsInfo** используется для получения сведения о столбце для привязки, если свойство сеанса SSPROP_ALLOWNATIVEVARIANT имеет значение FALSE (значение по умолчанию), возвращается DBTYPE_VARIANT **sql_variant**столбцов. Если свойство SSPROP_ALLOWNATIVEVARIANT имеет значение FALSE, DBTYPE_SQLVARIANT не поддерживается. Если свойство SSPROP_ALLOWNATIVEVARIANT имеет значение TRUE, возвращается тип столбца DBTYPE_SQLVARIANT. В этом случае в буфере сохраняется структура SSVARIANT. При выборке **sql_variant** данных как DBTYPE_SQLVARIANT свойство сеанса SSPROP_ALLOWNATIVEVARIANT должно быть присвоено значение TRUE.  
  
 Свойство SSPROP_ALLOWNATIVEVARIANT является частью специфического для поставщика набора свойств DBPROPSET_SQLSERVERSESSION и свойством сеанса.  
  
 DBTYPE_VARIANT применяется ко всем другим поставщикам OLE DB.  
  
## <a name="sspropallownativevariant"></a>Свойство SSPROP_ALLOWNATIVEVARIANT  
 Свойство SSPROP_ALLOWNATIVEVARIANT является свойством сеанса и частью набора свойств DBPROPSET_SQLSERVERSESSION.  
  
|||  
|-|-|  
|Свойство SSPROP_ALLOWNATIVEVARIANT|Тип: VT_BOOL<br /><br /> R Чтение и запись: чтение и запись<br /><br /> По умолчанию: значение VARIANT_FALSE<br /><br /> Описание: Определяет, является ли данные, полученные в качестве DBTYPE_VARIANT или DBTYPE_SQLVARIANT.<br /><br /> VARIANT_TRUE: Dbtype_sqlvariant в котором случае в буфере сохраняется структура SSVARIANT возвращается тип столбца.<br /><br /> VARIANT_FALSE: Тип столбца возвращается DBTYPE_VARIANT и буфер будет иметь структура VARIANT.|  
  
## <a name="see-also"></a>См. также  
 [Типы данных & #40; OLE DB & #41;](../../oledb/ole-db-data-types/data-types-ole-db.md)  
  
  
