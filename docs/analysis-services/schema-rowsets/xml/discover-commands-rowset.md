---
title: Набор строк DISCOVER_COMMANDS | Документы Microsoft
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
- DISCOVER_COMMANDS rowset
ms.assetid: d228f265-05d9-4d2c-a622-44c73eab7a71
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: f5fac5cdcfc9dd7f7be511a20018f9c6732ce028
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="discovercommands-rowset"></a>Набор строк DISCOVER_COMMANDS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Предоставляет ресурс действия сведения об использовании и в настоящее время выполнения или последних выполненных команд в соединениях, открытых на сервере.  
  
 **Область применения:** табличные модели, многомерные модели  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 Набор строк **DISCOVER_COMMANDS** содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Ограничение|Description|  
|-----------------|--------------------|-----------------|-----------------|  
|**SESSION_SPID**|**DBTYPE_I4**|Да|Идентификатор сеанса.|  
|**SESSION_COMMAND_COUNT**|**DBTYPE_I4**||Количество команд, выполненных с начала сеанса.|  
|**COMMAND_START_TIME**|**DBTYPE_DBTIMESTAMP**||Дата и время последнего запуска команды, выраженные как время в формате UTC на сервере.|  
|**COMMAND_ELAPSED_TIME_MS**|**DBTYPE_I8**||Общее затраченное время в миллисекундах после начала выполнения команды.|  
|**COMMAND_CPU_TIME_MS**|**DBTYPE_I8**||Время ЦП в миллисекундах, израсходованное командой после начала выполнения команды.|  
|**COMMAND_READS**|**DBTYPE_I8**||Накопленные данные о количестве операций чтения с диска после начала выполнения команды.|  
|**COMMAND_READ_KB**|**DBTYPE_I8**||Накопленные данные о количестве данных в килобайтах, считанных с диска после начала выполнения команды.|  
|**COMMAND_WRITES**|**DBTYPE_I8**||Накопленные данные о количестве операций записей на диск после начала выполнения команды.|  
|**COMMAND_WRITE_KB**|**DBTYPE_I8**||Накопленные данные о количестве данных в килобайтах, записанных на диск после начала выполнения команды.|  
|**COMMAND_TEXT**|**DBTYPE_WSTR**||Текст команды.|  
|**COMMAND_END_TIME**|**DBTYPE_DBTIMESTAMP**||Дата и время сервера в формате UTC на момент завершения выполнения команды.|  
  
 Этот набор строк схемы не отсортирован.  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Использование ADOMD.NET для возврата набора строк  
 Если для получения метаданных используется ADOMD.NET и набор строк схемы, то для ссылки на объект набора строк схемы в методе GetSchemaDataSet вы можете использовать идентификатор GUID или строку. Дополнительные сведения см. в статье [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md).  
  
 В следующей таблице указываются значения строки и идентификатора GUID, определяющие этот набор строк.  
  
|Аргумент|Значение|  
|--------------|-----------|  
|GUID|a07ccd34-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|Команды|  
  
## <a name="see-also"></a>См. также:  
 [Наборы строк схемы XML для аналитики](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
