---
title: "sys.assembly_types (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- assembly_types
- sys.assembly_types
- sys.assembly_types_TSQL
- assembly_types_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.assembly_types catalog view
ms.assetid: 35f0384f-7a6d-41b1-9461-f1406d68f317
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f4411b518085338e18b01697fd445ca1d18e7ce1
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="sysassemblytypes-transact-sql"></a>sys.assembly_types (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Содержит строку для каждого определяемого пользователем типа, определенного сборкой CLR. Следующие **sys.assembly_types** отображаются в списке наследуемых столбцов (в разделе [sys.types &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)) после **rule_object_id**.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**assembly_id**|**int**|Идентификатор сборки, из которой был создан данный тип.|  
|**assembly_class**|**sysname**|Имя класса в сборке, которая определяет данный тип.|  
|**is_binary_ordered**|**бит**|Сортировка байтов данного типа эквивалентна сортировке с применением к типу операторов сравнения.|  
|**is_fixed_length**|**бит**|Длина типа всегда такая же, как и max_length.|  
|**prog_id**|**nvarchar(40)**|Идентификатор ProgID типа, передаваемый в COM.|  
|**assembly_qualified_name**|**nvarchar(4000)**|Имя типа с указанием сборки. Имя указано в формате, подходящем для передачи методу Type.GetType().|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Скалярные типы представлений каталога &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/scalar-types-catalog-views-transact-sql.md)  
  
  
