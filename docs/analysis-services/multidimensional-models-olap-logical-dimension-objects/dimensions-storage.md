---
title: "Аналитика хранилища | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- dimensions [Analysis Services], storage
- storing data [Analysis Services]
- storage [Analysis Services], dimensions
- relational OLAP
- multidimensional OLAP
- MOLAP
- storing data [Analysis Services], dimensions
- ROLAP
ms.assetid: 8d74b932-2174-4e1f-8414-636455880b6a
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: b70bdcc3883148035437a5097c170cb52536b8e8
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2018
---
# <a name="dimensions---storage"></a>Измерения — хранилище
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
Измерения в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] поддерживают два режима хранения:  
  
-   Реляционный OLAP (ROLAP)  
  
-   Многомерный OLAP (MOLAP)  
  
 Режим хранения определяет место и форму данных измерения. MOLAP — режим хранения измерений по умолчанию. **См. также:**[обработка и режимы хранения секции](../../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-partition-storage-modes-and-processing.md)  
  
## <a name="molap"></a>MOLAP  
 Данные для измерения в режиме MOLAP хранятся в многомерной структуре в экземпляре служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Эта многомерная структура создается и заполняется при обработке измерения. Измерения MOLAP обеспечивают более высокую производительность, чем измерения ROLAP.  
  
## <a name="rolap"></a>ROLAP  
 Данные для измерения, использующего режим ROLAP, фактически хранятся в таблицах, используемых для определения измерения. Режим хранения ROLAP можно использовать для крупных измерений без дублирования больших объемов данных, однако, это приведет к потере производительности запроса. Измерения основаны непосредственно на таблицах в представлении источника данных, используемого для определения измерения, поэтому режим хранения ROLAP также может поддерживать OLAP реального времени.  
  
> [!IMPORTANT]  
>  Если измерение использует режим хранения ROLAP и при этом входит в состав куба, использующего режим хранения MOLAP, все изменения схемы в исходной таблице должны сопровождаться немедленной обработкой куба. В противном случае может возникнуть несогласованность результатов при запросах к кубу. **См. также:**[автоматизации административных задач служб Analysis Services с помощью служб SSIS](../../analysis-services/instances/automate-analysis-services-administrative-tasks-with-ssis.md).  
  
## <a name="see-also"></a>См. также  
 [Обработка и режимы хранения секции](../../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-partition-storage-modes-and-processing.md)  
  
  
