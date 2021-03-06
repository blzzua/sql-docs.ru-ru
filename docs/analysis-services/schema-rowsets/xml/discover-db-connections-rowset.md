---
title: Набор строк DISCOVER_DB_CONNECTIONS | Документы Microsoft
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
- DISCOVER_DB_CONNECTIONS rowset
ms.assetid: 12a51a4e-5f3d-4449-9d94-7836fea1bc8b
caps.latest.revision: 17
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 8a932cfa872e0cceed0b132f486349716ba4210b
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="discoverdbconnections-rowset"></a>Набор строк DISCOVER_DB_CONNECTIONS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Предоставляет ресурс действия сведения об использовании и открытым в данный момент соединения с сервера в базе данных.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 Набор строк **DISCOVER_DB_CONNECTIONS** содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Description|  
|-----------------|--------------------|------------|-----------------|  
|**CONNECTION_CATALOG_NAME**|**DBTYPE_WSTR**||Имя базы данных, с которой установлено текущее соединение.|  
|**CONNECTION_ID**|**DBTYPE_I4**||Уникальное число, определяющее соединение.|  
|**CONNECTION_IDLE_TIME_MS**|**DBTYPE_I8**||Время простоя (в миллисекундах) с момента открытия соединения.|  
|**CONNECTION_IN_USE**|**DBTYPE_I4**||Показывает активность соединения: 1 — активно, 0 — простаивает.|  
|**CONNECTION_LAST_COMMAND_END_TIME**|**DBTYPE_DBTIMESTAMP**||Дата и время сервера в формате UTC на момент завершения выполнения последней команды.|  
|**CONNECTION_LAST_COMMAND_START_TIME**|**DBTYPE_DBTIMESTAMP**||Дата и время на сервере в формате UTC, когда в последний раз запускалось выполнение команды.|  
|**CONNECTION_SERVER_NAME**|**DBTYPE_WSTR**||Имя сервера, с которым в настоящий момент установлено соединение.|  
|**CONNECTION_SPID**|**DBTYPE_I4**||Идентификатор сеанса.|  
|**CONNECTION_START_TIME**|**DBTYPE_DBTIMESTAMP**||Дата и время сервера в формате UTC на момент открытия соединения.|  
|**CONNECTION_USAGE_TIME_MS**|**DBTYPE_I8**||Время активной работы соединения (в миллисекундах) с момента начала соединения.|  
  
 Этот набор строк схемы не отсортирован.  
  
> [!IMPORTANT]  
>  Сведения в наборе строк **DISCOVER_DB_CONNECTIONS** будут отображаться только тогда, когда служба установит соединение с реляционными источниками данных.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк **DISCOVER_DB_CONNECTIONS** может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|CONNECTION_ID|DBTYPE_I4|Необязательный параметр.|  
|CONNECTION_IN_USE|DBTYPE_I4|Необязательный параметр.|  
|CONNECTION_SERVER_NAME|DBTYPE_WSTR|Необязательный параметр.|  
|CONNECTION_CATALOG_NAME|DBTYPE_WSTR|Обязательный.|  
|CONNECTION_SPID|DBTYPE_I4|Необязательный параметр.|  
  
## <a name="see-also"></a>См. также:  
 [Наборы строк схемы XML для аналитики](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
