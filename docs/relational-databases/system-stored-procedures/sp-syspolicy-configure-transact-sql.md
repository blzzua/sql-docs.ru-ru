---
title: "процедура sp_syspolicy_configure (Transact-SQL) | Документы Microsoft"
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
- sp_syspolicy_configure
- sp_syspolicy_configure_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syspolicy_configure
ms.assetid: 70c10922-9345-4190-ba69-808a43f760da
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e4ff49cd5be072fb288bb721b781474da93b7ba9
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="spsyspolicyconfigure-transact-sql"></a>sp_syspolicy_configure (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Настраивает параметры управления на основе политик, такие как параметр включения управления на основе политик.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_syspolicy_configure [ @name = ] 'name'  
    , [ @value = ] value  
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@name =** ] **'***name***'**  
 Имя параметра, который нужно настроить. *имя* — **sysname**является обязательным и не может быть NULL или пустая строка.  
  
 *имя* может иметь любое из следующих значений:  
  
-   Enabled — определяет, включено ли управление на основе политик.  
  
-   HistoryRetentionInDays — указывает число дней, в течение которых хранится журнал выполнения политик. Если это значение равно 0, то журнал не удаляется автоматически.  
  
-   LogOnSuccess — указывает, заносится ли успешное выполнение политик в журнал управления на основе политик.  
  
 [ **@value =** ] *value*  
 Значение, которое связано с указанным значением для *имя*. *значение* — **sql_variant**и является обязательным.  
  
-   Если указать «Enabled» для *имя*, воспользуйтесь одним из следующих значений:  
  
    -   0 = отключает управление на основе политик;  
  
    -   1 = включает управление на основе политик.  
  
-   Если указать «HistoryRententionInDays» для *имя*, укажите число дней в виде целочисленного значения.  
  
-   Если указать «LogOnSuccess» для *имя*, воспользуйтесь одним из следующих значений:  
  
    -   0 = в журнал заносится только неуспешное выполнение политики;  
  
    -   1 = в журнал заносится и успешное, и неуспешное выполнение политики.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Remarks  
 Процедура sp_syspolicy_configure должна выполняться в контексте системной базы данных msdb.  
  
 Чтобы просмотреть текущие значения этих параметров, запросите системное представление msdb.dbo.syspolicy_configuration.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в предопределенной роли базы данных PolicyAdministratorRole.  
  
> [!IMPORTANT]  
>  Возможно повышение учетных данных: пользователи в роли PolicyAdministratorRole могут создавать триггеры сервера и планировать выполнение политик, влияющих на работу экземпляра [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Например, пользователи в роли PolicyAdministratorRole могут создать политику, которая может запретить создание большинства объектов в компоненте [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Вследствие возможного повышения прав учетных данных роль PolicyAdministratorRole должна предоставляться только пользователям, имеющим право изменять конфигурацию компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
## <a name="examples"></a>Примеры  
 В следующем примере включается управление на основе политик.  
  
```  
EXEC msdb.dbo.sp_syspolicy_configure @name = N'Enabled'  
, @value = 1;  
  
GO  
```  
  
 В следующем примере устанавливается 14-дневный срок хранения журнала политик.  
  
```  
EXEC msdb.dbo.sp_syspolicy_configure @name = N'HistoryRetentionInDays'  
, @value = 14;  
  
GO  
```  
  
 В следующем примере для управления на основе политик настраивается регистрация и успешного, и неуспешного выполнения политик.  
  
```  
EXEC msdb.dbo.sp_syspolicy_configure @name = N'LogOnSuccess'  
, @value = 1;  
  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Управление на основе политик хранимых процедур &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/policy-based-management-stored-procedures-transact-sql.md)   
 [sp_syspolicy_set_config_enabled &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-set-config-enabled-transact-sql.md)   
 [sp_syspolicy_set_config_history_retention &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-set-config-history-retention-transact-sql.md)   
 [sp_syspolicy_set_log_on_success &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-set-log-on-success-transact-sql.md)  
  
  
