---
title: "SQL Server:Buffer Node | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance-monitor
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLServer:Buffer Node
- Buffer Node object
ms.assetid: fd3f9f0f-7c38-4cfd-a0c5-ee93dd52d9a5
caps.latest.revision: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0a40f828a1325408cf68058df89c29751f9a0edd
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2018
---
# <a name="sql-serverbuffer-node"></a>SQL Server:Buffer Node
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Объект **узел буфера** предоставляет счетчики, которые дополняют счетчики, предоставляемые объектом **диспетчер буферов**. Это позволяет контролировать распределение страницы буферного пула [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для каждого узла неоднородного доступа к памяти (NUMA). Для каждого используемого узла неоднородного доступа к памяти (NUMA) существует экземпляр объекта **узел буфера** . В архитектуре, отличной от NUMA, существует единственный экземпляр объекта **узел буфера** .  
  
## <a name="buffer-node-performance-objects"></a>Объекты производительности узла буфера  
 Объекты производительности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **узла буфера** описаны в следующей таблице.  
  
|Счетчики узла буфера SQL Server|Description|  
|-------------------------------------|-----------------|  
|**Страниц базы данных**|Указывает число страниц с содержимым базы данных в буферном пуле этого узла.|  
|**Ожидаемый срок жизни страницы**|Указывает минимальное количество секунд, в течение которых страница остается в буферном пуле этого узла без ссылок на нее.|  
|**Поисков страниц на локальном узле/с**|Указывает число запросов поиска с этого узла, которые были удовлетворены с этого узла.|  
|**Поисков страниц на удаленных узлах/с**|Указывает число запросов поиска с этого узла, которые были удовлетворены с других узлов.|  
  
 Если SQL Server выполняется на оборудовании, отличном от NUMA, то счетчики объектов **узел буфера** и **диспетчер буферов** должны иметь одинаковые значения.  
  
 На оборудовании NUMA суммы соответствующих счетчиков всех **узлов буфера** должны соответствовать своим дополнениям **диспетчера буферов**.  
  
> [!NOTE]  
>  Значения и суммы счетчиков могут точно не совпадать по причине динамической природы счетчиков и точности отбора значений.  
  
## <a name="see-also"></a>См. также:  
 [SQL Server, объект Buffer Manager](../../relational-databases/performance-monitor/sql-server-buffer-manager-object.md)   
 [Параметры конфигурации сервера «Server Memory»](../../database-engine/configure-windows/server-memory-server-configuration-options.md)   
 [Наблюдение за использованием ресурсов (системный монитор)](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)   
 [sys.dm_os_performance_counters (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql.md)  
  
  
