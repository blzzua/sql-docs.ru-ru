---
title: "sp_help_jobstep (Transact-SQL) | Документы Microsoft"
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
- sp_help_jobstep_TSQL
- sp_help_jobstep
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_jobstep
ms.assetid: 4a13b804-45f2-4f82-987f-42d9a57dd6db
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bb316ee70ad1cf1f98898fd08edbb7cfb9622f56
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="sphelpjobstep-transact-sql"></a>sp_help_jobstep (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает сведения об этапах задания, используемых службой агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для автоматизации выполнения.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_help_jobstep { [ @job_id = ] 'job_id' | [ @job_name = ] 'job_name' }  
     [ , [ @step_id = ] step_id ]   
     [ , [ @step_name = ] 'step_name' ]   
     [ , [ @suffix = ] suffix ]   
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@job_id =**] **'***job_id***'**  
 Идентификационный номер задачи, для которого возвращаются сведения о задании. *Аргумент job_id* — **uniqueidentifier**, значение по умолчанию NULL.  
  
 [ **@job_name =**] **'***job_name***'**  
 Имя задания. *job_name* — **sysname**, значение по умолчанию NULL.  
  
> [!NOTE]  
>  Либо *job_id* или *job_name* должен быть указан, но не оба аргумента одновременно.  
  
 [ **@step_id =**] *step_id*  
 Идентификатор этапа задания. Если не указан, включаются все этапы задания. *step_id* — **int**, значение по умолчанию NULL.  
  
 [ **@step_name =**] **'***step_name***'**  
 Имя шага задания. *step_name* — **sysname**, значение по умолчанию NULL.  
  
 [ **@suffix =**] *suffix*  
 Флаг, указывающий, является ли текстовое описание добавляется к **флаги** столбца в выходных данных. *суффикс*— **бит**, по умолчанию **0**. Если *суффикс* — **1**, то добавляется описание.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**step_id**|**int**|Уникальный идентификатор шага.|  
|**step_name**|**sysname**|Имя шага задания.|  
|**Подсистема**|**nvarchar(40)**|Подсистема, в которой выполняется команда этапа.|  
|**команда**|**nvarchar(max)**|Выполняемая на шаге команда.|  
|**flags**|**int**|Битовая маска значений, управляющая режимом шага.|  
|**cmdexec_success_code**|**int**|Для **CmdExec** шаг, это код завершения процесса успешной команды.|  
|**on_success_action**|**tinyint**|Операция, выполняемая в случае успешного завершении шага:<br /><br /> **1** = завершить задание с успехом.<br /><br /> **2** = выйти из задания с ошибкой.<br /><br /> **3** = перейти к следующему шагу.<br /><br /> **4** = перейти к шагу.|  
|**on_success_step_id**|**int**|Если **on_success_action** — 4, это значение указывает следующий этап для выполнения.|  
|**on_fail_action**|**tinyint**|Операция, совершаемая в случае сбоя при выполнении шага. Значения те же, как **on_success_action**.|  
|**on_fail_step_id**|**int**|Если **on_fail_action** равно 4, это значение указывает следующий этап для выполнения.|  
|**server**|**sysname**|Зарезервировано.|  
|**database_name**|**sysname**|Для шага [!INCLUDE[tsql](../../includes/tsql-md.md)] это база данных, в которой выполняется команда.|  
|**database_user_name**|**sysname**|Для шага [!INCLUDE[tsql](../../includes/tsql-md.md)] это контекст пользователя базы данных, в котором выполняется команда.|  
|**retry_attempts**|**int**|Максимальное количество повторных попыток выполнения команды (в случае сбоев).|  
|**retry_interval**|**int**|Интервал (в минутах) между повторными попытками.|  
|**os_run_priority**|**int**|Зарезервировано.|  
|**output_file_name**|**nvarchar(200)**|Файл, в команду, выполнение которой следует записывать вывод ([!INCLUDE[tsql](../../includes/tsql-md.md)], **CmdExec**, и **PowerShell** только для шагов).|  
|**last_run_outcome**|**int**|Результат последнего запуска этапа:<br /><br /> **0** = ошибка<br /><br /> **1** = выполнено успешно<br /><br /> **2** = Повтор<br /><br /> **3** = отменено<br /><br /> **5** = неизвестно|  
|**last_run_duration**|**int**|Продолжительность этапа в секундах при последнем запуске.|  
|**last_run_retries**|**int**|Число повторов команды при последнем запуске этапа.|  
|**last_run_date**|**int**|Дата начала последнего выполнения этапа.|  
|**last_run_time**|**int**|Время начала последнего выполнения этапа.|  
|**proxy_id**|**int**|Учетная запись-посредник для шага задания.|  
  
## <a name="remarks"></a>Remarks  
 **sp_help_jobstep** в **msdb** базы данных.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию эту хранимую процедуру могут выполнять только члены предопределенной роли сервера **sysadmin** . Другим пользователям должна быть предоставлена одна из следующих предопределенных ролей базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в базе данных **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Дополнительные сведения о разрешениях этих ролей см. в разделе [Предопределенные роли базы данных агента SQL Server](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79).  
  
 Члены **SQLAgentUserRole** могут только просматривать шагов заданий для заданий, которыми они владеют.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-return-information-for-all-steps-in-a-specific-job"></a>A. Возврат сведений обо всех шагах указанного задания  
 В следующем примере возвращаются все шаги задания с именем `Weekly Sales Data Backup`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_jobstep  
    @job_name = N'Weekly Sales Data Backup' ;  
GO  
```  
  
### <a name="b-return-information-about-a-specific-job-step"></a>Б. Возврат сведений об указанном шаге задания  
 В следующем примере возвращаются сведения о первом шаге задания с именем `Weekly Sales Data Backup`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_jobstep  
    @job_name = N'Weekly Sales Data Backup',  
    @step_id = 1 ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [sp_add_jobstep &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql.md)   
 [sp_delete_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobstep-transact-sql.md)   
 [sp_help_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-job-transact-sql.md)   
 [sp_update_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
