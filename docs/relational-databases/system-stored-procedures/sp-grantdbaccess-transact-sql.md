---
title: "sp_grantdbaccess (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
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
- sp_grantdbaccess
- sp_grantdbaccess_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_grantdbaccess
ms.assetid: 3eb09513-03f1-42f8-9917-3a1f3a579bec
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4e8e67cc8f4672a650f7909fc71a759c3a856fcf
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2017
---
# <a name="spgrantdbaccess-transact-sql"></a>sp_grantdbaccess (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Добавляет нового пользователя в текущую базу данных.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Используйте [CREATE USER](../../t-sql/statements/create-user-transact-sql.md) вместо него.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_grantdbaccess [ @loginame = ] 'login'  
    [ , [ @name_in_db = ] 'name_in_db' [ OUTPUT ] ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@loginame =** ] **"***входа* **"**  
 Имя группы Windows, имени входа Windows или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], которое будет сопоставлено с новым пользователем базы данных. Имена групп Windows и имена входа Windows должны быть дополнены именем домена Windows в виде *домена*\\*входа*, например **LONDON\Joeb**. Указанное имя входа не может быть уже сопоставлено с пользователем в базе данных. *Имя входа* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@name_in_db=**] **"***name_in_db***"** [ **ВЫВОДА**]  
 Имя нового пользователя базы данных. *name_in_db* является ВЫХОДНОЙ переменной с типом данных **sysname**и значение по умолчанию NULL. Если не указан, *входа* используется. Если указано как переменная OUTPUT со значением NULL,  **@name_in_db**  равно *входа*. *name_in_db* не должен существовать в текущей базе данных.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_grantdbaccess** вызывает создание пользователя, которая поддерживает дополнительные параметры. Сведения о создании пользователей баз данных см. в разделе [CREATE USER &#40; Transact-SQL &#41; ](../../t-sql/statements/create-user-transact-sql.md). Чтобы удалить пользователя базы данных из базы данных, используйте [DROP USER](../../t-sql/statements/drop-user-transact-sql.md).  
  
 **sp_grantdbaccess** не может выполняться внутри пользовательской транзакции.  
  
## <a name="permissions"></a>Permissions  
 Требуется членство в **db_owner** предопределенной роли базы данных или **db_accessadmin** предопределенной роли базы данных.  
  
## <a name="examples"></a>Примеры  
 В следующем примере используется `CREATE USER` Добавление пользователя базы данных для имени входа Windows `Edmonds\LolanSo` к текущей базе данных. Новому пользователю присваивается имя `Lolan`. Этот метод является предпочтительным при создании пользователя базы данных.  
  
```  
CREATE USER Lolan FOR LOGIN [Edmonds\LolanSo];  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Безопасность хранимых процедур &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [CREATE USER (Transact-SQL)](../../t-sql/statements/create-user-transact-sql.md)   
 [УДАЛИТЬ пользователя &#40; Transact-SQL &#41;](../../t-sql/statements/drop-user-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
