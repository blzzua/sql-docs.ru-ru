---
title: "sys.partition_functions (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
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
- sys.partition_functions_TSQL
- partition_functions
- sys.partition_functions
- partition_functions_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.partition_functions catalog view
ms.assetid: 96515727-728b-4bea-804a-36ce915b8b75
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a440995a63e75705c0a7b5d3c56e1e649c6defbe
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="syspartitionfunctions-transact-sql"></a>sys.partition_functions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-pdw-md.md)]

  Содержит по одной строке для каждой функции секционирования в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Имя функции секционирования. Уникален в пределах базы данных.|  
|**function_id**|**int**|Идентификатор функции секционирования. Уникален в пределах базы данных.|  
|**type**|**char(2)**|Тип функции.<br /><br /> R = диапазон|  
|**type_desc**|**nvarchar(60)**|Тип функции.<br /><br /> RANGE|  
|**ветвления**|**int**|Число секций, создаваемых функцией.|  
|**boundary_value_on_right**|**bit**|Для секционирования по диапазонам.<br /><br /> 1 = граничное значение включается в правый (RIGHT) диапазон границы.<br /><br /> 0 = LEFT (левый).|  
|**is_system**||**Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> 1 = объект используется для фрагментов полнотекстового индекса.<br /><br /> 0 = объект не используется для фрагментов полнотекстового индекса.|  
|**create_date**|**datetime**|Дата создания функции.|  
|**modify_date**|**datetime**|Дата последнего изменения функции с помощью инструкции ALTER.|  
  
## <a name="permissions"></a>Permissions  
 Необходимо быть членом роли **public** . Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также:  
 [Представления каталога функции секционирования &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/partition-function-catalog-views-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sys.partition_range_values &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-partition-range-values-transact-sql.md)   
 [sys.partition_parameters &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-partition-parameters-transact-sql.md)  
  
  
