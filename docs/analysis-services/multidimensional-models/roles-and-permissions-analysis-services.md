---
title: "Роли и разрешения (службы Analysis Services) | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [Analysis Services], about security
- security [Analysis Services - multidimensional data], about security
ms.assetid: bb885447-868b-4686-853c-8241f63d4370
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 6d84e48d30af647f8a07e514492ce9d883f33249
ms.sourcegitcommit: d8ab09ad99e9ec30875076acee2ed303d61049b7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/23/2018
---
# <a name="roles-and-permissions-analysis-services"></a>Роли и разрешения (службы Analysis Services)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]предоставляет модель авторизации на основе ролей, предоставляющее доступ к операциям, объектов и данных. Все пользователи получают доступ к экземпляру служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] или базе данных в контексте некоторой роли.  
  
 В качестве системного администратора службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , вы отвечаете за предоставление членства **роли администратора сервера** , которая передает неограниченный доступ к операциям на сервере. Эта роль имеет фиксированные разрешения, и ее нельзя настраивать. По умолчанию члены локальной группы администраторов автоматически являются системными администраторами служб Analysis Services.  
  
 Пользователи без прав администратора, которые запрашивают или обрабатывают данные, получают доступ через **роли базы данных**. И системные администраторы и администраторы баз данных могут создавать роли, которые описывают разные уровни доступа в рамках заданной базы данных, а затем назначают членство каждому пользователю, которому необходим доступ. Каждая роль обладает настраиваемым набором разрешений для доступа к объектам и операциям в рамках отдельной базы данных. Разрешения назначаются на уровне базы данных, на уровне внутренних объектов (кубов и измерений, но не перспектив) и на уровне строк.  
  
 Распространенной практикой является разделение операций по созданию ролей и назначению членства. Часто разработчик моделей добавляет роли на этапе проектирования. Таким образом, все определения ролей отражаются в файлах проекта, определяющих модели. Членство в ролях обычно определяется позднее, когда база данных переносится в рабочую среду. Обычно членство назначают администраторы базы данных, которые создают скрипты для разработки, тестирования и выполнения в качестве независимой операции.  
  
 Вся авторизация выполняется по допустимому удостоверению пользователя Windows. Службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] используют для проверки подлинности удостоверений пользователей исключительно проверку подлинности Windows. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]предоставляет метод проверки подлинности. В разделе [методики проверки подлинности, поддерживаемые службами Analysis Services](../../analysis-services/instances/authentication-methodologies-supported-by-analysis-services.md).  
  
> [!IMPORTANT]  
>  Разрешения являются аддитивными для каждого пользователя или группы Windows, по всем ролям базы данных. Если одна роль запрещает пользователю или группе выполнять определенные задачи или просматривать определенные данные, а другая роль предоставляет такое разрешение указанному пользователю или группе, то этому пользователю или группе будет разрешено выполнять упомянутые задачи или просматривать упомянутые данные.  
  
## <a name="in-this-section"></a>В этом разделе  
  
-   [Авторизацию доступа к объектам и операции &#40; Службы Analysis Services &#41;](../../analysis-services/multidimensional-models/authorizing-access-to-objects-and-operations-analysis-services.md)  
  
-   [Предоставление разрешений базы данных &#40; Службы Analysis Services &#41;](../../analysis-services/multidimensional-models/grant-database-permissions-analysis-services.md)  
  
-   [Предоставьте куба или модели разрешения &#40; Службы Analysis Services &#41;](../../analysis-services/multidimensional-models/grant-cube-or-model-permissions-analysis-services.md)  
  
-   [Предоставление разрешений доступа &#40; Службы Analysis Services &#41;](../../analysis-services/multidimensional-models/grant-process-permissions-analysis-services.md)  
  
-   [Предоставление разрешений на чтение описания метаданным объекта &#40; Службы Analysis Services &#41;](../../analysis-services/multidimensional-models/grant-read-definition-permissions-on-object-metadata-analysis-services.md)  
  
-   [Предоставление разрешений на объект источника данных &#40; Службы Analysis Services &#41;](../../analysis-services/multidimensional-models/grant-permissions-on-a-data-source-object-analysis-services.md)  
  
-   [Предоставление разрешений на &#40; структур интеллектуального анализа данных и моделей Службы Analysis Services &#41;](../../analysis-services/multidimensional-models/grant-permissions-on-data-mining-structures-and-models-analysis-services.md)  
  
-   [Предоставьте разрешения на измерение &#40; Службы Analysis Services &#41;](../../analysis-services/multidimensional-models/grant-permissions-on-a-dimension-analysis-services.md)  
  
-   [Предоставление настраиваемого доступа к измерению данных &#40; Службы Analysis Services &#41;](../../analysis-services/multidimensional-models/grant-custom-access-to-dimension-data-analysis-services.md)  
  
-   [Предоставление настраиваемого доступа к ячейке данных &#40; Службы Analysis Services &#41;](../../analysis-services/multidimensional-models/grant-custom-access-to-cell-data-analysis-services.md)  
  
## <a name="see-also"></a>См. также  
 [Создание ролей и управление ими](../../analysis-services/tabular-models/create-and-manage-roles-ssas-tabular.md)  
  
  
