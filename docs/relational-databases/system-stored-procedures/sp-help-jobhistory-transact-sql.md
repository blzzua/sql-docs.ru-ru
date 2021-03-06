---
title: "sp_help_jobhistory (Transact-SQL) | Документы Microsoft"
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
- sp_help_jobhistory_TSQL
- sp_help_jobhistory
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_jobhistory
ms.assetid: a944d44e-411b-4735-8ce4-73888d4262d7
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: de1836ee52354e96341386db5dfd33297f2d9be6
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="sphelpjobhistory-transact-sql"></a>sp_help_jobhistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Предоставляет сведения о заданиях серверов в многосерверном административном домене.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_help_jobhistory [ [ @job_id = ] job_id ]   
     [ , [ @job_name = ] 'job_name' ]   
     [ , [ @step_id = ] step_id ]   
     [ , [ @sql_message_id = ] sql_message_id ]   
     [ , [ @sql_severity = ] sql_severity ]   
     [ , [ @start_run_date = ] start_run_date ]   
     [ , [ @end_run_date = ] end_run_date ]   
     [ , [ @start_run_time = ] start_run_time ]   
     [ , [ @end_run_time = ] end_run_time ]   
     [ , [ @minimum_run_duration = ] minimum_run_duration ]   
     [ , [ @run_status = ] run_status ]   
     [ , [ @minimum_retries = ] minimum_retries ]   
     [ , [ @oldest_first = ] oldest_first ]   
     [ , [ @server = ] 'server' ]   
     [ , [ @mode = ] 'mode' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@job_id=** ] *job_id*  
 Идентификационный номер задания. *Аргумент job_id* — **uniqueidentifier**, значение по умолчанию NULL.  
  
 [ **@job_name=** ] **'***job_name***'**  
 Имя задания. *job_name* — **sysname**, значение по умолчанию NULL.  
  
 [ **@step_id=** ] *step_id*  
 Идентификационный номер этапа. *step_id* — **int**, значение по умолчанию NULL.  
  
 [ **@sql_message_id=** ] *sql_message_id*  
 Идентификационный номер сообщения об ошибке, возвращаемый Microsoft SQL Server при запуске задания. *sql_message_id* — **int**, значение по умолчанию NULL.  
  
 [ **@sql_severity=** ] *sql_severity*  
 Уровень серьезности сообщения об ошибке, возвращаемого SQL Server при запуске задания. *sql_severity* — **int**, значение по умолчанию NULL.  
  
 [ **@start_run_date=** ] *start_run_date*  
 Дата запуска задания. *start_run_date*— **int**, значение по умолчанию NULL. *start_run_date* должен быть задан в формате ГГГГММДД, где гггг — четырехзначное число года, мм — двухзначное число месяца, а дд — двухзначное число дня.  
  
 [ **@end_run_date=** ] *end_run_date*  
 Дата завершения задания. *end_run_date* — **int**, значение по умолчанию NULL. *end_run_date*должен быть задан в формате ГГГГММДД, где гггг — четырехзначное число года, мм — двухзначное число месяца, а дд — двухзначное число дня.  
  
 [ **@start_run_time=** ] *start_run_time*  
 Время запуска задания. *start_run_time* — **int**, значение по умолчанию NULL. *start_run_time*должен быть задан в формате ЧЧММСС, где ЧЧ — двухзначное число часов, мм — двухзначное число минут, а СС — двухзначное число дня.  
  
 [ **@end_run_time=** ] *end_run_time*  
 Время завершения выполнения задания. *end_run_time* — **int**, значение по умолчанию NULL. *end_run_time*должен быть задан в формате ЧЧММСС, где ЧЧ — двухзначное число часов, мм — двухзначное число минут, а СС — двухзначное число дня.  
  
 [ **@minimum_run_duration=** ] *minimum_run_duration*  
 Минимальное время для выполнения задания. *minimum_run_duration* — **int**, значение по умолчанию NULL. *minimum_run_duration*должен быть задан в формате ЧЧММСС, где ЧЧ — двухзначное число часов, мм — двухзначное число минут, а СС — двухзначное число дня.  
  
 [ **@run_status=** ] *run_status*  
 Состояние выполнения задания. *run_status* — **int**, значение по умолчанию NULL и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**0**|Ошибка|  
