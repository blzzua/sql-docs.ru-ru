---
title: "sys.sp_rda_set_rpo_duration (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-stretch
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.sp_rda_set_rpo_duration
- sys.sp_rda_set_rpo_duration_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_rda_set_rpo_duration stored procedure
ms.assetid: 95c80c5b-9252-4612-9ea7-544c48834fd2
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 82a07f1a75cc35aa05fe47c3a5c1324c0c1c0af4
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="syssprdasetrpoduration-transact-sql"></a>sys.sp_rda_set_rpo_duration (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Задает число часов перенесенных данных SQL Server сохраняет в промежуточную таблицу, чтобы обеспечить полное восстановление удаленной базы данных Azure, если необходима точка восстановления.    
    
 Дополнительные сведения см. в разделе [базы данных Stretch снижает риск потери данных для данных Azure, временно сохраняя перенесенные строки](../../sql-server/stretch-database/backup-stretch-enabled-databases-stretch-database.md#stretchRPO).  
   
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)    
     
## <a name="syntax"></a>Синтаксис    
    
```    
    
sp_rda_set_rpo_duration [ @duration_hrs = ] duration_hrs    
    
```    
    
## <a name="arguments"></a>Аргументы    
 [ @duration_hrs = ] *duration_hrs*    
 Число часов (ненулевое целочисленное значение) требуется SQL Server для хранения в текущей базе данных с включенным Stretch перенесенных данных. Значение по умолчанию и минимальное значение составляет 8 часов.    
 
 > [!NOTE]
 > Более высокие значения требуется больше пространства для хранения на сервере SQL Server.
    
## <a name="permissions"></a>Разрешения    
 Требуются права db_owner.    
    
## <a name="remarks"></a>Remarks    
 Получить текущее значение, запустив [sys.sp_rda_get_rpo_duration &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sys-sp-rda-get-rpo-duration-transact-sql.md).    
    
## <a name="see-also"></a>См. также    
 [sys.sp_rda_get_rpo_duration &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-rda-get-rpo-duration-transact-sql.md)     
 [Восстановление баз данных с поддержкой Stretch (база данных Stretch)](../../sql-server/stretch-database/restore-stretch-enabled-databases-stretch-database.md)     
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)    
    
  
