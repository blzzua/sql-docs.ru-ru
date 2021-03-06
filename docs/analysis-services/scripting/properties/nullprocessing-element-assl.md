---
title: Элемент NullProcessing (ASSL) | Документы Microsoft
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.custom: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- NullProcessing Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- NullProcessing
helpviewer_keywords:
- NullProcessing element
ms.assetid: 697be5c6-e9a6-4f74-9ff4-5f31400c2178
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: bd814424d42062652d85f780d03a8ac5b818c1b0
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="nullprocessing-element-assl"></a>NullProcessing Element (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Определяет как пустые значения обрабатываются.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<DataItem>  
   ...  
   <NullProcessing>...</NullProcessing>  
   ...  
</DataItem>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Description|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*Автоматически*|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Remarks  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|*Сохранить*|Сохраняет значение NULL.<br /><br /> Примечание: Это значение не поддерживается для мер числа различных объектов.|  
|*Ошибка*|Вызывает ошибку ключа NULL. Значение [NullKeyNotAllowed](../../../analysis-services/scripting/properties/nullkeynotallowed-element-assl.md) определяет реакцию экземпляра на эту ошибку.<br /><br /> Примечание: Это значение не поддерживается для мер.|  
|*UnknownMember*|Создает неизвестный элемент и вызывает ошибку преобразования ключа NULL. Значение [NullKeyConvertedToUnknown](../../../analysis-services/scripting/properties/nullkeyconvertedtounknown-element-assl.md) определяет реакцию экземпляра на эту ошибку.<br /><br /> Примечание: Это значение не поддерживается для столбцов, связанных с мерами.|  
|*ZeroOrBlank*|Преобразует значение NULL в ноль (для элементов числовых данных) или пустую строку (для элементов строковых данных).<br /><br /> Примечание: Это значение обеспечивает совместимость с предыдущими версиями [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|*Автоматически*|Использует обработку по умолчанию, определенную для элемента:<br /><br /> *ZeroOrBlank* для элементов данных OLAP.<br /><br /> *UnknownMember* для элементов данных интеллектуального анализа данных.|  
  
 Перечисление, соответствующее разрешенным значениям для **NullProcessing** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.NullProcessing>.  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
