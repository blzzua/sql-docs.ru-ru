---
title: "sys.pdw_replicated_table_cache_state (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/03/2017
ms.prod: 
ms.prod_service: sql-data-warehouse
ms.service: sql-data-warehouse
ms.component: system-catalog-views
ms.reviewer: barbkess
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
author: ronortloff
ms.author: rortloff
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5efc510645a6a5648c4d1e2c6e2c05567159e6e2
ms.sourcegitcommit: 0d904c23663cebafc48609671156c5ccd8521315
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2018
---
# <a name="syspdwreplicatedtablecachestate-transact-sql"></a>sys.pdw_replicated_table_cache_state (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

  Возвращает состояние кэша, связанный с реплицированной таблицы с **object_id**.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|object_id|**int**|Идентификатор объекта для таблицы. В разделе [sys.objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).<br /><br /> **object_id** является ключом для этого представления.||  
|state|**nvarchar(40)**|Состояние кэша реплицируемой таблицы для этой таблицы.|Не «готово», «Готово»|  
  
## <a name="example"></a>Пример
В этом примере соединяет sys.pdw_replicated_table_cache_state с sys.tables для получения имени таблицы и состояние кэша реплицируемой таблицы.

```sql
SELECT t.[name], p.[object_id], p.[state]
  FROM sys.pdw_replicated_table_cache_state p 
  JOIN sys.tables t ON t.object_id = p.object_id
```



## <a name="next-steps"></a>Следующие шаги  
 Список всех представлений каталога для хранилища данных SQL и параллельных хранилищ данных см. в разделе [хранилище данных SQL и представления каталога хранилища параллельных данных](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md).   
  
