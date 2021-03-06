---
title: Тип данных CubeAttribute (ASSL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- CubeAttribute Data Type
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- CubeAttribute
helpviewer_keywords:
- CubeAttribute data type
ms.assetid: 114ffb44-460b-4971-b31b-dd844e960b81
caps.latest.revision: 45
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 84899c5d82286fbcc49404f854ff38c0243a655e
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="cubeattribute-data-type-assl"></a>Тип данных CubeAttribute (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Определяет тип-примитив, представляющий атрибут, связанный с [куба](../../../analysis-services/scripting/objects/cube-element-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<CubeAttribute>  
   <AttributeID>...</AttributeID>  
   <AggregationUsage>...</AggregationUsage>  
   <AttributeHierarchyOptimizedState>...</AttributeHierarchyOptimizedState>  
   <AttributeHierarchyEnabled>...</AttributeHierarchyEnabled>  
   <AttributeHierarchyVisible>...</AttributeHierarchyVisible>  
   <Annotations>...</Annotations>  
</CubeAttribute>  
```  
  
## <a name="data-type-characteristics"></a>Характеристики типа данных  
  
|Характеристика|Description|  
|--------------------|-----------------|  
|Базовые типы данных|None|  
|Производные типы данных|None|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|[AggregationUsage](../../../analysis-services/scripting/properties/aggregationusage-element-assl.md), [заметки](../../../analysis-services/scripting/collections/annotations-element-assl.md), [AttributeHierarchyEnabled](../../../analysis-services/scripting/properties/attributehierarchyenabled-element-assl.md), [AttributeHierarchyOptimizedState](../../../analysis-services/scripting/properties/attributehierarchyoptimizedstate-element-assl.md), [ AttributeHierarchyVisible](../../../analysis-services/scripting/properties/attributehierarchyvisible-element-assl.md), [AttributeID](../../../analysis-services/scripting/properties/attributeid-element-assl.md)|  
|Производные элементы|[Атрибут](../../../analysis-services/scripting/objects/attribute-element-assl.md) ([атрибуты](../../../analysis-services/scripting/collections/attributes-element-assl.md) коллекцию [CubeDimension](../../../analysis-services/scripting/data-type/cubedimension-data-type-assl.md))|  
  
## <a name="remarks"></a>Remarks  
 *AttributeHierarchyOptimizedState* элемент не поддерживается при запуске службы со значениями свойства конфигурации DeploymentMode 1 или 2 (режим SharePoint или табличный, используемые для запуска [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] и табличной модели базы данных).  
  
 Нельзя добавить атрибут как уровень иерархии, если свойство *AtttributeHierarchyEnabled*имеет значение FALSE и экземпляр работает в режиме DeploymentMode 1 или 2 (режим сервера SharePoint или табличный).  
  
 Атрибуты в [CubeDimension](../../../analysis-services/scripting/data-type/cubedimension-data-type-assl.md) элемент, который не включен явно в [атрибуты](../../../analysis-services/scripting/collections/attributes-element-assl.md) становятся частью коллекции со значениями по умолчанию, назначенные им. После добавления в коллекцию, эти атрибуты могут возвращаться [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) метод.  
  
 [AggregationUsage](../../../analysis-services/scripting/properties/aggregationusage-element-assl.md) элемент управления как [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] автоматически статистических схем для атрибута. Элемент **AggregationUsage** не ограничивает любые статистические обработки, созданные для куба вручную.  
  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.CubeAttribute>.  
  
## <a name="see-also"></a>См. также:  
 [Службы Analysis Services сценариев типы данных XML в &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
