---
title: "Откат журнала изменений элемента (службы Master Data Services) | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: non-specific
ms.reviewer: 
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d39d3474-20e7-429f-9c8d-fcc4eb0854fc
caps.latest.revision: 
author: leolimsft
ms.author: lle
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7b9688b459697778774ec34dba289f2bb1e82145
ms.sourcegitcommit: 6ac1956307d8255dc544e1063922493b30907b80
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2018
---
# <a name="rollback-member-revision-history-master-data-services"></a>Откат журнала изменений элемента (Master Data Services)
  Запись в журнал изменений элемента осуществляется каждый раз при изменении элемента. Существует возможность откатить журнал изменений элемента к предыдущей версии.  
  
## <a name="prerequisites"></a>предварительные требования  
  
-   Необходимо иметь разрешение на обновление хотя бы одного из атрибутов выбранного элемента. При откате журнала изменений все значения атрибутов, которые могут быть обновлены, откатываются к значениям предыдущей версии.  
  
-   Журнал изменений доступен, только если типом журнала транзакций сущности является элемент.  
  
 **Откат журнала изменений элемента**  
  
1.  В диспетчере основных данных откройте обозреватель.  
  
2.  Выберите сущность и элемент для отката.  
  
3.  Щелкните **Просмотр журнала**.  
  
4.  Выберите версию для отката и нажмите **Откат**.  
  
## <a name="see-also"></a>См. также:  
 [Журнал изменений элемента (Master Data Services)](../master-data-services/member-revision-history-master-data-services.md)   
 [Изменение типа журнала транзакций сущности (службы Master Data Services)](../master-data-services/change-the-entity-transaction-log-type-master-data-services.md)  
  
  
