---
title: "sp_changeqreader_agent (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_changeqreader_agent_TSQL
- sp_changeqreader_agent
helpviewer_keywords:
- sp_changeqreader_agent
ms.assetid: d3fe79c5-31ef-4565-bf38-b476b5fb16f7
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0ce63f317910d84aae14f2457f383bce7ba291c1
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="spchangeqreaderagent-transact-sql"></a>sp_changeqreader_agent (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Изменяет свойства безопасности агента чтения очереди. Эта хранимая процедура выполняется на распространителе в базе данных распространителя или на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_changeqreader_agent [ [ @job_login = ] 'job_login' ]  
    [ , [ @job_password = ] 'job_password' ]  
    [ , [ @frompublisher = ] frompublisher   
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@job_login** =] **"***job_login***"**  
 Имя входа для учетной записи [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, под которой запускается агент. *job_login* — **nvarchar(257)**, значение по умолчанию NULL.  
  
 [  **@job_password** =] **"***job_password***"**  
 Пароль для учетной записи Windows, под которой запускается агент. *job_password* — **sysname**, значение по умолчанию NULL.  
  
 [  **@frompublisher=** ] *frompublisher*  
 Процедура, выполняемая на стороне издателя. *frompublisher* имеет тип bit и значение по умолчанию **0**. Значение **1** означает, что процедура выполняется на издателе в базе данных публикации.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_changeqreader_agent** используется в репликации транзакций.  
  
 **sp_changeqreader_agent** используется для изменения учетной записи Windows, под которой запускается агент чтения очереди. Можно изменить пароль существующего имени входа в систему Windows или ввести новое имя пользователя Windows и пароль.  
  
 После изменения имени входа и пароля агента необходимо остановить и повторно запустить агент, чтобы изменения вступили в силу.  
  
## <a name="permissions"></a>Permissions  
 Только члены **sysadmin** предопределенной роли сервера могут выполнять **sp_changeqreader_agent**.  
  
## <a name="see-also"></a>См. также:  
 [Просмотр и изменение параметров безопасности репликации](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)   
 [sp_addqreader_agent (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addqreader-agent-transact-sql.md)  
  
  
