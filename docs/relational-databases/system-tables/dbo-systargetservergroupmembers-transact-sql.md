---
title: "dbo.systargetservergroupmembers (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dbo.systargetservergroupmembers_TSQL
- dbo.systargetservergroupmembers
- systargetservergroupmembers
- systargetservergroupmembers_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- systargetservergroupmembers system table
ms.assetid: ee1b2ebd-03cb-4b91-a5d2-98d4d38f82ec
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 15bb35f90da3dfd8862a92fbaba1ccb2f36cbe89
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="dbosystargetservergroupmembers-transact-sql"></a>dbo.systargetservergroupmembers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Записывает, какие целевые серверы связаны в настоящее время с данной многосерверной группой.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**servergroup_id**|**int**|Идентификатор серверной группы|  
|**server_id**|**int**|Идентификатор сервера|  
  
  
