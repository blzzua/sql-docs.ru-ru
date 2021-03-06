---
title: "MSSQL_ENG002601 | Документация Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSSQL_ENG002601 error
ms.assetid: 657c3ae6-9e4b-4c60-becc-4caf7435c1dc
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e708bdefdee6680a7dcc6d44048a1714a6389916
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/08/2018
---
# <a name="mssqleng002601"></a>MSSQL_ENG002601
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="message-details"></a>Сведения о сообщении  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|2601|  
|Источник события|MSSQLSERVER|  
|Компонент|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Символическое имя|Недоступно|  
|Текст сообщения|Не удается вставить повторяющуюся строку ключа в объект '%.*ls' с уникальным индексом '%.\*ls'.|  
  
## <a name="explanation"></a>Объяснение  
 Это общая ошибка, которая может возникнуть независимо от того, реплицируется база данных или нет. В реплицируемых базах данных эта ошибка возникает, как правило, по причине неправильного управления первичными ключами в топологии. В распределенной среде необходимо убедиться в том, что одно и то же значение не вставлено в первичный ключевой столбец или в любой другой уникальный столбец на нескольких узлах. Возможные причины ошибки:  
  
-   Вставки или обновления строки выполняются более чем в одном узле. И репликация слиянием, и обновляемые подписки для репликации транзакций обеспечивают обнаружение и разрешение конфликта, однако по-прежнему рекомендуется вставлять или обновлять строку только в одном узле. Одноранговые транзакции не обеспечивают обнаружение и разрешение конфликтов. Требуется, чтобы операции вставки и обновления были секционированы.  
  
-   Строка была вставлена на подписчике, который должен быть доступен только для чтения. Подписчики на публикации моментальных снимков должны быть доступны только для чтения, так же как и подписчики на публикации транзакций, если только не используются обновляемые подписки или одноранговые репликации транзакций.  
  
-   Используется таблица со столбцом идентификаторов, однако управление столбцом осуществляется неверно.  
  
-   В публикации слиянием эта ошибка также может возникнуть во время вставки в системную таблицу **MSmerge_contents**. Возникающая ошибка подобна следующей: Не удается вставить повторяющуюся строку ключа в объект MSmerge_contents с уникальным индексом ucl1SycContents.  
  
## <a name="user-action"></a>Действие пользователя  
 Действие по устранению проблемы зависит от причины, по которой она возникла:  
  
-   Вставки или обновления строки выполняются более чем в одном узле.  
  
     Независимо от типа используемой репликации рекомендуется секционировать вставки и обновления везде, где это возможно, так как это уменьшит обработку данных, необходимую для обнаружения и разрешения конфликта. Секционирование вставок и обновлений является необходимым условием при использовании одноранговой репликации транзакций. Дополнительные сведения см. в разделе [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md).  
  
-   Строка была вставлена на подписчике, который должен быть доступен только для чтения.  
  
     Не выполняйте вставку или обновление строк на подписчике, если не используется репликация слиянием, репликация транзакций с обновляемыми подписками или одноранговая репликация транзакций.  
  
-   Используется таблица со столбцом идентификаторов, однако управление столбцом осуществляется неверно.  
  
     При использовании репликации слиянием или репликации с обновляемыми подписками столбцы идентификаторов должны автоматически управляться репликацией. При использовании одноранговой репликации транзакций управление этими столбцами должно выполняться вручную. Дополнительные сведения см. в статье [Репликация столбцов идентификаторов](../../relational-databases/replication/publish/replicate-identity-columns.md).  
  
-   Ошибка возникает во время вставки в системную таблицу **MSmerge_contents**.  
  
     Эта ошибка может возникнуть вследствие неверного значения свойства **join_unique_key**фильтра соединения. Это свойство должно быть установлено равным TRUE, только если соединенный столбец в родительской таблице является уникальным. Если это свойство установлено равным TRUE, но столбец не является уникальным, возникает эта ошибка. Дополнительные сведения об установке данного свойства см. в разделе [Define and Modify a Join Filter Between Merge Articles](../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md).  
  
## <a name="see-also"></a>См. также:  
 [Справочник по ошибкам и событиям (репликация)](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  