|**1**|Выполнено|  
|**2**|Повторить (только для этапа)|  
|**3**|Отменено|  
|**4**|Сообщение о проценте выполнения|  
|**5**|Неизвестно|  
  
 [ **@minimum_retries=** ] *minimum_retries*  
 Минимальное число повторных попыток выполнить задание. *minimum_retries* — **int**, значение по умолчанию NULL.  
  
 [ **@oldest_first=** ] *oldest_first*  
 Показывать ли результаты, начиная со старейшего задания. *oldest_first* — **int**, значение по умолчанию **0**, которое представляет новых заданий. **1** первыми старейшего задания.  
  
 [ **@server=** ] **'***server***'**  
 Имя сервера, на котором было выполнено задание. *сервер* — **nvarchar(30)**, значение по умолчанию NULL.  
  
 [ **@mode=** ] **'***mode***'**  
 Выводит ли SQL Server все столбцы в результирующем наборе (**полного**) или только краткую сводку столбцов. *режим* — **varchar(7)**, значение по умолчанию **Сводка**.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Реальный набор столбцов зависит от значения *режим*. Самый полный список столбцов показан ниже и возвращается, когда *режим* установлен в FULL.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**instance_id**|**int**|Идентификационный номер записи журнала.|  
|**job_id**|**uniqueidentifier**|Идентификатор задания.|  
|**job_name**|**sysname**|Имя задания.|  
|**step_id**|**int**|Идентификационный номер этапа (будет **0** для журнала заданий).|  
|**step_name**|**sysname**|Имя этапа (NULL для журнала заданий).|  
|**sql_message_id**|**int**|Для шага [!INCLUDE[tsql](../../includes/tsql-md.md)] — самый последний номер ошибки [!INCLUDE[tsql](../../includes/tsql-md.md)], обнаруженный при выполнении команды.|  
|**sql_severity**|**int**|Для шага [!INCLUDE[tsql](../../includes/tsql-md.md)] — самая высокая степень серьезности ошибки [!INCLUDE[tsql](../../includes/tsql-md.md)], обнаруженная при выполнении команды.|  
|**message**|**nvarchar(1024)**|Запись в журнале о задании или этапе.|  
|**run_status**|**int**|Результат задания или этапа.|  
|**run_date**|**int**|Дата начала выполнения задания или этапа.|  
|**run_time**|**int**|Дата начала выполнения задания или этапа.|  
|**run_duration**|**int**|Время, прошедшее с момента запуска задания или этапа в формате «ЧЧММСС».|  
|**operator_emailed**|**nvarchar(20)**|Оператор, которому было отправлено электронное письмо относительно этого задания (NULL для журнала этапов). |  
|**operator_netsent**|**nvarchar(20)**|Оператор, которому было отправлено сетевое сообщение относительно этого задания (NULL для журнала этапов).|  
|**operator_paged**|**nvarchar(20)**|Оператор, которому было отправлено сообщение на пейджер относительно этого задания (NULL для журнала этапов).|  
|**retries_attempted**|**int**|Количество повторных попыток запуска этапа (всегда 0 для журнала заданий).|  
|**server**|**nvarchar(30)**|Сервер, на котором выполняется задание или этап. Всегда (**локального**).|  
  
## <a name="remarks"></a>Remarks  
 **sp_help_jobhistory** возвращает отчет по журналу для указанных запланированных заданий. Если не указаны параметры, отчет содержит журнал всех заданий в расписании.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию эту хранимую процедуру могут выполнять только члены предопределенной роли сервера **sysadmin** . Другим пользователям должна быть предоставлена одна из следующих предопределенных ролей базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в базе данных **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Дополнительные сведения о разрешениях этих ролей см. в разделе [Предопределенные роли базы данных агента SQL Server](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79).  
  
 Члены **SQLAgentUserRole** роли базы данных могут только просматривать данные журнала для заданий, которыми они владеют.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-listing-all-job-information-for-a-job"></a>A. Вывод всех сведений о задании  
 В следующем примере отображаются все сведения о задании `NightlyBackups`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_jobhistory   
    @job_name = N'NightlyBackups' ;  
GO  
```  
  
### <a name="b-listing-information-for-jobs-that-match-certain-conditions"></a>Б. Вывод сведений о заданиях, которые соответствуют определенным условиям  
 Следующий пример иллюстрирует вывод всех сведений о шагах заданий, завершившихся неудачно с кодом ошибки `50100` (пользовательская ошибка) и уровнем серьезности `20`.  
  
```  
USE msdb  
GO  
  
EXEC dbo.sp_help_jobhistory  
    @sql_message_id = 50100,  
    @sql_severity = 20,  
    @run_status = 0,  
    @mode = N'FULL' ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [sp_purge_jobhistory (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-purge-jobhistory-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
