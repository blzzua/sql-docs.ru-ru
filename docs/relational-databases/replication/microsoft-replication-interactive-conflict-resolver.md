---
title: "Интерактивный сопоставитель конфликтов репликации (Майкрософт) | Документация Майкрософт"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.rep.replconflictviewer.interactiveresolver.f1
ms.assetid: d3d4a480-782b-4b1d-b839-565c8cf6cb24
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4db8c0fe2f91ea0663472d764258c91b8c9aa502
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/08/2018
---
# <a name="microsoft-replication-interactive-conflict-resolver"></a>Интерактивный сопоставитель конфликтов репликации (Microsoft)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Интерактивный сопоставитель конфликтов может применяться для подписок на публикации слиянием, которые синхронизируются с помощью диспетчера синхронизации Windows. Он позволяет просматривать, сравнивать, редактировать и выбирать результаты для конфликтов данных. Репликация также содержит средство просмотра конфликтов, позволяющее просматривать и изменять результаты конфликта после их фиксации. Интерактивный сопоставитель конфликтов позволяет выбирать результаты во время выполнения синхронизации.  
  
> [!NOTE]  
>  Конфликты, затрагивающие логические записи, не отображаются в интерактивном сопоставителе. Для просмотра сведений о таких конфликтах используются хранимые процедуры репликации. Дополнительные сведения см. в статье [Просмотр сведений о конфликтах для публикаций слиянием &#40;программирование репликации на языке Transact-SQL&#41;](../../relational-databases/replication/view-conflict-information-for-merge-publications.md).  
  
## <a name="options"></a>Параметры  
 **Имя столбца**  
 Имена всех столбцов в таблице. Один или несколько столбцов могли содержать конфликтующие данные. Независимо от того, какие столбцы конфликтуют, вся строка, в пользу которой был разрешен конфликт, переписывает всю проигравшую строку.  
  
 **Предлагаемое разрешение**  
 Сопоставитель конфликтов предлагает разрешение для статьи.  
  
 **Издатель**  
 Значение данных на издателе.  
  
 **Подписчик**  
 Значение данных на подписчике.  
  
 **Принять предлагаемый вариант**, **Принять вариант издателя**и **Принять вариант подписчика**  
 Щелкните, чтобы принять строку, которая будет применена на издателе или подписчике, в зависимости от того, в пользу какого участника был разрешен конфликт. Если конфликт был разрешен в пользу подписчика, все другие подписчики получат победившую в конфликте строку при следующей их синхронизации с издателем.  
  
 **Разрешить оставшиеся конфликты автоматически**  
 Автоматическое разрешение оставшихся конфликтов с помощью предлагаемого разрешения, предоставляемого для статьи сопоставителем конфликтов.  
  
 **Регистрация подробностей конфликта для последующего обращения**  
 Регистрация подробностей конфликта в системные таблицы.  
  
## <a name="see-also"></a>См. также:  
 [Интерактивное разрешение конфликтов](../../relational-databases/replication/merge/advanced-merge-replication-conflict-interactive-resolution.md)   
 [Просмотр и разрешение конфликтов данных для публикации слиянием (SQL Server Management Studio)](../../relational-databases/replication/view-and-resolve-data-conflicts-for-merge-publications.md)   
 [Синхронизация подписки с помощью диспетчера синхронизации Windows (Windows Synchronization Manager)](../../relational-databases/replication/synchronize-a-subscription-using-windows-synchronization-manager.md)   
 [Advanced Merge Replication Conflict Detection and Resolution](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)  
  
  
