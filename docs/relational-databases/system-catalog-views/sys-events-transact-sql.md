---
title: "sys.Events (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.events_TSQL
- sys.events
- events_TSQL
- events
dev_langs:
- TSQL
helpviewer_keywords:
- sys.events catalog view
ms.assetid: f245a97a-80fc-43fb-a6e4-139420c9a47a
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8479e77d947936c027dfe9e656a0f7847cc7d3a1
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2017
---
# <a name="sysevents-transact-sql"></a>sys.events (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Содержит по одной строке для каждого события, для которого срабатывает триггер или уведомление о событии. Эти события представляют типы событий, указанных при создании уведомления о событии или триггера с помощью [CREATE TRIGGER](../../t-sql/statements/create-trigger-transact-sql.md) или [CREATE EVENT NOTIFICATION](../../t-sql/statements/create-event-notification-transact-sql.md).  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|Идентификатор триггера или уведомления о событии. Это значение вместе с **тип**уникальным образом идентифицирует строку.|  
|**type**|**int**|Событие, которое возникает при срабатывании триггера.|  
|**type_desc**|**nvarchar(60)**|Описание события, которое возникает при срабатывании триггера.|  
|**is_trigger_event**|**bit**|1 = событие триггера.<br /><br /> 0 = событие уведомления.|  
|**event_group_type**|**int**|Группа событий, для которой создается уведомление о триггере или событии, или значение NULL, если уведомления для группы событий не создаются.|  
|**event_group_type_desc**|**nvarchar(60)**|Описание группы событий, для которой создается уведомление о триггере или событии, или значение NULL, если уведомления для группы событий не создаются.|  
  
## <a name="see-also"></a>См. также:  
 [Представления каталога объектов &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
