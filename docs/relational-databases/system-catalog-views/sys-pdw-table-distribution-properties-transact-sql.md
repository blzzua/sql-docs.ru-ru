---
title: "sys.pdw_table_distribution_properties (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: 
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 639a7475-7c92-41e0-a8ab-ad630eb5aea3
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a192bc274c3d2bc6485c4642882809ee7f375035
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="syspdwtabledistributionproperties-transact-sql"></a>sys.pdw_table_distribution_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Содержит данные о распространении для таблицы.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|**object_id**|**int**|Идентификатор таблицы, для которой три свойства были указаны.||  
|**distribution_policy**|**tinyint**|0 = UNDEFINED<br /><br /> 1 = НЕТ<br /><br /> 2 = HASH<br /><br /> 3 = РЕПЛИЦИРОВАТЬ<br /><br /> 4 = ROUND_ROBIN|REPLICATE применяется только к [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].|  
|**distribution_policy_desc**|**nvarchar(60)**|НЕ ОПРЕДЕЛЕНО, NONE, ХЭШ РЕПЛИЦИРОВАТЬ, SEGMENTED_HEAP|[!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Возвращает ХЭШ или REPLICATE.|  
  
## <a name="see-also"></a>См. также  
 [Хранилище данных SQL и представления каталога хранилища параллельных данных](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
