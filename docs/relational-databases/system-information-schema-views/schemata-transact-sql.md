---
title: "СХЕМЫ (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 09/08/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: system-information-schema-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SCHEMATA_TSQL
- SCHEMATA
dev_langs:
- TSQL
helpviewer_keywords:
- INFORMATION_SCHEMA.SCHEMATA view
- SCHEMATA view
ms.assetid: 69617642-0f54-4b25-b62f-5f39c8909601
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ac71e5f401f0eb411f7356d8bc4c15fa0a57c901
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="schemata-transact-sql"></a>SCHEMATA (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает по одной строке на каждую схему текущей базы данных. Чтобы получить сведения из этих представлений, укажите полное имя **INFORMATION_SCHEMA.** *view_name*. Для получения сведений обо всех базах данных в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], запрос [sys.databases &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) представления каталога.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**CATALOG_NAME**|**sysname**|Имя текущей базы данных.|  
|**SCHEMA_NAME**|**nvarchar (**128**)**|Имя схемы.|  
|**SCHEMA_OWNER**|**nvarchar (**128**)**|Имя владельца схемы.<br /><br /> **\*\*Важные \* \***  не используйте представления INFORMATION_SCHEMA, чтобы определить схему объекта. Единственный надежный способ найти схему объекта — выполнить запрос к представлению каталога sys.objects.|  
|**DEFAULT_CHARACTER_SET_CATALOG**|**varchar (**6**)**|Всегда возвращает значение NULL.|  
|**DEFAULT_CHARACTER_SET_SCHEMA**|**varchar (**3**)**|Всегда возвращает значение NULL.|  
|**DEFAULT_CHARACTER_SET_NAME**|**sysname**|Имя установленной по умолчанию кодировки.|  

**Пример**  
В следующем примере, возвращается информация о схемах в базе данных master:  
```sql  
SELECT * FROM master.INFORMATION_SCHEMA.SCHEMATA;
```  

## <a name="see-also"></a>См. также:  
 [Системные представления &#40; Transact-SQL &#41;](http://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [Представления информационной схемы &#40; Transact-SQL &#41;](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [sys.databases (Transact-SQL)](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [sys.schemas &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/schemas-catalog-views-sys-schemas.md)   
 [sys.syscharsets &#40; Transact-SQL &#41;](../../relational-databases/system-compatibility-views/sys-syscharsets-transact-sql.md)  
  
  
