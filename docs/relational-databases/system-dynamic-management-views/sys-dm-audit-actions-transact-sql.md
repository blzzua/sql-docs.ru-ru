---
title: "sys.dm_audit_actions (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_audit_actions_TSQL
- sys.dm_audit_actions
- dm_audit_actions_TSQL
- dm_audit_actions
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_audit_actions dynamic management view
ms.assetid: b987c2b9-998a-4a5f-a82d-280dc6963cbe
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4f5422f3230aa5d65df1a946ccf532e8108728e3
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmauditactions-transact-sql"></a>sys.dm_audit_actions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает строку для каждого действия аудита, которое может быть зарегистрировано в журнале аудита, и каждой группы действий аудита, которая может быть настроена в составе аудита [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Дополнительные сведения о [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] аудита, в разделе [подсистемы аудита SQL Server &#40; компонент Database Engine &#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md).  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**action_id**|**varchar(4)**|Идентификатор действия аудита. Они связаны с **action_id** значение, записанное в каждую запись аудита. Допускает значение NULL. NULL для групп аудита.|  
|**action_in_log**|**бит**|Определяет возможность записи действия в журнал аудита. Имеет следующие значения:<br /><br /> 1 = да<br /><br /> 0 = нет|  
|**name**|**sysname**|Имя действия аудита или группы действий. Не допускает значение NULL.|  
|**class_desc**|**nvarchar(120)**|Имя класса объекта, для которого применяется действие аудита. Может быть любым объектом области сервера, базы данных или схемы, но не включает объекты схемы. Не допускает значение NULL.|  
|**parent_class_desc**|**nvarchar(120)**|Имя родительского класса для объекта, описываемого class_desc. Значение NULL, если class_desc — Server.|  
|**covering_parent_action_name**|**nvarchar(120)**|Имя действия аудита или группа аудита, которая содержит действие аудита, описанное в этой строке. Используется, чтобы создать иерархию действий и охватывающие действия. Допускает значение NULL.|  
|**configuration_level**|**nvarchar(10)**|Указывает, что действие или группа действий, указанная в этой строке, настраивается на уровне группы или действия. Значение NULL, если действие нельзя настраивать.|  
|**containing_group_name**|**nvarchar(120)**|Имя группы аудита, которая содержит указанное действие. Значение NULL, если значением имени является группа.|  
  
## <a name="permissions"></a>Разрешения  
 Участники должны иметь **ВЫБЕРИТЕ** разрешение. По умолчанию это разрешение предоставлено роли Public.  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]. Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [Создание АУДИТА сервера &#40; Transact-SQL &#41;](../../t-sql/statements/create-server-audit-transact-sql.md)   
 [ALTER SERVER AUDIT &#40; Transact-SQL &#41;](../../t-sql/statements/alter-server-audit-transact-sql.md)   
 [DROP SERVER AUDIT &#40; Transact-SQL &#41;](../../t-sql/statements/drop-server-audit-transact-sql.md)   
 [Создание СПЕЦИФИКАЦИИ АУДИТА сервера &#40; Transact-SQL &#41;](../../t-sql/statements/create-server-audit-specification-transact-sql.md)   
 [ALTER SERVER AUDIT SPECIFICATION &#40; Transact-SQL &#41;](../../t-sql/statements/alter-server-audit-specification-transact-sql.md)   
 [DROP SERVER AUDIT SPECIFICATION &#40; Transact-SQL &#41;](../../t-sql/statements/drop-server-audit-specification-transact-sql.md)   
 [СОЗДАТЬ СПЕЦИФИКАЦИЮ АУДИТА базы данных &#40; Transact-SQL &#41;](../../t-sql/statements/create-database-audit-specification-transact-sql.md)   
 [ALTER DATABASE AUDIT SPECIFICATION &#40; Transact-SQL &#41;](../../t-sql/statements/alter-database-audit-specification-transact-sql.md)   
 [УДАЛИТЬ СПЕЦИФИКАЦИЮ АУДИТА базы данных &#40; Transact-SQL &#41;](../../t-sql/statements/drop-database-audit-specification-transact-sql.md)   
 [ALTER AUTHORIZATION &#40; Transact-SQL &#41;](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [sys.fn_get_audit_file &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-get-audit-file-transact-sql.md)   
 [sys.server_audits &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-server-audits-transact-sql.md)   
 [sys.server_file_audits &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-file-audits-transact-sql.md)   
 [sys.server_audit_specifications &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-server-audit-specifications-transact-sql.md)   
 [sys.server_audit_specification_details &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-server-audit-specification-details-transact-sql.md)   
 [sys.database_audit_specifications &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-database-audit-specifications-transact-sql.md)   
 [sys.database_audit_specification_details &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-audit-specification-details-transact-sql.md)   
 [sys.dm_server_audit_status &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-server-audit-status-transact-sql.md)   
 [sys.dm_audit_class_type_map &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-audit-class-type-map-transact-sql.md)   
 [Создание аудита сервера и спецификации аудита сервера](../../relational-databases/security/auditing/create-a-server-audit-and-server-audit-specification.md)  
  
  
