---
title: "sys.foreign_key_columns (Transact-SQL) | Документы Microsoft"
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
- sys.foreign_key_columns
- foreign_key_columns
- sys.foreign_key_columns_TSQL
- foreign_key_columns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.foreign_key_columns catalog view
ms.assetid: 7247f065-5441-4bcf-9f25-c84a03290dc6
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e7c7be375e2ec58549604571bace68e7c0277e66
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="sysforeignkeycolumns-transact-sql"></a>sys.foreign_key_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Содержит строку для каждого столбца или набора столбцов, представляющих внешний ключ.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**constraint_object_id**|**int**|Идентификатор ограничения FOREIGN KEY.|  
|**constraint_column_id**|**int**|Идентификатор столбца или набора столбцов, представляющих FOREIGN KEY (*1.. n* где n = число столбцов).|  
|**parent_object_id**|**int**|Идентификатор родителя ограничения, ссылающегося на объект.|  
|**parent_column_id**|**int**|Идентификатор родительского столбца, являющегося ссылающимся столбцом.|  
|**referenced_object_id**|**int**|Идентификатор объекта ссылки с потенциальным ключом.|  
|**referenced_column_id**|**int**|Идентификатор столбца ссылки (потенциальный ключевой столбец).|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также:  
 [Представления каталога объектов &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Часто задаваемые вопросы о запросах к системному каталогу SQL Server](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
