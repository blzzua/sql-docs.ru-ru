---
title: "Определение свойств измерения куба | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
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
- dimensions [Analysis Services], characteristics
- properties [Analysis Services], dimensions
ms.assetid: 9314e749-0918-4862-abaf-a21692188122
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 7f4f83f8225cc233b45bb3f4299a700992902995
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2018
---
# <a name="define-cube-dimension-properties"></a>Определение свойств измерения куба
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
Измерение куба представляет собой экземпляр измерения базы данных в пределах куба. Измерение базы данных может быть использовано в нескольких кубах, а измерения нескольких кубов могут быть основаны на одном измерении базы данных. В следующей таблице описаны свойства измерения куба.  
  
|Свойство|Описание|  
|--------------|-----------------|  
|**AllMemberAggregationUsage**|Управляет созданием статистических схем конструктором статистических схем в службах [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Это свойство может иметь следующие значения:<br /><br /> **Full**: каждый агрегат для куба должен включать элемент "Все".<br /><br /> **None**: ни один агрегат для куба не может включать элемент "Все". Это значение по умолчанию.<br /><br /> **Unrestricted**: на конструктор статистических схем не налагаются никакие ограничения.<br /><br /> **Default**: функциональное назначение такое же, как и у значения "Unrestricted".|  
|**Description**|Представляет описательное имя уровня.|  
|**DimensionID**|Содержит уникальный идентификатор (ID) измерения базы данных.|  
|**HierarchyUniqueNameStyle**|Определяет правила формирования уникальных имен для иерархий, содержащихся в измерении куба. Это свойство может иметь следующие значения:<br /><br /> **IncludeDimensionName**.<br />                    Имя измерения включается в качестве части имени иерархии. Это значение по умолчанию.<br /><br /> **ExcludeDimensionName**.<br />                    Имя измерения не включается в качестве части имени иерархии.|  
|**Идентификатор**|Содержит уникальный идентификатор измерения куба.|  
|**MemberUniqueNameStyle**|Определяет правила формирования уникальных имен для элементов иерархий, содержащихся в измерении куба. Это свойство может иметь следующие значения:<br /><br /> **Native**:<br />                      [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] автоматически определяют уникальные имена элементов. Это значение по умолчанию.<br /><br /> **NamePath**: службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] формируют составное имя, содержащее имя каждого уровня и заголовок элемента.|  
|**Название**|Содержит понятное имя измерения куба. По умолчанию имя измерения куба является таким же, как и имя измерения базы данных, если только уже не определено измерение куба с таким же именем.|  
|**Visible**|Определяет, является ли измерение куба видимым. Значение по умолчанию — **True**.|  
  
## <a name="see-also"></a>См. также  
 [Измерения &#40; Analysis Services — многомерные данные &#41;](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)  
  
  
