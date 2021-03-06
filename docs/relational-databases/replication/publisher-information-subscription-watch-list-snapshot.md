---
title: "Сведения об издателе, список просмотра подписок (моментальный снимок) | Документация Майкрософт"
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
f1_keywords:
- sql13.rep.monitor.publisherinfo.subscriptionssummary.snapshot.f1
ms.assetid: 2ebeee62-7f54-4c77-9d37-15708bc5cc23
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 719c58cb46c45da58af74ae82ee17f4e9df3b25f
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/08/2018
---
# <a name="publisher-information-subscription-watch-list-snapshot"></a>Сведения об издателе, список просмотра подписок (моментальный снимок)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Вкладка **Список наблюдения за подписками** доступна для распространителей под управлением [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и более поздних версий. Она предназначается для отображения сведений о подписках на все публикации, доступные на выбранном издателе. Список подписок можно фильтровать для просмотра ошибок, предупреждений и подписок с низкой производительностью. Эта вкладка предоставляет администратору единое расположение для контроля за активностью всех репликаций на издателе. Монитор репликации отображает все подписки, требующие внимания администратора, на основе выбранного типа репликации и в соответствии с параметром, выбранным в раскрывающемся списке **Показать** . Элементы отображаются на этой вкладке в соответствии с текущим состоянием и производительностью, поэтому подписки отображаются на этой странице только в случае, если они в настоящее время соответствуют параметру в списке **Показать** .  
  
## <a name="options"></a>Параметры  
 Для получения дополнительных сведений о подписке и о связанных с ней задачах щелкните правой кнопкой мыши на строке с этой подпиской, а затем выберите соответствующий параметр в контекстном меню. Чтобы изменить способ отображения данных в сетке, щелкните правой кнопкой мыши сетку, а затем один из следующих параметров.  
  
-   **Сортировать**: сортировка по одному или нескольким столбцам в диалоговом окне **Сортировка столбцов** .  
  
-   **Выберите столбцы для отображения**: выбор столбцов для отображения и порядка их отображения в диалоговом окне **Выбор столбцов** .  
  
-   **Фильтр**: фильтрация строк в сетке на основании значений столбцов в диалоговом окне **Параметры фильтра** .  
  
-   **Очистить фильтр**: удаление всех параметров фильтра для сетки.  
  
 Настройки фильтра уникальны для каждой сетки. Выбор и сортировка столбцов применяются ко всем сеткам одного типа, как, например, сетка публикаций для каждого издателя.  
  
 **Показать подписки на моментальные снимки**  
 Выберите типы подписок (на публикацию транзакций, на моментальные снимки или слиянием), которые будут выводиться для выбранного издателя.  
  
 **Показать**  
 Выберите состояния подписки, которые должны отображаться для выбранного типа подписки. Например, можно выбрать отображение только тех подписок, которые содержат ошибку.  
  
 **Состояние**  
 Состояние каждой подписки, определяемое состоянием агента моментальных снимков или агента распространителя (отображается состояние с более высоким приоритетом).  
  
 По умолчанию, в сетке, содержащей сведения о подписках, они сортируются по столбцу **Состояние** . В следующем списке показаны возможные значения состояния и порядок сортировки значений (например, ошибки всегда показываются в верхней части сетки).  
  
-   Ошибка  
  
-   Срок действия скоро истекает или истек  
  
-   Неинициализированная подписка  
  
-   Повтор последней невыполненной команды  
  
-   Синхронизация  
  
-   Нет синхронизации  
  
 Порядок сортировки также определяет отображаемое значение, если данная подписка имеет более одного состояния. Например, если подписка содержит ошибку и срок ее действия скоро истекает, в столбце **Состояние** отображается **Ошибка**.  
  
 Значения состояний **Срок действия скоро истекает или истек** и **Неинициализированная подписка** являются предупреждениями. Когда выводится предупреждение, столбец **Состояние** также отображается при запущенном агенте. Например, возможно состояние **Выполняется, срок действия скоро истекает или истек**.  
  
 Значение состояния **Срок действия скоро истекает или истек** отображается только при установленном пороге. Дополнительные сведения об установке пороговых значений см. в статье [Настройка пороговых значений и предупреждений в мониторе репликации](../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md).  
  
 **Подписка**  
 Имя каждой подписки в виде: *имя_подписчика: имя_базы_данных_подписки*.  
  
 **Публикация**  
 Имя публикации, с которой синхронизируется подписка, в виде *имя_базы_данных_публикации: имя_публикации*.  
  
 **Последняя синхронизация**  
 Время последнего запуска агента распространителя. Если в данный момент синхронизация выполняется, то выводится сообщение **Выполняется** .  
  
## <a name="see-also"></a>См. также:  
 [Запуск монитора репликации](../../relational-databases/replication/monitor/start-the-replication-monitor.md)   
 [Просмотр сведений и выполнение задач для издателя (монитор репликации)](../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-publisher-replication-monitor.md)   
 [Наблюдение за репликацией](../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  
