---
title: "Свойства измерения базы данных | Документы Microsoft"
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
- metadata [Analysis Services]
- dimensions [Analysis Services], characteristics
- properties [Analysis Services], dimensions
ms.assetid: 075548ef-08a3-413c-8ee0-4a074c276fcc
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: d05ca23a224bd7c702bd54ef4355c568cf593327
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2018
---
# <a name="database-dimension-properties"></a>Свойства измерений базы данных
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
В [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], характеристики измерения задаются метаданные для измерения, основываясь на настройках различных свойств измерения и на нем атрибутах или иерархиях, содержащихся в измерении. Следующая таблица содержит описания свойств измерений служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
|property|Описание|  
|--------------|-----------------|  
|**AttributeAllMemberName**|Задает имя элемента «Все» для атрибутов измерения.|  
|**Параметры сортировки**|Задает параметры сортировки, применяемые в измерении.|  
|**CurrentStorageMode**|Содержит текущий режим хранения для измерения.|  
|**DependsOnDimension**|Содержит идентификатор другого измерения, от которого зависит данное (если такое имеется).|  
|**Description**|Содержит описание измерения.|  
|**ErrorConfiguration**|Настраиваемые параметры обработки ошибок для обработки ситуаций с повторяющимися ключами, неизвестными ключами, предельными значениями ошибок, действиями при обнаружении ошибки, файлом журнала ошибок и ключами со значением NULL.|  
|**Идентификатор**|Содержит уникальный идентификатор измерения.|  
|**Язык**|Задает язык по умолчанию для измерения.|  
|**MdxMissingMemberMode**|Определяет, как обрабатываются пропущенные элементы для инструкций многомерных выражений.|  
|**MiningModelID**|Содержит идентификатор модели интеллектуального анализа данных, с которой связано измерение интеллектуального анализа данных. Применяется, только если измерение является измерением модели интеллектуального анализа данных.|  
|**Название**|Указывает имя измерения.|  
|**ProactiveCaching**|Определяет настройки упреждающего кэширования для измерения.|  
|**ProcessingGroup**|Указывает группу обработки. Значения: ByAttribute и ByTable. Значение по умолчанию — **ByAttribute**.|  
|**ProcessingMode**|Показывает, следует ли службам [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] производить индексирование и статистическую обработку во время работы или после нее.|  
|**ProcessingPriority**|Определяет приоритет обработки для измерения во время работы в фоновом режиме, например отложенная статистическая обработка, индексирование или кластеризация.|  
|**Source**|Определяет представление источника данных, к которому привязано измерение.|  
|**StorageMode**|Определяет режим хранения измерения.|  
|**Тип**|Указывает тип измерения.|  
|**UnknownMember**|Показывает, видим ли неизвестный элемент.|  
|**UnknownMemberName**|Указывает заголовок (на языке по умолчанию для измерения) для неизвестного элемента измерения.|  
|**WriteEnabled**|Показывает, доступна ли обратная запись в измерение (зависит от прав доступа).|  
  
> [!NOTE]  
>  Дополнительные сведения о настройке значений свойства ErrorConfiguration и UnknownMember при работе со значениями null и других проблемах целостности данных см. в разделе [обработка проблем целостности данных в службах Analysis Services 2005](http://go.microsoft.com/fwlink/?LinkId=81891).  
  
## <a name="see-also"></a>См. также  
 [Атрибуты и иерархии атрибутов](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)   
 [Пользовательские иерархии](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md)   
 [Связей измерений](../../analysis-services/multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)   
 [Измерения &#40; Analysis Services — многомерные данные &#41;](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)  
  
  
