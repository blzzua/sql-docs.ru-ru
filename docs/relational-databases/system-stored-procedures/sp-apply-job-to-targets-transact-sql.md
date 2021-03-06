---
title: "sp_apply_job_to_targets (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_apply_job_to_targets
- sp_apply_job_to_targets_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_apply_job_to_targets
ms.assetid: 4a3e9173-7e3c-4100-a9ac-2f5d2c60a8b0
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 341a14b2ae6aa3d551ab90d4ff2f931d617aa3f2
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="spapplyjobtotargets-transact-sql"></a>sp_apply_job_to_targets (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Применяет задание к одному или нескольким целевым серверам или к целевым серверам, принадлежащим к одной или нескольким группам целевых серверов.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_apply_job_to_targets { [ @job_id = ] job_id | [ @job_name = ] 'job_name' }  
     [ , [ @target_server_groups = ] 'target_server_groups' ]   
     [ , [ @target_servers = ] 'target_servers' ]   
     [ , [ @operation = ] 'operation' ]   
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@job_id =**] *job_id*  
 Идентификационный номер задания, которое следует применить к указанным целевым серверам и группам целевых серверов. *Аргумент job_id* — **uniqueidentifier**, значение по умолчанию NULL.  
  
 [ **@job_name =**] **'***job_name***'**  
 Имя указания, которое следует применить к связанным целевым серверам и группам целевых серверов. *job_name* — **sysname**, значение по умолчанию NULL.  
  
> [!NOTE]  
>  Либо *job_id* или *job_name* должен быть указан, но не оба аргумента одновременно.  
  
 [ **@target_server_groups =**]  **'***target_server_groups***'**  
 Список групп целевых серверов с разделителями-запятыми, к которым следует применить указанное задание. *target_server_groups* — **nvarchar(2048)**, значение по умолчанию NULL.  
  
 [ **@target_servers=** ] **'***target_servers***'**  
 Список целевых серверов с разделителями-запятыми, к которым следует применить указанное задание. *target_servers*— **nvarchar(2048)**, значение по умолчанию NULL.  
  
 [  **@operation=** ] **"***операции***"**  
 Определяет, должно ли указанное задание быть применено или удалено с указанных целевых серверов или групп целевых серверов. *Операция*— **varchar(7)**, значение по умолчанию APPLY. Допустимы следующие операции: **применить** и **удалить**.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Remarks  
 **sp_apply_job_to_targets** предоставляет простой способ применения (или удаления) задания к нескольким целевым серверам и является альтернативой вызову **sp_add_jobserver** (или **sp_delete_jobserver** ) один раз для каждого целевого сервера, который требуется.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера могут выполнить эту процедуру.  
  
## <a name="examples"></a>Примеры  
 В следующем примере ко всем целевым серверам в группе `Backup Customer Information` применяется ранее созданное задание `Servers Maintaining Customer Information`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_apply_job_to_targets  
    @job_name = N'Backup Customer Information',  
    @target_server_groups = N'Servers Maintaining Customer Information',   
    @operation = N'APPLY' ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [sp_add_jobserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql.md)   
 [sp_delete_jobserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobserver-transact-sql.md)   
 [sp_remove_job_from_targets &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-remove-job-from-targets-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
