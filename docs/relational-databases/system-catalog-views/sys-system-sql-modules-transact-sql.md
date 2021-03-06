---
title: "sys.system_sql_modules (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- system_sql_modules_TSQL
- sys.system_sql_modules
- sys.system_sql_modules_TSQL
- system_sql_modules
dev_langs:
- TSQL
helpviewer_keywords:
- sys.system_sql_modules catalog view
ms.assetid: ad3548bc-4780-4821-b962-b421d52daed9
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 66917b2a30649119ee7921f4343d79765efbb8b1
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="syssystemsqlmodules-transact-sql"></a>sys.system_sql_modules (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает одну запись на каждый системный объект, который содержит языковый модуль SQL. Системные объекты типа FN, IF, P, PC, TF, V обладают связанным модулем SQL. Для определения содержащего его объекта, можно соединить это представление для [sys.system_objects](../../relational-databases/system-catalog-views/sys-system-objects-transact-sql.md).  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|Идентификационный номер контейнера уникален в пределах базы данных.|  
|**Определение**|**nvarchar(max)**|Текст на языке SQL, определяющий этот модуль.|  
|**uses_ansi_nulls**|**bit**|1 = модуль был создан с параметром SET ANSI_NULLS ON.<br /><br /> Всегда возвращает значение 1.|  
|**uses_quoted_identifier**|**bit**|1 = модуль был создан с параметром SET QUOTED_IDENTIFIER ON.<br /><br /> Всегда возвращает значение 1.|  
|**is_schema_bound**|**bit**|0 = модуль был создан с параметром SCHEMABINDING.<br /><br /> Всегда возвращает значение 0.|  
|**uses_database_collation**|**bit**|0 = модуль не зависит от параметров сортировки базы данных по умолчанию.<br /><br /> Всегда возвращает значение 0.|  
|**is_recompiled**|**bit**|0 = процедура не была создана с параметром WITH RECOMPILE.<br /><br /> Всегда возвращает значение 0.|  
|**null_on_null_input**|**bit**|0 = модуль не был создан, чтобы обеспечить выходные значения NULL для любых входных значений NULL.<br /><br /> Всегда возвращает значение 0.|  
|**execute_as_principal_id**|**int**|Всегда возвращает NULL.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также:  
 [sys.sql_modules (Transact-SQL)](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [sys.all_sql_modules &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-all-sql-modules-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Представления каталога объектов &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)  
  
  
