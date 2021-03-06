---
title: "sys.database_role_members (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 01/31/2017
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
- sys.database_role_members_TSQL
- sys.database_role_members
- database_role_members_TSQL
- database_role_members
dev_langs:
- TSQL
helpviewer_keywords:
- sys.database_role_members catalog view
ms.assetid: ed1b019d-ca48-4db3-85df-cf6d2db591cf
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: abe12465ae80a9373475a0158cdacc663b8f00fa
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="sysdatabaserolemembers-transact-sql"></a>sys.database_role_members (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает одну строку для каждого члена каждой роли базы данных.  Пользователи базы данных, роли приложений и других ролей базы данных может быть членами роли базы данных. Чтобы добавить членов роли, используйте [ALTER ROLE](../../t-sql/statements/alter-role-transact-sql.md) инструкции с `ADD MEMBER` параметр. Соединения с [sys.database_principals](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md) для возвращения имен `principal_id` значения.
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**role_principal_id**|**int**|Идентификатор участника базы данных роли.|  
|**member_principal_id**|**int**|Идентификатор участника базы данных члена.|  
  
## <a name="permissions"></a>Permissions  
 Любой пользователь может просматривать данные о своем членстве в роли. Для просмотра других ролей членства требует членства в `db_securityadmin` предопределенной роли базы данных или `VIEW DEFINITION` в базе данных.  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="example"></a>Пример  
 Следующий запрос возвращает список членов ролей базы данных.  
  
```  
SELECT DP1.name AS DatabaseRoleName,   
   isnull (DP2.name, 'No members') AS DatabaseUserName   
 FROM sys.database_role_members AS DRM  
 RIGHT OUTER JOIN sys.database_principals AS DP1  
   ON DRM.role_principal_id = DP1.principal_id  
 LEFT OUTER JOIN sys.database_principals AS DP2  
   ON DRM.member_principal_id = DP2.principal_id  
WHERE DP1.type = 'R'
ORDER BY DP1.name;  
```  
  
## <a name="see-also"></a>См. также:  
 [Представления каталога безопасности (Transact-SQL)](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Участники (компонент Database Engine)](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
[Изменение РОЛИ (Transact-SQLL)](../../t-sql/statements/alter-role-transact-sql.md)      
[sys.server_role_members (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-role-members-transact-sql.md)   
  


