---
title: "MSSQLSERVER_3181 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 3181 (Database Engine error)
ms.assetid: e6d2e716-5263-477c-ad0e-7bcbfef4c1f3
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 928fe1db4bf164e80b765c9b77dc3fefe3517b5d
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver3181"></a>MSSQLSERVER_3181
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Идентификатор события|3181|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|LDDB_STORAGE_VERIFY|  
|Текст сообщения|Попытка восстановления из этой резервной копии может привести к недостатку места на диске. Подробные сведения будут приведены в следующих сообщениях.|  
  
## <a name="explanation"></a>Объяснение  
Инструкция RESTORE VERIFYONLY проверяет доступное место на диске, где будет восстанавливаться база данных.  
  
### <a name="possible-causes"></a>Возможные причины  
Может быть, недостаточно места на диске для восстановления проверяемой резервной копии.  
  
## <a name="user-action"></a>Действие пользователя  
Восстановить резервную копию в расположении, где достаточно места на диске, либо обеспечить больше места на диске.  
  
## <a name="see-also"></a>См. также:  
[Восстановление базы данных в новое место (SQL Server)](~/relational-databases/backup-restore/restore-a-database-to-a-new-location-sql-server.md)  
[Восстановление файлов в новое место (SQL Server)](~/relational-databases/backup-restore/restore-files-to-a-new-location-sql-server.md)  
[RESTORE (Transact-SQL)](~/t-sql/statements/restore-statements-transact-sql.md)  
[RESTORE VERIFYONLY (Transact-SQL)](~/t-sql/statements/restore-statements-verifyonly-transact-sql.md)  
  
