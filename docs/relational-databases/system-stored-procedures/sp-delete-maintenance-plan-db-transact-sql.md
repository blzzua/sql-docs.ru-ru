---
title: "Хранимая процедура sp_delete_maintenance_plan_db (Transact-SQL) | Документы Microsoft"
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
- sp_delete_maintenance_plan_db_TSQL
- sp_delete_maintenance_plan_db
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_maintenance_plan_db
- maintenance plans [SQL Server], deleting
- removing maintenance plan
- disassociating maintenance plan
ms.assetid: d1e8afb5-12ee-492b-a770-ba708ed7c8a4
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 69f523fbdb044d889cc3ee961d38ae6e6681136c
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="spdeletemaintenanceplandb-transact-sql"></a>Хранимая процедура sp_delete_maintenance_plan_db (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Отсоединяет определенный план обслуживания от указанной базы данных.  
  
> [!NOTE]  
>  Эта хранимая процедура используется планами обслуживания базы данных. Эта возможность заменена планами обслуживания, не использующими данную хранимую процедуру. Используйте данную процедуру для поддержки планов обслуживания баз данных в установках, которые были обновлены с предыдущих версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_delete_maintenance_plan_db [ @plan_id = ] 'plan_id' ,   
     [ @db_name = ] 'database_name'   
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@plan_id =**] **'***plan_id***'**  
 Указывает идентификатор плана обслуживания. *plan_id* — **uniqueidentifier**.  
  
 [ **@db_name =**] **'***database_name***'**  
 Указывает имя базы данных, которая должна быть удалена из плана обслуживания. *database_name* — **sysname**.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Remarks  
 **Хранимая процедура sp_delete_maintenance_plan_db** должна запускаться из **msdb** базы данных.  
  
 **Sp_delete_maintenance_plan_db** хранимая процедура удаляет взаимосвязь между планом обслуживания и указанной базы данных, удаляет и не разрушает базу данных.  
  
 Когда **sp_delete_maintenance_plan_db** Удаляет последнюю базу данных из плана обслуживания, эта хранимая процедура также удаляет план обслуживания.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера могут выполнять **sp_delete_maintenance_plan_db**.  
  
## <a name="examples"></a>Примеры  
 Удаление плана обслуживания в **AdventureWorks2012** базы данных, добавленного ранее при помощи **sp_add_maintenance_plan_db**.  
  
```  
EXECUTE   sp_delete_maintenance_plan_db N'FAD6F2AB-3571-11D3-9D4A-00C04FB925FC', N'AdventureWorks2012';  
```  
  
## <a name="see-also"></a>См. также  
 [Планы обслуживания](../../relational-databases/maintenance-plans/maintenance-plans.md)   
 [План обслуживания базы данных хранимой процедуры &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/database-maintenance-plan-stored-procedures-transact-sql.md)  
  
  
