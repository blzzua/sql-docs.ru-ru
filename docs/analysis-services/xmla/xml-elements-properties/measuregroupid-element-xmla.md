---
title: Элемент MeasureGroupID (XML для Аналитики) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- MeasureGroupID Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#MeasureGroupID
- http://schemas.microsoft.com/analysisservices/2003/engine#MeasureGroupID
- microsoft.xml.analysis.measuregroupid
helpviewer_keywords:
- MeasureGroupID element
ms.assetid: ff55777e-54ea-42b9-a084-2e12e0a10988
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 765d4de799e1f54f8202351b010a891c3f88f961
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="measuregroupid-element-xmla"></a>Элемент MeasureGroupID (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]Идентифицирует группу мер внутри родительского элемента, который содержит ссылку на объект.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Object> <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <MeasureGroupID>...</MeasureGroupID>  
   ...  
</Object>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Description|  
|--------------------|-----------------|  
|Тип данных и длина|String|  
|Значение по умолчанию|None|  
|Количество элементов|См. в следующей таблице.|  
  
|Предок или родитель|Количество элементов|  
|------------------------|-----------------|  
|[Source](../../../analysis-services/xmla/xml-elements-properties/source-element-xmla.md), [Target](../../../analysis-services/xmla/xml-elements-properties/target-element-xmla.md)|1-1: обязательный элемент, который встречается ровно один раз.|  
|Все остальные|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Object](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md), [ParentObject](../../../analysis-services/xmla/xml-elements-properties/parentobject-element-xmla.md), [Source](../../../analysis-services/xmla/xml-elements-properties/source-element-xmla.md), [Target](../../../analysis-services/xmla/xml-elements-properties/target-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
