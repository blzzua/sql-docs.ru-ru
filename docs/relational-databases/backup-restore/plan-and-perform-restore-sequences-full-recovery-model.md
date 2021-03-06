---
title: "Планирование и выполнение последовательностей восстановления (модель полного восстановления) | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: backup-restore
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-backup-restore
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- restore sequences [SQL Server], planning for
- full recovery model [SQL Server], planning restore sequences
ms.assetid: 9cbefaf8-d2b6-41c9-83fc-b3807a841fe2
caps.latest.revision: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: df70e2b5fce0983fa3501b6bd53376f75d10d900
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2018
---
# <a name="plan-and-perform-restore-sequences-full-recovery-model"></a>Планирование и выполнение последовательностей восстановления (модель полного восстановления)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  В этой теме приведены рекомендации по планированию и выполнению последовательности восстановления баз данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] согласно модели полного восстановления. *Последовательность восстановления* — это последовательность из одной или нескольких инструкций [RESTORE](../../t-sql/statements/restore-statements-transact-sql.md) . Как правило, она инициализирует содержимое базы данных, файлы или страницы, производя последовательность восстановления (стадия копирования данных), выполняет накат записанных транзакций (стадия повтора) и откатывает нефиксированные транзакции (стадия отката).  
  
 В простых случаях для последовательности восстановления необходима только полная резервная копия базы данных, разностная резервная копия и последующие резервные копии журнала. В таких ситуациях выстроить правильную последовательность восстановления нетрудно. Например, чтобы восстановить всю базу данных до точки сбоя, начинают с резервного копирования журнала действующих транзакций ( *заключительного фрагмента журнала* ). Затем восстанавливают последнюю полную резервную копию базы данных, последнюю разностную резервную копию базы данных (если она есть), а затем все последующие резервные копии журналов в порядке их выполнения.  
  
 В более сложных случаях может оказаться совсем непросто определить правильную последовательность восстановления. Например, для последовательности восстановления может потребоваться несколько резервных копий файла или восстановление данных до определенного момента времени. В самых сложных случаях может потребоваться обход разветвленного пути восстановления, образующего одну или несколько вилок восстановления.  
  
> [!NOTE]  
>  Последовательность резервных копий данных и журналов, которая позволяет привести базу данных к состоянию на определенный момент времени, называется *путь восстановления* . Путь восстановления представляет собой определенный набор преобразований, отражающих развитие базы данных в течение времени и, в то же время, поддерживающих согласованность данных в ней. Путь восстановления описывает диапазон номеров LSN от точки запуска (LSN,GUID) до конечной точки (LSN,GUID). Диапазон номеров LSN в ветви восстановления может проходить по одной или более ветвям от начала до конца.  
  
## <a name="to-plan-a-restore-sequence"></a>Планирование последовательности восстановления  
 Перед запуском последовательности восстановления выполните следующие действия.  
  
1.  По возможности создайте резервную копию заключительного фрагмента журнала базы данных. Дополнительные сведения см. в статье [Резервные копии заключительного фрагмента журнала (SQL Server)](../../relational-databases/backup-restore/tail-log-backups-sql-server.md).  
  
2.  Определите целевую точку восстановления.  
  
     Целевая точка восстановления может быть любым моментом времени или меткой в пределах резервной копии журнала транзакций. Дополнительные сведения см. в статье [Восстановление базы данных SQL Server до определенного момента времени (модель полного восстановления)](../../relational-databases/backup-restore/restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md) или [Использование помеченных транзакций для согласованного восстановления связанных баз данных (модель полного восстановления)](../../relational-databases/backup-restore/use-marked-transactions-to-recover-related-databases-consistently.md).  
  
3.  Определите тип выполняемого восстановления. Дополнительные сведения см. в статье [Обзор процессов восстановления (SQL Server)](../../relational-databases/backup-restore/restore-and-recovery-overview-sql-server.md).  
  
4.  Определите, какие резервные копии необходимы, и убедитесь, что доступны необходимые наборы носителей и устройства резервного копирования. Дополнительные сведения см. в статьях [Устройства резервного копирования (SQL Server)](../../relational-databases/backup-restore/backup-devices-sql-server.md) и [Наборы носителей, семейства носителей и резервные наборы данных Sets (SQL Server)](../../relational-databases/backup-restore/media-sets-media-families-and-backup-sets-sql-server.md).  
  
## <a name="to-perform-a-restore-sequence"></a>Выполнение последовательности восстановления  
 Выполнение последовательности восстановления.  
  
1.  Чтобы начать последовательность, восстановите одну или несколько резервных копий данных, например: резервную копию данных, частичную резервную копию, одну или несколько резервных копий файлов.  
  
2.  При необходимости можно восстановить последние разностные резервные копии, основанные на этих полных резервных копиях.  
  
     Для каждой полной резервной копии, которую планируется восстановить, определите, является ли она основой для каких-либо разностных резервных копий. Если да, то по возможности восстановите самую последнюю разностную копию. Дополнительные сведения см. в статье [Разностные резервные копии (SQL Server)](../../relational-databases/backup-restore/differential-backups-sql-server.md).  
  
3.  Произведите накат базы данных, по порядку восстановив резервные копии журналов, заканчивая резервной копией, содержащей точку восстановления. Необходимость в применении всех резервных копий зависит от того, какая из них содержит целевую точку восстановления.  
  
    -   Если точка восстановления совпадает с точкой сбоя, необходимо восстановить все резервные копии журнала, созданные с момента восстановления последней резервной копии данных (полной или разностной). Дополнительные сведения см. в статье [Применение резервных копий журналов транзакций (SQL Server)](../../relational-databases/backup-restore/apply-transaction-log-backups-sql-server.md).  
  
    -   Для восстановления на момент времени самые последние резервные копии журнала могут не потребоваться. Если используется [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], то помощник по восстановлению базы данных гарантирует, что будут выбраны только резервные копии, которые необходимо восстановить на указанный момент времени. Эти резервные копии составляют рекомендованный план восстановления для данного восстановления на момент времени. Дополнительные сведения см. в статье [Восстановление базы данных SQL Server до определенного момента времени (модель полного восстановления)](../../relational-databases/backup-restore/restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md).  
  
## <a name="restarting-a-restore-sequence"></a>Перезапуск последовательности восстановления  
 Столкнувшись с проблемой в ходе выполнения последовательности восстановления, можно выйти и перезапустить последовательность восстановления заново с самого начала. Например, если случайно было восстановлено слишком много резервных копий журнала и тем самым восстановление перешло запланированную точку восстановления, необходимо перезапустить последовательность восстановления и выполнить ее до резервной копии журнала, содержащей целевую точку восстановления.  
  
## <a name="see-also"></a>См. также:  
 [Общие сведения о резервном копировании (SQL Server)](../../relational-databases/backup-restore/backup-overview-sql-server.md)   
 [Обзор процессов восстановления (SQL Server)](../../relational-databases/backup-restore/restore-and-recovery-overview-sql-server.md)   
 [Выполнение полного восстановления базы данных (модель полного восстановления)](../../relational-databases/backup-restore/complete-database-restores-full-recovery-model.md)   
 [Восстановление в сети (SQL Server)](../../relational-databases/backup-restore/online-restore-sql-server.md)   
 [Файлы из резервных копий (модель полного восстановления)](../../relational-databases/backup-restore/file-restores-full-recovery-model.md)   
 [Восстановление страниц (SQL Server)](../../relational-databases/backup-restore/restore-pages-sql-server.md)   
 [Поэтапное восстановление (SQL Server)](../../relational-databases/backup-restore/piecemeal-restores-sql-server.md)  
  
  
