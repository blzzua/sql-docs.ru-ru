---
title: "MSmerge_tombstone (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSmerge_tombstone_TSQL
- MSmerge_tombstone
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_tombstone system table
ms.assetid: 8b3fc7bf-729b-40f2-8a26-e7dfbe8ddb38
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 55644aa0543de70ca4ec11ee65a446d073ce3556
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="msmergetombstone-transact-sql"></a>MSmerge_tombstone (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSmerge_tombstone** таблица содержит сведения об удаленных строках и позволяет удаления распространяются на другие подписчики. Эта таблица хранится в базах данных публикации и подписки.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**ROWGUID**|**uniqueidentifier**|Идентификатор строки.|  
|**tablenick**|**int**|Псевдоним таблицы.|  
|**type**|**tinyint**|Тип удаления:<br /><br /> 1 = удаление пользователем.<br /><br /> 5 = строка больше не принадлежит отфильтрованной секции.<br /><br /> 6 = удаление системой.|  
|**журнала обращений и преобразований**|**varbinary(249)**|Указывает версию удаленной записи и ее обновления, известные на момент удаления. Обеспечивает правила согласованного разрешения конфликта, когда подписчик обновляет строку при удалении ее другим подписчиком.|  
|**Создание**|**int**|Назначается при удалении строки. Если подписчик запрашивает поколение N, отправляются только захоронения с поколением >= N.|  
|**logical_record_parent_rowguid**|**uniqueidentifier**|Идентифицирует логическую запись, которой принадлежит удаленная строка.|  
|**logical_record_lineage**|**Varbinary(501)**|Пары псевдонимов подписчиков и номеров версий, используемые для ведения журнала удалений логической записи, которой принадлежит данная строка.|  
  
## <a name="see-also"></a>См. также:  
 [Таблицы репликации &#40; Transact-SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
