---
title: "Получение сведений об уведомлениях о событиях | Документация Майкрософт"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: service-broker
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- event notifications [SQL Server], metadata
- status information [SQL Server], event notifications
- metadata [SQL Server], event notifications
ms.assetid: 8bc10867-66d6-4f57-ac32-a6c29f3327cd
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1ef3efe96a38e594a945653ca08469811e813340
ms.sourcegitcommit: 0d904c23663cebafc48609671156c5ccd8521315
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2018
---
# <a name="get-information-about-event-notifications"></a>Получение сведений об уведомлениях о событиях
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Следующие представления каталога доступны для запроса метаданных об уведомлениях о событиях.  
  
 **Получение сведений об уведомлениях о событиях несерверного уровня**  
  
-   [sys.event_notifications (Transact-SQL)](../../relational-databases/system-catalog-views/sys-event-notifications-transact-sql.md)  
  
> [!NOTE]  
>  Необходимые минимальные требования для просмотра метаданных о любом уведомлении в **sys.event_notifications** , созданном на уровне базы данных: иметь разрешение CONTROL, ALTER, TAKE OWNERSHIP или VIEW DEFINITION для базы данных, быть владельцем уведомления о событии или иметь разрешение ALTER ANY DATABASE EVENT NOTIFICATION. Необходимые минимальные требования для уведомлений о событиях, созданных в определенной очереди: иметь разрешение CONTROL, ALTER, TAKE OWNERSHIP или VIEW DEFINITION для объекта, быть владельцем уведомления о событии или иметь разрешение ALTER ANY DATABASE EVENT NOTIFICATION.  
  
 **Получение сведений об уведомлениях о событиях серверного уровня**  
  
-   [sys.server_event_notifications (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-event-notifications-transact-sql.md)  
  
> [!NOTE]  
>  Необходимые минимальные требования для просмотра метаданных любого уведомления о событии в представлении каталога **sys.server_event_notifications**: иметь разрешение CONTROL или VIEW ANY DEFINITION для сервера, быть именем входа или владельцем уведомления о событии или иметь разрешение ALTER ANY EVENT NOTIFICATION.  
  
 **Получение сведений обо всех событиях, которые могут создать уведомления**  
  
-   [sys.event_notification_event_types (Transact-SQL)](../../relational-databases/system-catalog-views/sys-event-notification-event-types-transact-sql.md)  
  
> [!NOTE]  
>  Это представление каталога не возвращает группы событий.  
  
## <a name="see-also"></a>См. также:  
 [Уведомления о событиях](../../relational-databases/service-broker/event-notifications.md)  
  
  
