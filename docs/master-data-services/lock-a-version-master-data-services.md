---
title: "Блокировка версии (службы Master Data Services) | Документы Майкрософт"
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
helpviewer_keywords:
- versions [Master Data Services], locking
- locking versions [Master Data Services]
ms.assetid: 7bb62a84-12d8-4b29-9b6e-6aa25410618e
caps.latest.revision: 
author: leolimsft
ms.author: lle
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a83d9b583a00132f3dea36dc0791296a2105aeae
ms.sourcegitcommit: 6ac1956307d8255dc544e1063922493b30907b80
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2018
---
# <a name="lock-a-version-master-data-services"></a>Блокировка версии (службы Master Data Services)
  В среде [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]блокировка версии модели препятствует изменениям элементов модели и их атрибутов.  
  
> [!NOTE]  
>  Если версия заблокирована, суперпользователи и администраторы модели по-прежнему могут добавлять, изменять и удалять элементы. Другие пользователи с разрешениями для модели могут только просматривать элементы.  
  
## <a name="prerequisites"></a>предварительные требования  
 Для выполнения этой процедуры:  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](../master-data-services/administrators-master-data-services.md).  
  
-   Версия должна быть в состоянии **Открыта**.  
  
-   Необходимо иметь разрешение на доступ к функциональной области "Управление версиями". Дополнительные сведения см. в разделе [Разрешения функциональной области (службы Master Data Services)](../master-data-services/functional-area-permissions-master-data-services.md).  
  
### <a name="to-lock-a-version"></a>Блокировка версии  
  
1.  В среде [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Управление версиями**.  
  
2.  На странице **Управление версиями** выберите строки для версии, которую необходимо заблокировать.  
  
3.  Нажмите кнопку **Заблокировать**.  
  
4.  В диалоговом окне подтверждения нажмите кнопку **ОК**.  
  
## <a name="next-steps"></a>Next Steps  
  
-   [Подтверждение исправления проблемы, обнаруженной при проверке на соответствие бизнес-правилам (службы Master Data Services)](../master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
-   [Фиксация версии (службы Master Data Services)](../master-data-services/commit-a-version-master-data-services.md)  
  
## <a name="see-also"></a>См. также:  
 [Версии (службы Master Data Services)](../master-data-services/versions-master-data-services.md)   
 [Разблокировка версии (службы Master Data Services)](../master-data-services/unlock-a-version-master-data-services.md)  
  
  
