---
title: "sys.sysconfigures (Transact-SQL) | Документы Microsoft"
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
- sys.sysconfigures
- sysconfigures
- sys.sysconfigures_TSQL
- sysconfigures_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sysconfigures compatibility view
- sysconfigures system table
ms.assetid: 146bf10a-c898-4676-a2a1-673fb1cee7a2
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3b423d21fe65751502e41de6639bc85b0ac8c61f
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="syssysconfigures-transact-sql"></a>sys.sysconfigures (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит по одной строке для каждого установленного пользователем параметра конфигурации. **sysconfigures** содержит параметры конфигурации, заданные перед последним запуском [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], а также все динамические наборы параметров конфигурации с тех пор.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**value**|**int**|Значение переменной, доступное для изменения пользователем. Оно используется компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)], только если была выполнена инструкция RECONFIGURE.|  
|**config**|**int**|Номер переменной конфигурации.|  
|**комментарий**|**nvarchar(255)**|Описание параметра конфигурации.|  
|**status**|**smallint**|Битовая карта, указывающая состояние параметра. Возможные значения:<br /><br /> 0 = статический. Настройка вступает в силу после перезапуска сервера.<br /><br /> 1 = динамический. Переменная вступает в силу после выполнения инструкции RECONFIGURE.<br /><br /> 2 = расширенный. Переменная показывается только если **Показывать дополнительные параметры** имеет значение. Настройка вступает в силу после перезапуска сервера.<br /><br /> 3 = расширенный динамический.|  
  
## <a name="see-also"></a>См. также  
 [Сопоставление системных таблиц с системными представлениями &#40; Transact-SQL &#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Представления совместимости (Transact-SQL)](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
