---
title: "Профили агента репликации | Документация Майкрософт"
ms.custom: 
ms.date: 03/07/2017
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
- Distribution Agent, profiles
- replication [SQL Server], agents and profiles
- replication agent profiles [SQL Server]
- Merge Agent, profiles
- agents [SQL Server replication], profiles
- Queue Reader Agent, profiles
- profiles [SQL Server], replication agents
- Snapshot Agent, profiles
- Log Reader Agent, profiles
ms.assetid: 0e980725-e42f-4283-94cb-d8a6dba5df62
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1894d29e1b34cf6abb889a89e2d1e8782d92c373
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/08/2018
---
# <a name="replication-agent-profiles"></a>Профили агента репликации
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  При настройке репликации на распространителе устанавливается набор профилей агентов. Профиль агента содержит набор параметров, используемых при каждом запуске агента: каждый агент регистрируется на распространителе во время запуска и запрашивает параметры в своем профиле. Для подписок на публикацию слиянием, которые используют веб-синхронизацию, профили загружаются и хранятся на подписчике. Если профиль изменяется, профиль, хранящийся на подписчике, обновляется при следующем запуске агента слияния. Дополнительные сведения о веб-синхронизации см. в разделе [Web Synchronization for Merge Replication](../../../relational-databases/replication/web-synchronization-for-merge-replication.md).  
  
 Служба репликации предоставляет каждому агенту профиль по умолчанию и набор дополнительных предопределенных профилей для агента чтения журнала, агента распространителя и агента слияния. Кроме предоставляемых профилей можно создать профили в соответствии с требованиями приложений. Профиль агента позволяет легко изменять ключевые параметры для всех агентов, связанных с данным профилем. Например, если имеются 20 агентов моментальных снимков и необходимо изменить запрашиваемое значение времени ожидания (параметр **-QueryTimeout** ), можно обновить профиль, используемый данными агентами моментальных снимков, и все агенты этого типа будут автоматически использовать новое значение при следующем запуске.  
  
 Можно также использовать различные профили для различных экземпляров агента. Например, агент слияния, который обеспечивает подключение издателя и распространителя посредством коммутируемого соединения, может использовать набор параметров, наиболее подходящих для медленного соединения при помощи профиля **медленная линия связи** .  
  
> [!NOTE]  
>  Если значение параметра агента указывается в командной строке, данное значение отменяет набор значений для этого параметра в профиле агента.  
  
 **Использование и изменение профилей агента**  
  
-   [Работа с профилями агента репликации](../../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)  
  
## <a name="snapshot-agent-profiles"></a>Профили агента моментальных снимков  
 В приведенной ниже таблице указываются параметры, определенные в профиле по умолчанию для агента моментальных снимков. Дополнительные сведения об этих параметрах см. в разделе [Replication Snapshot Agent](../../../relational-databases/replication/agents/replication-snapshot-agent.md).  
  
||значение по умолчанию|  
|-|-------------|  
|**-BcpBatchSize**|100000|  
|**-HistoryVerboseLevel**|2|  
|**-LoginTimeout**|15|  
|**-QueryTimeout**|1800|  
  
## <a name="log-reader-agent-profiles"></a>Профили агента чтения журнала  
 В приведенной ниже таблице указываются параметры, определенные в профилях для агента чтения журнала. Каждый столбец в этой таблице представляет собой именованный профиль. Дополнительные сведения об этих параметрах см. в разделе [Replication Log Reader Agent](../../../relational-databases/replication/agents/replication-log-reader-agent.md).  
  
||значение по умолчанию|подробный журнал|  
|-|-------------|---------------------|  
|**-HistoryVerboseLevel**|1|2|  
|**-LoginTimeout**|15|15|  
|**-LogScanThreshold**|500000|500000|  
|**-PollingInterval**|5|5|  
|**-QueryTimeout**|1800|1800|  
|**-ReadBatchSize**|500|500|  
  
## <a name="distribution-agent-profiles"></a>Профили агента распространителя  
 В приведенной ниже таблице указываются параметры, определенные в профилях для агента распространителя. Каждый столбец в этой таблице представляет собой именованный профиль. Дополнительные сведения об этих параметрах см. в разделе [Replication Distribution Agent](../../../relational-databases/replication/agents/replication-distribution-agent.md).  
  
