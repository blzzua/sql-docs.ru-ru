---
title: Набор строк DMSCHEMA_MINING_MODELS | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DMSCHEMA_MINING_MODELS
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DMSCHEMA_MINING_MODELS rowset
ms.assetid: 1636f4cf-b342-4e2e-93b4-04136e2d41ef
caps.latest.revision: 41
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 838f17f1e9725738686635b3000f28929084c122
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="dmschemaminingmodels-rowset"></a>Набор строк DMSCHEMA_MINING_MODELS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Перечисляет модели интеллектуального анализа данных в текущем каталоге. **DMSCHEMA_MINING_MODELS** набор строк содержит сведения, такие как имена модели, дату обработки и алгоритм интеллектуального анализа данных, связанный с каждой моделью интеллектуального анализа данных.  
  
 , и делает это по-другому. **DMSCHEMA_MINING_MODELS** набора строк схемы очень похож на [DBSCHEMA_TABLES](../../../analysis-services/schema-rowsets/ole-db/dbschema-tables-rowset.md) набора строк схемы и может использоваться так же.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 **DMSCHEMA_MINING_MODELS** набор строк содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Description|  
|-----------------|--------------------|-----------------|  
|**MODEL_CATALOG**|**DBTYPE_WSTR**|Имя каталога. Заполняется именем базы данных, элементом которой является модель.|  
|**MODEL_SCHEMA**|**DBTYPE_WSTR**|Неполное имя схемы. Этот столбец не поддерживается [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; он всегда содержит **NULL**.|  
|**MODEL_NAME**|**DBTYPE_WSTR**|Имя модели интеллектуального анализа данных. Этот столбец содержит имя модели интеллектуального анализа данных и никогда не бывает пустым.|  
|**MODEL_TYPE**|**DBTYPE_WSTR**|Тип модели.|  
|**MODEL_GUID**|**DBTYPE_GUID**|Идентификатор GUID модели.|  
|**DESCRIPTION**|**DBTYPE_WSTR**|Понятное описание модели.|  
|**MODEL_PROPID**|**DBTYPE_UI4**|Идентификатор свойства модели. Этот столбец не поддерживается [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; он всегда содержит **NULL**.|  
|**DATE_CREATED**|**DBTYPE_DBTIMESTAMP**|Дата создания этой модели.|  
|**DATE_MODIFIED**|**DBTYPE_DBTIMESTAMP**|Дата последнего изменения определения этой модели.|  
|**SERVICE_TYPE_ID**|**DBTYPE_UI4**|Перечисление, определяющее тип алгоритма интеллектуального анализа данных, который используется моделью. Этот тип может иметь одно из следующих значений.<br /><br /> **DM_SERVICETYPE_CLASSIFICATION** (1)<br /><br /> **DM_SERVICETYPE_SEGMENTATION**(2)<br /><br /> **АССОЦИАЦИЯ DM_SERVICETYPE_**(4)<br /><br /> **DM_SERVICETYPE_ DENSITY_ESTIMATE**(8)<br /><br /> **DM_SERVICETYPE_SEQUENCE**(16)|  
|**ПАРАМЕТРЫ SERVICE_NAME**|**DBTYPE_WSTR**|Имя алгоритма интеллектуального анализа данных (для конкретного поставщика), который используется моделью.|  
|**CREATION_STATEMENT**|**DBTYPE_WSTR**|Инструкция, с помощью которой была создана модель интеллектуального анализа данных.|  
|**PREDICTION_ENTITY**|**DBTYPE_WSTR**|Список столбцов (с запятыми в качестве разделителей), для которых доступно прогнозирование.|  
|**IS_POPULATED**|**DBTYPE_BOOL**|Логический флаг. Показывает, заполняется ли модель.<br /><br /> **Значение TRUE,** Если модель является заполненных; в противном случае — **FALSE**.|  
|**MINING_PARAMETERS**|**DBTYPE_WSTR**|Список параметров с разделителями-запятыми, которые изначально использовались при создании модели.|  
|**MINING_STRUCTURE**|**DBTYPE_WSTR**|Идентификатор структуры интеллектуального анализа данных, на основе которой создана модель.|  
|**LAST_PROCESSED**|**DBTYPE_DBTIMESTAMP**|Дата и время последней обработки модели.|  
|**MSOLAP_IS_DRILLTHROUGH_ENABLED**|**DBTYPE_BOOL**|Логический флаг. Показывает, поддерживает ли модель детализацию.|  
|**ФИЛЬТР**|**DBTYPE_WSTR**|Критерий фильтра, связанный с моделью интеллектуального анализа данных.<br /><br /> Значение NULL или пустая строка означают, что фильтр не применяется.|  
|**TRAINING_SET_SIZE**|**DBTYPE_UIS**|Число вариантов в обучающем наборе модели интеллектуального анализа данных после обработки структуры и применения к модели фильтров.|  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 **DMSCHEMA_MINING_MODELS** строк может быть ограничен на столбцы в таблице ниже.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|**MODEL_CATALOG**|**DBTYPE_WSTR**|Необязательный параметр.|  
|**MODEL_SCHEMA**|**DBTYPE_WSTR**|Необязательный параметр.|  
|**MODEL_NAME**|**DBTYPE_WSTR**|Необязательный параметр.|  
|**MODEL_TYPE**|**DBTYPE_WSTR**|Необязательный параметр.|  
|**ПАРАМЕТРЫ SERVICE_NAME**|**DBTYPE_WSTR**|Необязательный параметр.|  
|**SERVICE_TYPE_ID**|**DBTYPE_UI4**|Необязательный параметр.|  
|**MINING_STRUCTURE**|**DBTYPE_WSTR**|Необязательный параметр.|  
  
 Примеры запросов этот набор строк. в разделе [запрос, параметры, используемые для создания модели интеллектуального анализа данных](../../../analysis-services/data-mining/query-the-parameters-used-to-create-a-mining-model.md).  
  
## <a name="see-also"></a>См. также:  
 [Наборы строк схемы интеллектуального анализа данных](../../../analysis-services/schema-rowsets/data-mining/data-mining-schema-rowsets.md)  
  
  
