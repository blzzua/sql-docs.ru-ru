---
title: sys.dm_db_log_space_usage (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 06/29/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sys.dm_db_log_space_usage
- sys.dm_db_log_space_usage_TSQL
- dm_db_log_space_usage
- dm_db_log_space_usage_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_log_space_usage dynamic management view
ms.assetid: f6b40060-c17d-472f-b0a3-3b350275d487
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4578d219630f97245d4cf46c6ddb701457e92ac3
ms.sourcegitcommit: 8b332c12850c283ae413e0b04b2b290ac2edb672
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/05/2018
---
# <a name="sysdmdblogspaceusage-transact-sql"></a>sys.dm_db_log_space_usage (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Возвращает пространства сведения об использовании для журнала транзакций. 
  
> [!NOTE]
> Все файлы журнала транзакций будут объединены.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|database_id|**smallint**|Идентификатор базы данных.|  
|total_log_size_in_bytes |**bigint** |Размер журнала  |
|used_log_space_in_bytes |**bigint** |Занято размер журнала  |     
|used_log_space_in_percent |**real** |Занято размер журнала в процентах от размера всего журнала |
|log_space_in_bytes_since_last_backup |**bigint** |Объем пространства, используемого с момента последней резервной копии журнала <br />**Применяется к:** [!INCLUDE[sssql14-md](../../includes/sssql14-md.md)] через [!INCLUDE[sscurrent-md](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDS](../../includes/sssds-md.md)].|
    
  
## <a name="permissions"></a>Разрешения  

На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], требуется `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], требуется `VIEW DATABASE STATE` разрешение в базе данных.   
  
## <a name="examples"></a>Примеры  
  
### <a name="a-determine-the-amount-of-free-log-space-in-tempdb"></a>A. Определение объема свободного журнала пространства в базе данных tempdb   
Следующий запрос возвращает общего свободного пространства журнала в мегабайтах (МБ), доступных в базе данных tempdb.

```sql
USE tempdb;  
GO  

SELECT (total_log_size_in_bytes - used_log_space_in_bytes)*1.0/1024/1024 AS [free log space in MB]  
FROM sys.dm_db_log_space_usage;  
```
  
## <a name="see-also"></a>См. также  
[Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
[Динамические административные представления, относящиеся к базе данных &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)   
[sys.dm_db_file_space_usage](../../relational-databases/system-dynamic-management-views/sys-dm-db-file-space-usage-transact-sql.md)    
[sys.dm_db_task_space_usage &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-task-space-usage-transact-sql.md)   
[sys.dm_db_session_space_usage (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-session-space-usage-transact-sql.md)  
[sys.dm_db_log_info (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-log-info-transact-sql.md)    
[sys.dm_db_log_stats (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-log-stats-transact-sql.md) 



