---
title: "Свойства куба - многомерной модели программирования | Документы Microsoft"
ms.custom: 
ms.date: 03/17/2017
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
- Collation property
- ID property
- ErrorConfiguration property
- cubes [Analysis Services], properties
- Description property
- DefaultMeasure property
- ProcessingMode property
- AggregationPrefix property
- EstimatedRows property
- Visible property
- StorageLocation property
- StorageMode property
- ScriptErrorHandlingMode property
- Source property
- ScriptCacheProcessingMode property
- Language property
- Name property
- properties [Analysis Services], cubes
- ProcessingPriority property
- ProactiveCaching property
ms.assetid: 72ca3387-620d-4473-8e23-7fe1f2b3d5bf
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 0d22d6fd46939b435cc0a8a6f25268aea0a192d6
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2018
---
# <a name="cube-properties---multidimensional-model-programming"></a>Свойства куба - многомерной модели программирования
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
Кубы имеют ряд свойств, изменение которых оказывает непосредственное влияние на их работу. Эти свойства перечислены в следующей таблице.  
  
> [!NOTE]  
>  Некоторые свойства устанавливаются автоматически при создании куба и не могут быть изменены.  
  
 Дополнительные сведения о задании свойств куба см. в разделе [конструктор кубов &#40; Analysis Services — многомерные данные &#41; ](http://msdn.microsoft.com/library/a6692467-da88-4312-8b03-d812f2ae5a96).  
  
|property|Описание|  
|--------------|-----------------|  
|**AggregationPrefix**|Общий префикс, используемый для имен агрегатов.|  
|**Параметры сортировки**|Код локали (LCID) и флаг сравнения, отделенный символом подчеркивания, например Latin1_General_C1_AS.|  
|**DefaultMeasure**|Содержит многомерное выражение, определяющее меру для куба по умолчанию.|  
|**Description**|Содержит описание куба, которое может отображаться в клиентских приложениях.|  
|**ErrorConfiguration**|Содержит настраиваемые параметры обработки ошибок, которые относятся к обработке ситуаций с повторяющимися и неизвестными ключами, действиями при обнаружении ошибок и их предельному числу, файлам журналов ошибок и обработки ключей NULL.|  
|**EstimatedRows**|Указывает предполагаемое количество строк в кубе.|  
|**Идентификатор**|Содержит уникальный идентификатор куба.|  
|**Язык**|Указывает идентификатор языка куба по умолчанию.|  
|**Название**|Указывает понятное имя куба.|  
|**ProactiveCaching**|Определяет настройки упреждающего кэша для куба.|  
|**ProcessingMode**|Показывает, следует ли производить индексирование и статистическую обработку во время обработки или после нее. Параметры **регулярного** или **отложенной**.|  
|**ProcessingPriority**|Определяет приоритет обработки куба во время фоновых операций, например отложенных статистических вычислений или индексирования. Значение по умолчанию — **0**.|  
|**ScriptCacheProcessingMode**|Определяет, когда должен создаваться кэш скрипта: во время обработки или после нее. Параметры **регулярного** и **отложенной**.|  
|**ScriptErrorHandlingMode**|Определяет обработку ошибок. Параметры **IgnoreNone** или **IgnoreAll**|  
|**Source**|Отображает представление источника данных, используемое для куба.|  
|**StorageLocation**|Указывает для куба место хранения в файловой системе. Если не задано иное, то место хранения наследуется из базы данных, содержащей объект куба.|  
|**StorageMode**|Указывает для куба режим хранения. Значения: **MOLAP**, **ROLAP**, или **HOLAP**.|  
|**Visible**|Определяет, отображается куб или скрыт.|  
  
> [!NOTE]  
>  Дополнительные сведения о настройке значений свойства ErrorConfiguration при работе со значениями null и других проблемах целостности данных см. в разделе [обработка проблем целостности данных в службах Analysis Services 2005](http://go.microsoft.com/fwlink/?LinkId=81891).  
  
## <a name="see-also"></a>См. также  
 [Упреждающее кэширование &#40; Секций &#41;](../../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md)  
  
  
