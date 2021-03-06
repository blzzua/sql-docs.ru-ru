---
title: "REVOKE, отмена разрешения на асимметричный ключ (Transact-SQL) | Документы Майкрософт"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- permissions [SQL Server], asymmetric keys
- asymmetric keys [SQL Server], permissions
- REVOKE statement, asymmetric keys
ms.assetid: 1a1063e8-ffc7-4775-a40d-e155740ad7b2
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ae298d40c75f35df8ed93c850ecadd797155656b
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="revoke-asymmetric-key-permissions-transact-sql"></a>REVOKE, отмена разрешений на асимметричный ключ (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Отменяет разрешения на асимметричный ключ.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
REVOKE [ GRANT OPTION FOR ] { permission  [ ,...n ] }   
    ON ASYMMETRIC KEY :: asymmetric_key_name   
    { TO | FROM } database_principal [ ,...n ]  
    [ CASCADE ]  
    [ AS revoking_principal ]  
```  
  
## <a name="arguments"></a>Аргументы  
 GRANT OPTION FOR  
 Указывает, что возможность предоставлять указанное разрешение будет отменена.  
  
> [!IMPORTANT]  
>  Если участник обладает указанным разрешением без параметра GRANT, будет отменено само разрешение.  
  
 *permission*  
 Указывает разрешение, которое может быть отменено на сборку. Перечислены ниже.  
  
 ON ASYMMETRIC KEY **::***asymmetric_key_name*  
 Задает асимметричный ключ, для которого отменяется разрешение. Квалификатор области **::** является обязательным.  
  
 *database_principal*  
 Задает участника, у которого отменяется разрешение. Это может быть:  
  
-   Пользователь базы данных  
  
-   Роль базы данных  
  
-   Роль приложения  
  
-   Пользователь базы данных, сопоставленный имени входа Windows  
  
-   Пользователь базы данных, сопоставленный группе Windows  
  
-   Пользователь базы данных, сопоставленный сертификату  
  
-   Пользователь базы данных, сопоставленный асимметричному ключу  
  
-   Пользователь базы данных, не сопоставленный серверу-участнику  
  
 CASCADE  
 Показывает, что отменяемое разрешение также отменяется для других участников, для которых оно было предоставлено или запрещено данным участником. Само разрешение отменено не будет.  
  
> [!CAUTION]  
>  Каскадная отмена разрешения, предоставленного с помощью параметра WITH GRANT OPTION, приведет к отмене разрешений GRANT и DENY для этого разрешения.  
  
 AS *revoking_principal*  
 Указывает участника, от которого участник, выполняющий данный запрос, получает право на отмену разрешения. Это может быть:  
  
-   Пользователь базы данных  
  
-   Роль базы данных  
  
-   Роль приложения  
  
-   Пользователь базы данных, сопоставленный имени входа Windows  
  
-   Пользователь базы данных, сопоставленный группе Windows  
  
-   Пользователь базы данных, сопоставленный сертификату  
  
-   Пользователь базы данных, сопоставленный асимметричному ключу  
  
-   Пользователь базы данных, не сопоставленный серверу-участнику  
  
## <a name="remarks"></a>Remarks  
 Асимметричный ключ — защищаемое на уровне базы данных содержимое базы данных, являющейся его родителем в иерархии разрешений. Ниже перечислены наиболее специфичные и ограниченные разрешения (вместе с наиболее общими разрешениями, куда они входят неявно), которые могут быть отменены для ассиметричного ключа.  
  
|Разрешение асимметричного ключа|Содержится в разрешении асимметричного ключа|Содержится в разрешении базы данных|  
|-------------------------------|------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY ASYMMETRIC KEY|  
|REFERENCES|CONTROL|REFERENCES|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Разрешения  
 Требуется разрешение CONTROL на асимметричный ключ.  
  
## <a name="see-also"></a>См. также:  
 [REVOKE (Transact-SQL)](../../t-sql/statements/revoke-transact-sql.md)   
 [Разрешения (компонент Database Engine)](../../relational-databases/security/permissions-database-engine.md)   
 [Участники (компонент Database Engine)](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [CREATE CERTIFICATE (Transact-SQL)](../../t-sql/statements/create-certificate-transact-sql.md)   
 [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-asymmetric-key-transact-sql.md)   
 [CREATE APPLICATION ROLE (Transact-SQL)](../../t-sql/statements/create-application-role-transact-sql.md)   
 [Иерархия шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