||значение по умолчанию|подробный журнал|диспетчер синхронизации Windows|продолжать при возникновении ошибок согласованности данных|профиль распространителя для потоковой передачи данных OLEDB|  
|-|-------------|---------------------|-------------------------------------|-----------------------------------------|----------------------------------------------|  
|**-BcpBatchSize**|100000|100000|1000|100000|2147473647|  
|**-CommitBatchSize**|100|100|100|100|100|  
|**-CommitBatchThreshold**|1000|1000|1000|1000|1000|  
|**-HistoryVerboseLevel**|1|2|1|1|1|  
|**-KeepAliveMessageInterval**|300|300|300|300|300|  
|**-LoginTimeout**|15|15|15|15|15|  
|**-MaxBcpThreads**|1|1|1|1|1|  
|**-MaxDeliveredTransactions**|0|0|0|0|0|  
|**-OledbStreamThreshold**|NULL|NULL|NULL|NULL|32768|  
|**-PacketSize**|NULL|NULL|NULL|NULL|32768|  
|**-PollingInterval**|5|5|5|5|5|  
|**-QueryTimeout**|1800|1800|1800|1800|1800|  
|**-SkipErrors**|NULL|NULL|NULL|**-SkipErrors** 2601:2627:20598|NULL|  
|**-TransactionsPerHistory**|100|100|100|100|100|  
|**-UseOledbStreaming**|NULL|NULL|NULL|NULL|**-UseOledbStreaming**|  
  
## <a name="merge-agent-profiles"></a>Профили агента слияния  
 В приведенной ниже таблице указываются параметры, определенные в профилях для агента слияния. Каждый столбец в этой таблице представляет собой именованный профиль. Дополнительные сведения об этих параметрах см. в разделе [Replication Merge Agent](../../../relational-databases/replication/agents/replication-merge-agent.md).  
  
||значение по умолчанию|подробный журнал|диспетчер синхронизации Windows|проверка правильности количества строк|проверка правильности количества строк и контрольной суммы|медленная линия связи|межсерверный большого объема|  
|-|-------------|---------------------|-------------------------------------|-------------------------|--------------------------------------|---------------|------------------------------------|  
|**-BcpBatchSize**|100000|100000|1000|100000|100000|100000|100000|  
|**-ChangesPerHistory**|100|50|50|100|100|100|1000|  
|**-DestThreads**|2|1|1|1|1|1|4|  
|**-DownloadGenerationsPerBatch**|50|50|50|50|50|1|500|  
|**-DownloadReadChangesPerBatch**|100|100|100|100|100|100|100|  
|**-DownloadWriteChangesPerBatch**|100|100|100|100|100|100|100|  
|**-FastRowCount**|1|1|1|1|1|1|1|  
|**-HistoryVerboseLevel**|2|3|1|1|2|1|2|  
|**-KeepAliveMessageInterval**|300|300|300|300|300|300|300|  
|**-LoginTimeout**|15|15|15|15|15|15|15|  
|**-MaxDownloadChanges**|0|0|0|0|0|0|0|  
|**-MaxUploadChanges**|0|0|0|0|0|0|0|  
|**-MetadataRetentionCleanup**|1|1|1|1|1|1|1|  
|**-NumDeadlockRetries**|5|5|5|5|5|5|5|  
|**-ParallelUploadDownload**|NULL|NULL|NULL|NULL|NULL|NULL|1|  
|**-PollingInterval**|60|60|60|60|60|60|60|  
|**-QueryTimeout**|300|300|300|300|300|300|600|  
|**-QueueSizeMultiplier**|NULL|NULL|NULL|NULL|NULL|NULL|5|  
|**-SrcThreads**|2|2|2|2|2|1|3|  
|**-StartQueueTimeout**|0|0|0|0|0|0|0|  
|**-UploadGenerationsPerBatch**|50|50|50|50|50|1|500|  
|**-UploadReadChangesPerBatch**|100|100|100|100|100|100|100|  
|**-UploadWriteChangesPerBatch**|100|100|100|100|100|100|100|  
|**-Validate**|0|0|0|1|3|0|0|  
|**-ValidateInterval**|60|60|60|60|60|60|60|  
  
## <a name="queue-reader-agent-profiles"></a>Профили агента чтения очереди  
 В приведенной ниже таблице указываются параметры, определенные в профиле по умолчанию для агента чтения очереди. Дополнительные сведения об этих параметрах см. в разделе [Replication Queue Reader Agent](../../../relational-databases/replication/agents/replication-queue-reader-agent.md).  
  
||значение по умолчанию|  
|-|-------------|  
|**-HistoryVerboseLevel**|1|  
|**-LoginTimeout**|15|  
|**-PollingInterval**|5|  
|**-QueryTimeout**|1800|  
  
## <a name="see-also"></a>См. также:  
 [Администрирование агента репликации](../../../relational-databases/replication/agents/replication-agent-administration.md)   
 [Просмотр и изменение параметров командной строки агента репликации (SQL Server Management Studio)](../../../relational-databases/replication/agents/view-and-modify-replication-agent-command-prompt-parameters.md)   
 [Replication Agent Executables Concepts](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md)  
  
  
