---
title: "Запуск монитора репликации | Документация Майкрософт"
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
- Replication Monitor, starting
ms.assetid: e037bd27-cc87-4ee9-9e5f-83f6d717cfa4
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9e1a339c818c4199656d3114d214b2908501a017
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/08/2018
---
# <a name="start-the-replication-monitor"></a>Запуск монитора репликации
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Монитор репликации может быть запущен из командной строки или в среде [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] на любом экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Запустив монитор репликации, добавьте в монитор одного или несколько издателей. Дополнительные сведения см. в статье [Добавление и удаление издателей в мониторе репликации](../../../relational-databases/replication/monitor/add-and-remove-publishers-from-replication-monitor.md).  
  
### <a name="to-start-replication-monitor-from-sql-server-management-studio"></a>Запуск монитора репликации из среды SQL Server Management Studio  
  
1.  Подключитесь к экземпляру [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в среде [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], а затем раскройте узел сервера.  
  
2.  Щелкните правой кнопкой мыши папку **Репликация** или любую из ее вложенных папок, а затем щелкните **Запустить монитор репликации**.  
  
### <a name="to-start-replication-monitor-from-the-command-prompt"></a>Запуск монитора репликации из командной строки  
  
1.  Находясь в командной строке, перейдите в каталог установки средств. Путь по умолчанию: [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]Tools\Binn\.  
  
2.  Запустите файл sqlmonitor.exe.  
  
## <a name="see-also"></a>См. также:  
 [Наблюдение за репликацией](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  
