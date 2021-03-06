---
title: sys.dm_os_memory_nodes (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_os_memory_nodes_TSQL
- sys.dm_os_memory_nodes
- sys.dm_os_memory_nodes_TSQL
- dm_os_memory_nodes
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_memory_nodes dynamic management view
ms.assetid: bf4032fe-7db1-40e9-a62e-d69cebff4b44
caps.latest.revision: 24
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d1cafffe3a2fa227ab8c2450731041ca1cc5d3d4
ms.sourcegitcommit: 8b332c12850c283ae413e0b04b2b290ac2edb672
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/05/2018
---
# <a name="sysdmosmemorynodes-transact-sql"></a>sys.dm_os_memory_nodes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Внутреннее распределение памяти в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] осуществляется с помощью диспетчера памяти [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Отслеживание разницу между счетчиков памяти из **sys.dm_os_process_memory** и внутренних счетчиков может указывать на использование памяти, из внешних компонентов в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] области памяти.  
  
 Узлы создаются для каждого физического узла памяти NUMA. Они могут отличаться от узлов ЦП в **sys.dm_os_nodes**.  
  
 Распределение памяти, выполняемое напрямую с помощью процедур распределения памяти Windows, не отслеживается. В следующей таблице приведены данные о распределении памяти, выполненном исключительно с помощью интерфейса диспетчера памяти [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Вызов его из [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], используйте имя **sys.dm_pdw_nodes_os_memory_nodes**.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**memory_node_id**|**smallint**|Указывает идентификатор узла памяти. Они связаны с **memory_node_id** из **sys.dm_os_memory_clerks**. Не допускает значения NULL.|  
|**virtual_address_space_reserved_kb**|**bigint**|Указывает объем зарезервированного виртуального адресного пространства (в КБ), которое не зафиксировано и не сопоставлено с физическими страницами. Не допускает значения NULL.|  
|**virtual_address_space_committed_kb**|**bigint**|Указывает объем виртуального адресного пространства (в КБ), зафиксированного или сопоставленного с физическими страницами. Не допускает значения NULL.|  
|**locked_page_allocations_kb**|**bigint**|Указывает объем физической памяти (в КБ), заблокированной [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Не допускает значения NULL.|  
|**single_pages_kb**|**bigint**|**Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].<br /><br /> Объем зафиксированной памяти (в КБ), выделенной с помощью механизма распределения одиночных страниц узла памяти. Эта память распределяется из буферного пула. Данное значение указывает на узел, от которого исходит запрос на выделение памяти, а не на физическое положение выделенной памяти.|  
|**pages_kb**|**bigint**|**Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Указывает объем зафиксированной памяти (в КБ), выделенной данным узлом NUMA с помощью механизма распределения страниц диспетчера памяти. Не допускает значения NULL.|  
|**multi_pages_kb**|**bigint**|**Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].<br /><br /> Объем зафиксированной памяти (в КБ), выделенной с помощью механизма многостраничного распределения потоков этого узла. Указанная память выделяется из пространства, находящегося вне буферного пула. Данное значение указывает на узел, от которого исходит запрос на выделение памяти, а не на физическое положение выделенной памяти.|  
|**shared_memory_reserved_kb**|**bigint**|Указывает объем общей памяти (в КБ), зарезервированной данным узлом. Не допускает значения NULL.|  
|**shared_memory_committed_kb**|**bigint**|Указывает объем общей памяти (в КБ), зафиксированной данным узлом. Не допускает значения NULL.|  
|**cpu_affinity_mask**|**bigint**|**Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Только для внутреннего применения. Не допускает значения NULL.|  
|**online_scheduler_mask**|**bigint**|**Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Только для внутреннего применения. Не допускает значения NULL.|  
|**processor_group**|**smallint**|**Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Только для внутреннего применения. Не допускает значения NULL.|  
|**foreign_committed_kb**|**bigint**|**Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Указывает объем общей памяти (в КБ), зафиксированной другими узлами памяти. Не допускает значения NULL.|  
|**target_kb** |**bigint** |**Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)].<br /><br /> Указывает цель памяти для узла памяти, в КБ. |   
|**pdw_node_id**|**int**|**Применяется к**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Идентификатор для узла, это распределение.|  
  
## <a name="permissions"></a>Разрешения

На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], требуется `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], требуется `VIEW DATABASE STATE` разрешение в базе данных.   

## <a name="see-also"></a>См. также  
  [Динамические административные представления, относящиеся к операционной системе SQL Server &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


