---
title: "MSsubscriptions (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
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
- MSsubscriptions_TSQL
- MSsubscriptions
dev_langs:
- TSQL
helpviewer_keywords:
- MSsubscriptions system table
ms.assetid: b7e8301d-d115-41f6-8d4f-e0d25f453b25
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6e37aa7c4c227739fe528abe4a2b067fe51a4ba4
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="mssubscriptions-transact-sql"></a>MSsubscriptions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSsubscriptions** содержит по одной строке для каждой опубликованной статьи в подписке, предоставленной локальным распространителем. Эта таблица хранится в базе данных распространителя.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**publisher_database_id**|**int**|Идентификатор базы данных издателя.|  
|**publisher_id**|**smallint**|Идентификатор издателя.|  
|**publisher_db**|**sysname**|Имя базы данных издателя.|  
|**publication_id**|**int**|Идентификатор публикации.|  
|**article_id**|**int**|Идентификатор статьи.|  
|**subscriber_id**|**smallint**|Идентификатор подписчика.|  
|**subscriber_db**|**sysname**|Имя базы данных подписки.|  
|**subscription_type**|**int**|Тип подписки.<br /><br /> **0** = принудительно отправить.<br /><br /> **1** = по запросу.<br /><br /> **2** = анонимная.|  
|**параметром sync_type, равным**|**tinyint**|Тип синхронизации:<br /><br /> **1** = автоматическая.<br /><br /> **2** = нет синхронизации.|  
|**status**|**tinyint**|Состояние подписки.<br /><br /> **0** = неактивно.<br /><br /> **1** = подписка.<br /><br /> **2** = активно.|  
|**subscription_seqno**|**varbinary(16)**|Порядковый номер транзакции моментального снимка памяти.|  
|**snapshot_seqno_flag**|**bit**|Указывает источник порядкового номера транзакции снимка, где значение **1** означает, что **subscription_seqno** имеет порядковый номер моментального снимка.|  
|**independent_agent**|**bit**|Указывает, имеется ли для данной публикации изолированный агент распространителя.|  
|**subscription_time**|**datetime**|Только для внутреннего применения.|  
|**loopback_detection**|**bit**|Применяется к подпискам, которые являются частью двунаправленной топологии репликации транзакций. Механизм распознавания обратной связи определяет, отправляет ли агент распространителя транзакции, созданные в подписчике, обратно подписчику:<br /><br /> **1** = не отправляет обратно.<br /><br /> **0** = отправляет обратно.<br /><br /> Примечание: Этот столбец поддерживается только для обратной совместимости с функциями двунаправленной репликации в [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]. Для более поздних версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] следует использовать одноранговую репликацию. Дополнительные сведения см. в разделе [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md).|  
|**agent_id**|**int**|Идентификатор агента.|  
|**update_mode**|**tinyint**|Тип обновления.|  
|**publisher_seqno**|**varbinary(16)**|Последовательный номер транзакции на издателе для этой подписки.|  
|**ss_cplt_seqno**|**varbinary(16)**|Последовательный номер, используемый для обозначения завершения одновременной обработки моментальных снимков.|  
  
## <a name="see-also"></a>См. также:  
 [Таблицы репликации](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_helpsubscription &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md)  
  
  
