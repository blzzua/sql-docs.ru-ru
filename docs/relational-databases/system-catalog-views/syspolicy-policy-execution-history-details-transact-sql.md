---
title: "syspolicy_policy_execution_history_details (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/09/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- syspolicy_policy_execution_history_details
- syspolicy_policy_execution_history_details_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- syspolicy_policy_execution_history_details view
ms.assetid: 97ef6573-5e8b-4ba5-8ae0-7901e79a9683
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f560563cb2f558a55d9aeafd1e8a9d6071dfffb6
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="syspolicypolicyexecutionhistorydetails-transact-sql"></a>syspolicy_policy_execution_history_details (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Показывает выполненные условные выражения, целевые объекты выполнения выражений, результат каждого выполнения и сведения об ошибках, возникших при выполнении. Следующая таблица описывает столбцы в представлении syspolicy_execution_history_details.  
  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|detail_id|**bigint**|Идентификатор записи. Каждая запись соответствует попытке выполнить или обеспечить одно условное выражение из политики. Если условие применялось к нескольким целевым объектам, для каждого условия будет выведено несколько детализированных записей — по одной на целевой объект.|  
|history_id|**bigint**|Идентификатор события в журнале. Каждое событие в журнале соответствует одной попытке выполнения политики. Поскольку одно условие может включать несколько условных выражений и несколько целевых объектов, history_id можно создавать несколько детализированных записей. Использовать для соединения этого представления в столбец history_id [syspolicy_policy_execution_history](../../relational-databases/system-catalog-views/syspolicy-policy-execution-history-transact-sql.md) представления.|  
|target_query_expression|**nvarchar(max)**|Целевой объект политики и syspolicy_policy_execution_history представления.|  
|execution_date|**datetime**|Дата и время создания этой детализированной записи.|  
|набор по|**бит**|Успешный или неуспешный результат вычисления условного выражения для данного целевого объекта:<br /><br /> 0 (успешное завершение) или 1 (неуспешное завершение)|  
|result_detail|**nvarchar(max)**|Результирующее сообщение. Генерируется только в том случае, когда обеспечивается аспектом.|  
|exception_message|**nvarchar(max)**|Сообщение, выданное в результате возникшего исключения.|  
|exception|**nvarchar(max)**|Описание возникшего исключения.|  
  
## <a name="remarks"></a>Remarks  
 При устранении неполадок политики управления на основе запроса, просмотра syspolicy_policy_execution_history_details, чтобы определить, какие цель и условие выражения результат был неуспешным, если они не удалось и просмотреть соответствующие ошибки.  
  
 Далее приводится запрос, сочетающий представления `syspolicy_policy_execution_history_details`, `syspolicy_policy_execution_history_details` и `syspolicy_policies` и выводящий имя политики, имя условия и подробные сведения об ошибках.  
  
```  
SELECT Pol.name AS Policy,   
Cond.name AS Condition,   
PolHistDet.target_query_expression,   
PolHistDet.execution_date,   
PolHistDet.result,   
PolHistDet.result_detail,   
PolHistDet.exception_message,   
PolHistDet.exception   
FROM msdb.dbo.syspolicy_policies AS Pol  
JOIN msdb.dbo.syspolicy_conditions AS Cond  
    ON Pol.condition_id = Cond.condition_id  
JOIN msdb.dbo.syspolicy_policy_execution_history AS PolHist  
    ON Pol.policy_id = PolHist.policy_id  
JOIN msdb.dbo.syspolicy_policy_execution_history_details AS PolHistDet  
    ON PolHist.history_id = PolHistDet.history_id  
WHERE PolHistDet.result = 0 ;  
```  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в роли PolicyAdministratorRole базы данных msdb.  
  
## <a name="see-also"></a>См. также  
 [Администрирование серверов с помощью управления на основе политик](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)   
 [Административные представления на основе политик (Transact-SQL)](../../relational-databases/system-catalog-views/policy-based-management-views-transact-sql.md)  
  
  
