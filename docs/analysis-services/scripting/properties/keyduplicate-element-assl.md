---
title: Элемент KeyDuplicate (ASSL) | Документы Microsoft
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
- KeyDuplicate Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- KeyDuplicate
helpviewer_keywords:
- KeyDuplicate element
ms.assetid: d7000b8b-e81f-4401-8738-00c2e0f73a59
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 97c4d349cecfc9fb1dd51c1c018110068b5be7dc
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="keyduplicate-element-assl"></a>Элемент KeyDuplicate (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Определяет, каким образом [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ошибок повторения ключей при их обнаружении во время обработки.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<ErrorConfiguration>  
   ...  
      <KeyDuplicate>...</KeyDuplicate>  
   ...  
</ErrorConfiguration>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Description|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*Пропустить ошибку*|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[ErrorConfiguration](../../../analysis-services/scripting/objects/errorconfiguration-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Remarks  
 Ошибки с повторяющимися значениями ключа возникают только во время обработки измерения, когда ключ атрибута появляется больше одного раза. Поскольку ключи атрибутов должны быть уникальны, службы [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] удаляют повторяющиеся записи. Ошибки с повторяющимися значениями ключа обычно свидетельствуют о дефектах модели измерения, в частности в связях между ее атрибутами.  
  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|*Пропустить ошибку*|При обработке эту ошибку следует пропускать и продолжать выполнение.|  
|*Сообщить и продолжить*|При обработке следует создать отчет об этой ошибке и продолжать выполнение.|  
|*Сообщить и остановить выполнение*|При обработке следует создать отчет об этой ошибке и прервать выполнение.|  
  
 Перечисление, соответствующее разрешенным значениям для **KeyDuplicate** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.ErrorOption>.  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
