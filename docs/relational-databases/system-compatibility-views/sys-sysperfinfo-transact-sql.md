---
title: "sys.sysperfinfo (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-compatibility-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sysperfinfo_TSQL
- sys.sysperfinfo_TSQL
- sys.sysperfinfo
- sysperfinfo
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sysperfinfo compatibility view
- sysperfinfo system table
ms.assetid: e22a81cd-27de-4690-9443-6aad6393bd3c
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 92d1cb29e339017f13c5b784f2b1459cf1a19432
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="syssysperfinfo-transact-sql"></a>sys.sysperfinfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] представление внутренних счетчиков, которые могут отображаться с помощью системного монитора Windows.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**object_name**|**nchar(128)**|Имя объекта производительности, такие как **SQLServer:LockManager** или **SQLServer:BufferManager**.|  
|**counter_name**|**nchar(128)**|Имя счетчика производительности в рамках объекта, таких как **запросов страниц** или **запрошенные блокировки**.|  
|**имя_экземпляра**|**nchar(128)**|Именованный экземпляр счетчика. Например, существуют счетчики, предназначенные для каждого типа блокировки, такие как **таблицы**, **страницы**, **ключ**, и т. д. Имя экземпляра позволяет различать похожие счетчики.|  
|**cntr_value**|**bigint**|Текущее значение счетчика. Часто оно является счетчиком уровня или счетчиком монотонно возрастающей величины, подсчитывающей наступление событий экземпляра.|  
|**cntr_type**|**int**|Тип счетчика, как определено архитектурой производительности Windows.|  
  
## <a name="see-also"></a>См. также  
 [Сопоставление системных таблиц с системными представлениями &#40; Transact-SQL &#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Представления совместимости (Transact-SQL)](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
