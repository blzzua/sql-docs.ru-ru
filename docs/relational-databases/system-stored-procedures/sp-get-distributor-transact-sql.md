---
title: "Хранимая процедура sp_get_distributor (Transact-SQL) | Документы Microsoft"
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
- sp_get_distributor
- sp_get_distributor_TSQL
helpviewer_keywords:
- sp_get_distributor
ms.assetid: f0134448-bc17-4f2f-bd81-619351ce56ac
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5a9a52ebbb8e17ff88008b2b04208a0d383179ea
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="spgetdistributor-transact-sql"></a>Хранимая процедура sp_get_distributor (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Определяет, установлен ли на сервере распространитель. Хранимая процедура выполняется на компьютере, где выполняется поиск распространителя, в любой базе данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_get_distributor   
```  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**установлен**|**int**|**0** = нет; **1** = Да|  
|**сервер распространения**|**sysname**|Имя сервера распространителя|  
|**базы данных распространителя установлена**|**int**|**0** = нет; **1** = Да|  
|**— издатель распространителя**|**int**|**0** = нет; **1** = Да|  
|**имеется Удаленный распространяющий издатель**|**int**|**0** = нет; **1** = Да|  
  
## <a name="remarks"></a>Замечания  
 **Хранимая процедура sp_get_distributor** используется в основном [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] в моментальных снимков, транзакций и репликации слиянием.  
  
## <a name="permissions"></a>Permissions  
 Любой пользователь может выполнять **sp_get_distributor**. НЕНУЛЕВОЙ результирующий набор возвращается, если эта хранимая процедура выполняется членами **db_owner** или **replmonitor** фиксированных ролей базы данных распространителя или членами  **db_owner** предопределенной роли базы данных по крайней мере одной опубликованной базы данных. Набор НЕНУЛЕВОЙ результат также возвращается, если эта хранимая процедура выполняется для пользователей в списке доступа к публикации (PAL) из по крайней мере одной опубликованной базы данных, либо в списке доступа к публикации базы данных распространителя для издателя, отличном от издателя SQL Server можно также выполнять **sp _get_distributor**.  
  
## <a name="see-also"></a>См. также:  
 [Настройка публикации и распространения](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [Distributor and Publisher Information Script](../../relational-databases/replication/administration/distributor-and-publisher-information-script.md)  (Скрипт вывода сведений о распространителе и издателе)  
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
