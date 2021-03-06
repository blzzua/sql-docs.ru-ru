---
title: "Применение и обновление набора изменений (Master Data Services) | Документы Майкрософт"
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
ms.assetid: 3a6a3cf2-1e77-43d3-a64a-855ae51258e7
caps.latest.revision: 
author: leolimsft
ms.author: lle
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3e6f059a5ac85fce47256ae2b75f170017186e14
ms.sourcegitcommit: 6ac1956307d8255dc544e1063922493b30907b80
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2018
---
# <a name="apply-and-update-a-changeset-master-data-services"></a>Применение и обновление набора изменений (Master Data Services)
  Набор изменений — это совокупность ожидающих изменений основных данных. Набор изменений можно применить локально, чтобы просмотреть, добавить, обновить и удалить ожидающие изменения в этом наборе.  
  
## <a name="prerequisites"></a>предварительные требования  
  
-   Необходимо иметь разрешение на доступ к функциональной области **Обозреватель** . Дополнительные сведения см. в разделе [Разрешения функциональной области (службы Master Data Services)](../master-data-services/functional-area-permissions-master-data-services.md).  
  
-   Необходимо иметь по крайней мере доступ на обновление сущности или одного из ее атрибутов.  
  
-   Можно просмотреть только набор изменений, которым вы владеете или который отправлен вам на утверждение, если вы являетесь администратором сущности.  
  
-   Вы можете изменить только набор изменений, владельцем которого вы являетесь, и если он находится в открытом или отклоненном состоянии.  
  
## <a name="to-apply-and-update-a-changeset"></a>Применение и обновление набора изменений  
  
1.  На домашней странице [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] выберите модель и версию, а затем щелкните **Обозреватель**.  
  
2.  Щелкните сущность в меню **Сущности** .  
  
3.  В области справа выберите **Наборы изменений** и дважды щелкните набор изменений, который хотите просмотреть и изменить.  
  
4.  Нажмите кнопку **Применить**.  
  
     Ожидающие изменения применяются к элементу сущности в сетке. Ожидающие изменения выделены.  
  
     Создание, удаление и обновление элементов приводит к изменениям в наборе изменений.  
  
5.  Чтобы обратить ожидающие изменения, в области **Наборы изменений** щелкните правой кнопкой мыши в сетке и выберите пункт **Обратить**.  
  
## <a name="next-steps"></a>Next Steps  
 [Фиксация или отправка набора изменений (Master Data Services)](../master-data-services/commit-or-submit-a-changeset-master-data-services.md)  
  
## <a name="see-also"></a>См. также:  
 [Создание набора изменений (Master Data Services)](../master-data-services/create-a-changeset-master-data-services.md)   
 [Утверждение или отклонение набора изменений (Master Data Services)](../master-data-services/approve-or-reject-a-changeset-master-data-services.md)  
  
  
