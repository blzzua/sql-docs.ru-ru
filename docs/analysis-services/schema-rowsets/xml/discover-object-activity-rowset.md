---
title: Набор строк DISCOVER_OBJECT_ACTIVITY | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DISCOVER_OBJECT_ACTIVITY rowset
ms.assetid: 100f7de1-ad5c-4973-b863-3c10df1245c4
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 573b41cb848ee7a8e93bfdc4625b8a05857f2d61
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="discoverobjectactivity-rowset"></a>Набор строк DISCOVER_OBJECT_ACTIVITY
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Предоставляет сведения об использовании ресурсов, на объект с момента запуска службы.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 Набор строк **DISCOVER_OBJECT_ACTIVITY** содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Description|  
|-----------------|--------------------|------------|-----------------|  
|**OBJECT_AGGREGATION_HIT**|**DBTYPE_I8**||Количество случаев обнаружения в кэше результатов статистической обработки объекта с начала работы службы.|  
|**OBJECT_AGGREGATION_MISS**|**DBTYPE_I8**||Количество случаев, в которых не произошло обращение в кэш за существующими результатами статистической обработки объекта (т.е. в которых эти результаты не были использованы) с начала работы службы.|  
|**OBJECT_CPU_TIME_MS**|**DBTYPE_I8**||Время ЦП в миллисекундах, израсходованное объектом с начала работы службы.|  
|**OBJECT_DATA_VERSION**|**DBTYPE_I4**||Номер в журнале обращений и преобразований для данных этого объекта; этот номер возрастает после каждой обработки объекта.|  
|**OBJECT_HIT**|**DBTYPE_I8**||Количество случаев обнаружения объекта в кэше с начала работы службы.|  
|**OBJECT_ID**|**DBTYPE_WSTR**||Идентификатор объекта, определенный во время создания|  
|**OBJECT_MISS**|**DBTYPE_I8**||Количество случаев, в которых объект не был обнаружен в кэше с начала работы службы.|  
|**OBJECT_PARENT_PATH**|**DBTYPE_WSTR**||Путь к родительскому объекту текущего объекта.|  
|**OBJECT_READ_KB**|**DBTYPE_I8**||Накопленные данные о количестве данных в килобайтах, считанных объектом с начала работы службы.|  
|**OBJECT_READS**|**DBTYPE_I8**||Накопленные данные о количестве операций чтения, выполненных объектом с начала работы службы.|  
|**OBJECT_ROWS_RETURNED**|**DBTYPE_I8**||Количество строк, возвращенных объектом вызывающему объекту с начала работы службы.|  
|**OBJECT_ROWS_SCANNED**|**DBTYPE_I8**||Количество строк, просмотренных объектом с начала работы службы.|  
|**OBJECT_VERSION**|**DBTYPE_I4**||Номер версии метаданных для объекта. Этот номер изменяется при каждом изменении объекта.|  
|**OBJECT_WRITE_KB**|**DBTYPE_I8**||Накопленные данные о количестве данных в килобайтах, записанных объектом с начала работы службы.|  
|**OBJECT_WRITES**|**DBTYPE_I8**||Накопленные данные о количестве операций записи, выполненных объектом с начала работы службы.|  
  
 Этот набор строк схемы не отсортирован.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк **DISCOVER_OBJECT_ACTIVTY** может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|OBJECT_PARENT_PATH|DBTYPE_WSTR|Необязательный параметр.|  
|OBJECT_ID|DBTYPE_WSTR|Необязательный параметр.|  
  
## <a name="see-also"></a>См. также:  
 [Наборы строк схемы XML для аналитики](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
