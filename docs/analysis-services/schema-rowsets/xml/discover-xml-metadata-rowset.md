---
title: Набор строк DISCOVER_XML_METADATA | Документы Microsoft
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
- DISCOVER_XML_METADATA
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DISCOVER_XML_METADATA rowset
ms.assetid: 0befd026-db1b-43ac-b0e6-734abb56a4b1
caps.latest.revision: 40
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 64fe5c240808b727c0985f432bb634d83cb68e91
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="discoverxmlmetadata-rowset"></a>Набор строк DISCOVER_XML_METADATA
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Возвращает XML-документ, описывающий запрошенный объект. Возвращаемый набор строк всегда состоит из одной строки и одного столбца.  
  
 При вызове метода [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) метод с **DISCOVER_XML_METATDATA** значения перечисления в [RequestType](../../../analysis-services/xmla/xml-elements-properties/requesttype-element-xmla.md) элемент, **Discover**возвращает **DISCOVER_XML_METATDATA** набора строк.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 Набор строк **DISCOVER_XML_METADATA** содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Description|  
|-----------------|--------------------|------------|-----------------|  
|**МЕТАДАННЫЕ**|**DBTYPE_WSTR**||XML-документ, который описывает объект, требуемый в соответствии с ограничением.|  
  
 Этот набор строк схемы не отсортирован.  
  
> [!IMPORTANT]  
>  Набор строк **DISCOVER_XML_METADATA** нельзя запрашивать с помощью синтаксиса команды SELECT. Тем не менее **DISCOVER_XML_METADATA** набора строк можно запрашивать с помощью <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.GetSchemaDataSet%2A>.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк **DISCOVER_XML_METADATA** может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|**DatabaseID**|**DBTYPE_WSTR**|Необязательный параметр.|  
|**DimensionID**|**DBTYPE_WSTR**|Необязательный параметр.|  
|**CubeID**|**DBTYPE_WSTR**|Необязательный параметр.|  
|**MeasureGroupID**|**DBTYPE_WSTR**|Необязательный параметр.|  
|**PartitionID**|**DBTYPE_WSTR**|Необязательный параметр.|  
|**PerspectiveID**|**DBTYPE_WSTR**|Необязательный параметр.|  
|**DimensionPermissionID**|**DBTYPE_WSTR**|Необязательный параметр.|  
|**RoleID**|**DBTYPE_WSTR**|Необязательный параметр.|  
|**DatabasePermissionID**|**DBTYPE_WSTR**|Необязательный параметр.|  
|**MiningModelID**|**DBTYPE_WSTR**|Необязательный параметр.|  
|**MiningModelPermissionID**|**DBTYPE_WSTR**|Необязательный параметр.|  
|**DataSourceID**|**DBTYPE_WSTR**|Необязательный параметр.|  
|**MiningStructureID**|**DBTYPE_WSTR**|Необязательный параметр.|  
|**AggregationDesignID**|**DBTYPE_WSTR**|Необязательный параметр.|  
|**Числовое обозначение TraceID**|**DBTYPE_WSTR**|Необязательный параметр.|  
|**MiningStructurePermissionID**|**DBTYPE_WSTR**|Необязательный параметр.|  
|**CubePermissionID**|**DBTYPE_WSTR**|Необязательный параметр.|  
|**Идентификатор сборки**|**DBTYPE_WSTR**|Необязательный параметр.|  
|**MdxScriptID**|**DBTYPE_WSTR**|Необязательный параметр.|  
|**DataSourceViewID**|**DBTYPE_WSTR**|Необязательный параметр.|  
|**DataSourcePermissionID**|**DBTYPE_WSTR**|Необязательный параметр.|  
|**ObjectExpansion**|**DBTYPE_WSTR**|Необязательный параметр.|  
  
 Ограничения, **ObjectExpansion**, доступных для каждого основного объекта служб [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. В клиенте ограничения обычно используются для описания объектов OLAP, для которых должен быть возвращен код на языке DDL, а ограничение **ObjectExpansion** служит для определения степени развертывания в возвращаемом коде на языке DDL. Следующая таблица указывает, может ли значение перечисления для [Alter элемент &#40; XML для Аналитики &#41; ](../../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md) команд.  
  
|Значение перечисления|Description|  
|-----------------------|-----------------|  
|**ReferenceOnly**|Возвращает только имя/идентификатор/отметку времени/состояние, требуемое для запрашиваемых объектов, а также, рекурсивно, все основные объекты-потомки.|  
|**ObjectProperties**|Развертывает запрашиваемый объект без ссылок на содержащиеся объекты (включает развернутые более мелкие содержащиеся объекты).|  
|**ExpandObject**|Аналогичен параметру *ObjectProperties*, но также возвращает имя, идентификатор и отметку времени для вложенных основных объектов.|  
|**ExpandFull**|Полностью развертывает запрашиваемый объект рекурсивно до конца каждого содержащегося объекта.|  
  
## <a name="see-also"></a>См. также:  
 [Наборы строк схемы XML для аналитики](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
