---
title: "sp_browsesnapshotfolder (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
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
- sp_browsesnapshotfolder
- sp_browsesnapshotfolder_TSQL
helpviewer_keywords:
- sp_browsesnapshotfolder
ms.assetid: 0872edf2-4038-4bc1-a68d-05ebfad434d2
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4b31f3bb0e865452fd6f557a4832b04a21c11624
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="spbrowsesnapshotfolder-transact-sql"></a>sp_browsesnapshotfolder (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает полный путь к последнему моментальному снимку, созданному для данной публикации. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_browsesnapshotfolder [@publication= ] 'publication'  
    { [ , [ @subscriber = ] 'subscriber' ]  
 [ , [ @subscriber_db = ] 'subscriber_db' ] }  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@publication=**] **"***публикации***"**  
 Имя публикации, которая содержит статью. *Публикация* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@subscriber=**] **"***подписчика***"**  
 Имя подписчика. *подписчик* — **sysname**, значение по умолчанию NULL.  
  
 [  **@subscriber_db=**] **"***subscriber_db***"**  
 Имя базы данных подписки. *subscriber_db* — **sysname**, значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**snapshot_folder**|**nvarchar(512)**|Полный путь к каталогу моментальных снимков.|  
  
## <a name="remarks"></a>Замечания  
 **sp_browsesnapshotfolder** используется в репликации моментальных снимков и репликации транзакций.  
  
 Если *подписчика* и *subscriber_db* поля содержат значение NULL, хранимая процедура возвращает последний моментальный снимок для публикации можно найти папку моментальных снимков. Если *подписчика* и *subscriber_db* поля заданы, хранимая процедура возвращает папку моментальных снимков для указанной подписки. Если для данной публикации не был создан моментальный снимок, то возвращается пустой результирующий набор.  
  
 Если публикация настроена так, что моментальные снимки создаются и в рабочем каталоге издателя, и в папке моментальных снимков, то результирующий набор состоит из двух строк. Первая строка содержит папку моментальных снимков публикации, а вторая — рабочий каталог издателя. **sp_browsesnapshotfolder** полезно для определения каталога, в котором формируются файлы моментальных снимков.  
  
## <a name="permissions"></a>Permissions  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять **sp_browsesnapshotfolder**.  
  
## <a name="see-also"></a>См. также:  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
