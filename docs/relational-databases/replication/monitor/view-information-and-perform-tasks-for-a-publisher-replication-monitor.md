---
title: "Просмотр сведений и выполнение задач на издателе (монитор репликации) | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
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
- Publishers [SQL Server replication], Replication Monitor tasks
- viewing Publisher information
- Publishers [SQL Server replication], viewing information
ms.assetid: 1e777e95-377a-4de3-b965-867464aadaaf
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6d82b24e92b90f7e4688b9f97746dc40ad94dd1b
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/08/2018
---
# <a name="view-information-and-perform-tasks-for-a-publisher-replication-monitor"></a>Просмотр сведений и выполнение задач на издателе (монитор репликации)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Монитор репликации содержит следующие вкладки, на которых отображаются сведения о выбранном издателе:  
  
-   **Публикации**  
  
     На этой вкладке отображаются сведения обо всех публикациях на выбранном издателе.  
  
-   **Список наблюдения за подписками**  
  
     Эта вкладка предназначена для отображения сведений о подписках из всех публикаций, доступных на выбранном издателе, для которых имеются ошибки, предупреждения или наихудшие показатели производительности. Эта вкладка не отображается для запущенных версий распространителей, предшествующих [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].  
  
-   Вкладка**Агенты**   
  
     На этой вкладке отображаются подробные сведения об агентах и заданиях, используемых всеми типами репликации. Эта вкладка также позволяет запускать и останавливать агенты и задания.  
  
 Чтобы просмотреть дополнительные сведения о параметрах каждой вкладки, щелкните вкладку на правой панели, а затем щелкните **Справка** в строке меню. Сведения о запуске монитора репликации см. в [этой статье](../../../relational-databases/replication/monitor/start-the-replication-monitor.md).  
  
### <a name="to-view-information-and-perform-tasks-for-a-publisher"></a>Просмотр сведений и выполнение задач для издателя  
  
1.  Раскройте группу издателей на левой панели, затем щелкните издателя.  
  
2.  Чтобы просмотреть сведения обо всех публикациях, щелкните вкладку **Публикации** .  
  
3.  Чтобы просмотреть сведения о подписках, перейдите на вкладку **Список наблюдения за подписками** . Эта вкладка также позволяет получать доступ к более подробным сведениям и выполнять следующие задачи:  
  
    -   Для просмотра подробных сведений об агенте, связанном с подпиской, щелкните правой кнопкой мыши подписку, а затем выберите **Просмотреть сведения**.  
  
    -   Чтобы просмотреть свойства подписки, щелкните правой кнопкой мыши подписку, а затем щелкните **Свойства**.  
  
    -   Чтобы синхронизировать принудительную подписку, щелкните правой кнопкой мыши подписку и выберите **Запустить синхронизацию**.  
  
    -   Чтобы повторно инициализировать подписку, щелкните правой кнопкой мыши подписку и выберите **Повторно инициализировать подписку**.  
  
4.  Чтобы просмотреть сведения об агентах, перейдите на вкладку **Агенты** . На этой вкладке можно также просмотреть другие подробные сведения и выполнить дополнительные задачи.  
  
    -   Чтобы просмотреть подробные сведения об агенте (например, информационные сообщения и возможные сообщения об ошибках), щелкните правой кнопкой мыши агент, а затем щелкните **Просмотреть сведения**.  
  
    -   Чтобы просмотреть подробные сведения о задании, запустившем агента (например, расписание, описание шагов задания и т. п.), щелкните правой кнопкой мыши агент, а затем щелкните **Свойства**.  
  
    -   Чтобы управлять профилями агентов, щелкните правой кнопкой мыши агент, затем выберите **Профиль агента**. Дополнительные сведения см. в статье [Работа с профилями агента репликации](../../../relational-databases/replication/agents/work-with-replication-agent-profiles.md).  
  
    -   Чтобы запустить агент, который еще не запущен, щелкните правой кнопкой мыши этот агент, а затем щелкните **Запустить агент**.  
  
    -   Чтобы остановить агент, который запущен, щелкните правой кнопкой мыши этот агент, а затем щелкните **Остановить агент**.  
  
## <a name="see-also"></a>См. также:  
 [Просмотр и изменение свойств издателя и распространителя](../../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [Наблюдение за репликацией](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  
