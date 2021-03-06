---
title: "Набор строк DISCOVER_LOCATIONS | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
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
ms.assetid: 6d3a1171-8e4d-4022-ade0-b785cf795d70
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 61f69caeab165c4d6822f8f25667ad544d6014ec
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2018
---
# <a name="discoverlocations-rowset"></a>Набор строк DISCOVER_LOCATIONS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
Возвращает сведения о содержимом файла резервной копии. Необходимо иметь разрешение на доступ к папке с резервными файлами.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 Набор строк **DISCOVER_LOCATIONS** содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Ограничение|Описание|  
|-----------------|--------------------|-----------------|-----------------|  
|**LOCATION_BACKUP_FILE_PATHNAME**|**DBTYPE_WSTR**|Обязательно, см. ниже.|Расположение файла резервной копии.|  
|**LOCATION_PARTITION_OBJECTPATH**|**DBTYPE_WSTR**||Путь к секции относительно папки данных.|  
|**LOCATION_PARTITION_DATASOURCEID**|**DBTYPE_WSTR**||Идентификатор источника данных, используемый для обработки секции.|  
|**LOCATION_PARTITION_DATASOURCENAME**|**DBTYPE_WSTR**||Имя источника данных, используемого для обработки.|  
|**LOCATION_PARTITION_NAME**|**DBTYPE_WSTR**||Имя секции.|  
|**LOCATION_PARTITION_SIZE**|**DBTYPE_WSTR**||Приблизительный размер секции.|  
|**LOCATION_CONNECTION_STRING**|**DBTYPE_WSTR**||Строка подключения для источника данных, используемого в обработке.|  
|**LOCATION_PARTITION_FOLDER**|**DBTYPE_WSTR**||Исходное расположение этой секции при создании файла резервной копии.|  
  
 Этот набор строк схемы не отсортирован.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк **DISCOVER_LOCATIONS** может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|**LOCATION_BACKUP_FILE_PATHNAME**|**DBTYPE_WSTR**|Обязательно|  
|**LOCATION_PASSWORD PF_DBTYPE**|**DBTYPE_WSTR**|Требуется, если был указан во время резервного копирования. Это ограничение не используется для ограничения возвращаемых строк. Оно используется для задания пароля для доступа к папке.|  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Использование ADOMD.NET для возврата набора строк  
 Если для получения метаданных используется ADOMD.NET и набор строк схемы, то для ссылки на объект набора строк схемы в методе GetSchemaDataSet вы можете использовать идентификатор GUID или строку. Дополнительные сведения см. в статье [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md).  
  
 В следующей таблице указываются значения строки и идентификатора GUID, определяющие этот набор строк.  
  
|Аргумент|Значение|  
|--------------|-----------|  
|GUID|a07ccd92-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|Расположения|  
  
## <a name="see-also"></a>См. также  
 [XML для аналитики наборы строк схемы](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
