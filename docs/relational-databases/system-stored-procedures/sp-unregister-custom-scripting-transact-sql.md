---
title: "sp_unregister_custom_scripting (Transact-SQL) | Документы Microsoft"
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
- sp_unregister_custom_scripting_TSQL
- sp_unregister_custom_scripting
helpviewer_keywords:
- sp_unregister_custom_scripting
ms.assetid: b6e9e0d2-9144-434d-88af-4874f2582399
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: fce6b2d16e732b76519cb0fbf66a16ca5db6928f
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="spunregistercustomscripting-transact-sql"></a>sp_unregister_custom_scripting (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Эта хранимая процедура удаляет пользовательских пользовательская хранимая процедура или [!INCLUDE[tsql](../../includes/tsql-md.md)] файла сценария, который был зарегистрирован с помощью [sp_register_custom_scripting](../../relational-databases/system-stored-procedures/sp-register-custom-scripting-transact-sql.md). Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_unregister_custom_scripting [ @type  = ] 'type'  
    [ , [ @publication = ] 'publication' ]  
    [ , [ @article = ] 'article' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@type**  =] **"***тип***"**  
 Тип удаляемой пользовательской хранимой процедуры или скрипта. *Тип* — **varchar(16)**, без значения по умолчанию и может принимать одно из следующих значений.  
  
|Значение|Description|  
|-----------|-----------------|  
|**Вставка**|Зарегистрированная пользовательская хранимая процедура или скрипт выполняется при репликации инструкции INSERT.|  
|**обновление**|Зарегистрированная пользовательская хранимая процедура или скрипт выполняется при репликации инструкции UPDATE.|  
|**удалить**|Зарегистрированная пользовательская хранимая процедура или скрипт выполняется при репликации инструкции DELETE.|  
|**custom_script**|Зарегистрированная пользовательская хранимая процедура или скрипт выполняется в конце триггера языка DDL.|  
  
 [  **@publication**  =] **"***публикации***"**  
 Имя публикации, для которой удаляется пользовательская хранимая процедура или скрипт. *Публикация* — **sysname**, значение по умолчанию NULL.  
  
 [  **@article**  =] **"***статьи***"**  
 Имя статьи, для которой удаляется пользовательская хранимая процедура или скрипт. *статья* — **sysname**, значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_unregister_custom_scripting** используется в моментальных снимков и репликации транзакций.  
  
## <a name="permissions"></a>Permissions  
 Только члены **sysadmin** предопределенной роли сервера **db_owner** предопределенной роли базы данных или **db_ddladmin** предопределенной роли базы данных могут выполнять **sp_ unregister_custom_scripting**.  
  
## <a name="see-also"></a>См. также:  
 [sp_register_custom_scripting &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-register-custom-scripting-transact-sql.md)  
  
  
