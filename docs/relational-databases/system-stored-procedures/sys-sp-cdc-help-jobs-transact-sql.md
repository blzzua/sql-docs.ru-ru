---
title: "sys.sp_cdc_help_jobs (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_cdc_help_jobs
- sys.sp_cdc_help_jobs_TSQL
- sp_cdc_help_jobs_TSQL
- sys.sp_cdc_help_jobs
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cdc_help_jobs
ms.assetid: 9399b4bc-8293-408f-b3cb-f904e0657fb5
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4382b14729daf79809e8501f191657b11d4f311e
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2017
---
# <a name="sysspcdchelpjobs-transact-sql"></a>sys.sp_cdc_help_jobs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Выдает сведения о всех заданиях очистки системы отслеживания измененных данных и заданиях записи в текущей базе данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sys.sp_cdc_help_jobs  
```  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**Аргумент job_id**|**uniqueidentifier**|Идентификатор задания.|  
|**job_type**|**nvarchar(20)**|Тип задания.|  
|**maxtrans**|**int**|Максимальное количество транзакций, обрабатываемое в каждом цикле просмотра.<br /><br /> **maxtrans** допустим только для заданий записи.|  
|**maxscans**|**int**|Максимальное количество циклов просмотра, выполняемых для извлечения всех строк из журнала.<br /><br /> **maxscans** допустим только для заданий записи.|  
|**непрерывные**|**bit**|Флаг, указывающий, следует ли выполнять задание записи непрерывно (1) или запускать однократно (0). Дополнительные сведения см. в разделе [sys.sp_cdc_add_job &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sys-sp-cdc-add-job-transact-sql.md).<br /><br /> **непрерывные** допустим только для заданий записи.|  
|**pollingInterval**|**bigint**|Число секунд между циклами просмотра журнала.<br /><br /> **pollingInterval** допустим только для заданий записи.|  
|**хранения**|**bigint**|Число минут, в течение которого строки изменений нужно хранить в таблицах изменений.<br /><br /> **хранения** допустим только для заданий очистки.|  
|**Пороговое значение**|**bigint**|Максимальное число записей, подлежащих удалению, которые могут быть удалены с помощью одной инструкции при очистке.|  
  
## <a name="permissions"></a>Permissions  
 Требуется членство в **db_owner** предопределенной роли базы данных.  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращаются данные об определенных заданиях отслеживания и очистки для базы данных `AdventureWorks2012`.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sys.sp_cdc_help_jobs;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [dbo.cdc_jobs &#40; Transact-SQL &#41;](../../relational-databases/system-tables/dbo-cdc-jobs-transact-sql.md)   
 [sys.sp_cdc_add_job (Transact-SQL)](../../relational-databases/system-stored-procedures/sys-sp-cdc-add-job-transact-sql.md)  
  
  
