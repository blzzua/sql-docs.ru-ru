---
title: "MSSQLSERVER_10521 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 10521 (Database Engine error)
ms.assetid: ba2d7e44-207c-4428-b5f0-c975ac122c0d
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c5af095c81317caed8f98b8d61f687dced828b87
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver10521"></a>MSSQLSERVER_10521
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|10521|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|PG_PARAM_NEEDED|  
|Текст сообщения|Не удалось создать структуру плана "%.\*ls", поскольку значение **@type** указано как "%ls", а параметр "%ls" имеет значение NULL. Этот тип должен иметь значение, отличное от NULL, для этого параметра. Укажите для этого параметра значение, отличное от NULL, либо измените его тип таким образом, чтобы он допускал значение NULL.|  
  
## <a name="explanation"></a>Объяснение  
Для типа, указанного в **@type**, требуется значение, отличное от NULL, но предоставлено значение NULL.  
  
## <a name="user-action"></a>Действие пользователя  
Укажите для этого параметра значение, отличное от NULL, либо измените его тип таким образом, чтобы он допускал значение NULL.  
  
## <a name="see-also"></a>См. также:  
[sp_create_plan_guide (Transact-SQL)](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[Структуры плана](~/relational-databases/performance/plan-guides.md)  
[sp_create_plan_guide_from_handle (Transact-SQL)](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
