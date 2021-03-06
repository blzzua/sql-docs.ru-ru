---
title: "Класс событий Broker:Corrupted Message | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: event-classes
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Broker:Corrupted Message event class
ms.assetid: 084bf198-2138-438e-bdc7-4ff1e04300f7
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a0da6275497d4b073329e07bd16540e6b6153f1a
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/12/2018
---
# <a name="brokercorrupted-message-event-class"></a>Broker:Corrupted Message, класс событий
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создает событие **Broker:Corrupted Message** , когда компонент Service Broker получает поврежденное сообщение.  
  
## <a name="brokercorrupted-message-event-class-data-columns"></a>Столбцы данных класса событий Broker:Corrupted Message  
  
|Столбец данных|Тип|Description|Номер столбца|Фильтруемый|  
|-----------------|----------|-----------------|-------------------|----------------|  
|**ApplicationName**|**nvarchar**|Имя клиентского приложения, установившего соединение с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Этот столбец заполняется значениями, передаваемыми приложением, а не отображаемым именем программы.|10|Да|  
|**BigintData1**|**bigint**|Порядковый номер этого сообщения.|52|нет|  
|**BinaryData**|**image**|Текст сообщения.|2|Да|  
|**ClientProcessID**|**int**|Идентификатор, присвоенный компьютером сервера процессу, в котором работает клиентское приложение. Этот столбец данных заполняется в том случае, если клиент вводит идентификатор клиентского процесса.|9|Да|  
|**DatabaseID**|**int**|Идентификатор базы данных, указанной в инструкции USE *database* , или базы данных по умолчанию, если для данного экземпляра инструкция USE *database* не выполнялась. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] отображает имя базы данных, если столбец данных **ServerName** захвачен при трассировке и сервер доступен. Определите значение для базы данных, используя функцию DB_ID.|3|Да|  
|**Ошибка**|**int**|Идентификационный номер сообщения в **sys.messages** для текста в событии.|31|нет|  
|**EventClass**|**int**|Тип захваченного класса событий. Всегда **161** для **Broker:Corrupted Message**.|27|нет|  
|**EventSequence**|**int**|Порядковый номер этого события.|51|нет|  
|**FileName**|**nvarchar**|Сетевой адрес удаленной конечной точки.|36|нет|  
|**GUID**|**uniqueidentifier**|Идентификатор диалога, к которому принадлежит поврежденное сообщение. Этот идентификатор передается в составе сообщения и является общим для обоих участников диалога.|54|нет|  
|**Host Name**|**nvarchar**|Имя компьютера, на котором выполняется клиентская программа. Заполнение этого столбца данных производится в том случае, если клиент предоставляет имя узла. Чтобы определить имя узла, используйте функцию HOST_NAME.|8|Да|  
|**IntegerData**|**int**|Фрагментарный номер этого сообщения.|25|Да|  
|**IsSystem**|**int**|Указывает, произошло событие в системном или в пользовательском процессе. 1 = системный, 0 = пользовательский.|60|нет|  
|**LoginSid**|**image**|Идентификатор безопасности вошедшего в систему пользователя. Значение идентификатора безопасности уникально для каждого имени входа на сервере.|41|Да|  
|**NTDomainName**|**nvarchar**|Домен Windows, к которому принадлежит пользователь.|7|Да|  
|**NTUserName**|**nvarchar**|Имя пользователя, которому принадлежит соединение, создавшее это событие.|6|Да|  
|**ObjectName**|**nvarchar**|Имя службы другой стороны диалога и строка соединения, используемая удаленной базой данных для установки соединения с этой базой данных.|34|нет|  
|**RoleName**|**nvarchar**|Роль конечной точки, получающей это сообщение. Одно из следующих значений.<br /><br /> **initiator**: получающая конечная точка является инициатором диалога.<br /><br /> **target**: получающая конечная точка является адресатом диалога.|38|нет|  
|**ServerName**|**nvarchar**|Имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , подвергаемого трассировке.|26|нет|  
|**Severity**|**int**|Если ошибка стала причиной, по которой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] удалил сообщение — серьезность этой ошибки.|29|нет|  
|**SPID**|**int**|Идентификатор процесса сервера, который [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] присвоил процессу, связанному с клиентом.|12|Да|  
|**StartTime**|**datetime**|Время начала события, если доступно.|14|Да|  
|**Состояние**|**int**|Указывает место в исходном коде [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , которое вызвало это событие. Каждое место, которое может вызвать это событие, обозначается отдельным кодом состояния. Сотрудник службы технической поддержки Microsoft может использовать этот код состояния для обнаружения участка, выполнение которого привело к событию.|30|нет|  
|**TextData**|**ntext**|Описание выявленного повреждения.|1|Да|  
|**Transaction ID**|**bigint**|Назначенный системой идентификатор транзакции.|4|нет|  
  
 Столбец **TextData** этого события содержит пояснение, описывающее проблему с сообщением.  
  
  
