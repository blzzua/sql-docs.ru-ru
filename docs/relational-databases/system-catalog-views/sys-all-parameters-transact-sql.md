---
title: "sys.all_parameters (Transact-SQL) | Документы Microsoft"
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
- all_parameters_TSQL
- sys.all_parameters
- all_parameters
- sys.all_parameters_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.all_parameters catalog view
ms.assetid: eecbb68e-9b4c-4243-94e2-8096a9cc7892
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a0513ae73ab3feb03bf2da24fcd2e0b458f4e9af
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="sysallparameters-transact-sql"></a>sys.all_parameters (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Содержит все параметры, относящиеся к пользовательским или системным объектам.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|Идентификатор объекта, которому принадлежит этот параметр.|  
|**name**|**sysname**|Имя параметра. Уникален в пределах объекта. Если объект является скалярной функцией, именем параметра будет пустая строка в строке, представляющей возвращаемое значение.|  
|**parameter_id**|**int**|Идентификатор параметра. Уникален в пределах объекта. Если объект является скалярной функцией, **parameter_id** = 0 представляет возвращаемое значение.|  
|**system_type_id**|**tinyint**|Идентификатор системного типа параметра.|  
|**user_type_id**|**int**|Определенный пользователем идентификатор типа параметра.<br /><br /> Чтобы вернуть имя типа, присоединение к [sys.types](../../relational-databases/system-catalog-views/sys-types-transact-sql.md) представления на этот столбец каталога.|  
|**max_length**|**smallint**|Максимальная длина параметра в байтах.<br /><br /> -1 = тип данных столбца — **varchar(max)**, **nvarchar(max)**, **varbinary(max)**, или **xml**.|  
|**точность**|**tinyint**|Точность параметра, если он является числовым; иначе — 0.|  
|**Масштаб**|**tinyint**|Масштаб числового параметра, если он является числовым; иначе — 0.|  
|**is_output**|**bit**|1 = выходной параметр (или возвращаемый); иначе — 0.|  
|**is_cursor_ref**|**bit**|1 = параметр является ссылкой на курсор.|  
|**has_default_value**|**bit**|1 = параметр имеет значение по умолчанию.<br /><br /> В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживаются значения по умолчанию для объектов среды CLR в данном представлении каталога, поэтому в данном столбце всегда будет содержаться значение 0 для объектов языка [!INCLUDE[tsql](../../includes/tsql-md.md)]. Для просмотра значения по умолчанию параметра в [!INCLUDE[tsql](../../includes/tsql-md.md)] объекта, запрос **определения** столбец [sys.sql_modules](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md) представления каталога, или используйте [OBJECT_DEFINITION](../../t-sql/functions/object-definition-transact-sql.md)системная функция.|  
|**is_xml_document**|**bit**|1 = содержимое является готовым XML-документом.<br /><br /> 0 = содержимое является фрагментом документа, или тип данных столбца не **xml**.|  
|**значение по умолчанию**|**sql_variant**|Если **has_default_value** равно 1, значение этого столбца является значением по умолчанию для параметра; в противном случае — NULL.|  
|**xml_collection_id**|**int**|Идентификатор коллекции XML-схем, используемый для проверки параметра.<br /><br /> Ненулевое значение, если тип данных параметра **xml** и XML типизирован.<br /><br /> 0 = нет коллекций XML-схем, или тип параметра не XML.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также:  
 [Представления каталога объектов &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Запросив системный каталог SQL Server часто задаваемые вопросы](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [sys.parameters (Transact-SQL)](../../relational-databases/system-catalog-views/sys-parameters-transact-sql.md)   
 [sys.system_parameters &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-system-parameters-transact-sql.md)  
  
  
