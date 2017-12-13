---
title: "sys.dm_db_xtp_nonclustered_index_stats (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/29/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_db_xtp_nonclustered_index_stats_TSQL
- dm_db_xtp_nonclustered_index_stats
- sys.dm_db_xtp_nonclustered_index_stats_TSQL
- sys.dm_db_xtp_nonclustered_index_stats
dev_langs: TSQL
helpviewer_keywords: sys.dm_db_xtp_nonclustered_index_stats
ms.assetid: d55ba31c-296c-419b-9c4b-c126e0a3d156
caps.latest.revision: "10"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e1b54d3955dd250a3d3799170e4ad15a7312802f
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2017
---
# <a name="sysdmdbxtpnonclusteredindexstats-transact-sql"></a>sys.dm_db_xtp_nonclustered_index_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

  Динамическое административное представление sys.dm_db_xtp_nonclustered_index_stats содержит статистику операций с некластеризованными индексами в оптимизированных для памяти таблицах. Динамическое административное представление sys.dm_db_xtp_nonclustered_index_stats содержит по одной строке для каждого некластеризованного индекса в оптимизированной для памяти таблице в текущей базе данных.  
  
 Статистика, приведенная в sys.dm_db_xtp_nonclustered_index_stats, собирается во время создания структуры индекса в памяти. Структуры индекса в памяти создаются повторно при перезапуске базы данных.  
  
 Для отслеживания работы индексов и выявления закономерностей при выполнении операций DML и в случае, если база данных переводится в режим «в сети», используйте представление sys.dm_db_xtp_nonclustered_index_stats. При перезапуске базы данных с оптимизированной для памяти таблицей индекс строится путем вставки в память по одной строке за раз. Количество разбиений, объединений и консолидаций страниц позволяет понять, какая работа была проделана для построения индекса при переводе базы данных в режим «в сети». Эти значения также можно оценить до и после выполнения серии операций DML.  
  
 Большое количество повторных попыток указывает на проблему с параллелизмом. Обратитесь в службу поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)].  
  
 Дополнительные сведения об оптимизированных для памяти некластеризованных индексах см. в разделе [Обзор SQL Server In-Memory OLTP внутренние компоненты](http://t.co/T6zToWc6y6), страница 17.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|object_id|**int**|Идентификатор объекта.|  
|xtp_object_id|**bigint**|Идентификатор таблицы, оптимизированные для памяти.|  
|index_id|**int**|Идентификатор индекса.|  
|delta_pages|**bigint**|Общее число разностных страниц для этого индекса в дереве.|  
|internal_pages|**bigint**|Для внутреннего использования. Общее число внутренних страниц для этого индекса в дереве.|  
|leaf_pages|**bigint**|Общее число конечных страниц для этого индекса в дереве.|  
|outstanding_retired_nodes|**bigint**|Для внутреннего использования. Отображает общее число узлов для этого индекса во внутренних структурах.|  
|page_update_count|**bigint**|Совокупное количество операций, обновляющих страницу в индексе.|  
|page_update_retry_count|**bigint**|Совокупное количество повторных попыток выполнить операцию, обновляющую страницу в индексе.|  
|page_consolidation_count|**bigint**|Совокупное количество консолидаций страниц в индексе.|  
|page_consolidation_retry_count|**bigint**|Совокупное количество повторных попыток выполнить операцию консолидации страниц.|  
|page_split_count|**bigint**|Совокупное количество операций разбиения страниц в индексе.|  
|page_split_retry_count|**bigint**|Совокупное количество повторных попыток выполнить операцию разбиения страниц.|  
|key_split_count|**bigint**|Совокупное количество разбиения ключей в индексе.|  
|key_split_retry_count|**bigint**|Совокупное количество повторных попыток выполнить операцию разбиения ключа.|  
|page_merge_count|**bigint**|Совокупное количество операций объединения страниц в индексе.|  
|page_merge_retry_count|**bigint**|Совокупное количество повторных попыток выполнить операцию объединения страниц.|  
|key_merge_count|**bigint**|Совокупное количество операций объединения ключей в индексе.|  
|key_merge_retry_count|**bigint**|Совокупное количество повторных попыток выполнить операцию объединения ключей.|  
  
## <a name="permissions"></a>Permissions  
 Необходимо разрешение VIEW DATABASE STATE на текущую базу данных.  
  
## <a name="see-also"></a>См. также:  
 [Динамические административные представления таблиц, оптимизированных для памяти &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql.md)  
  
  