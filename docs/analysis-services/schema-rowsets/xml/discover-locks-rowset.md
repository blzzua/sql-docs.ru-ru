---
title: Набор строк DISCOVER_LOCKS | Документы Microsoft
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
- DISCOVER_LOCKS rowset
ms.assetid: dea48167-212c-40b7-a416-434042a1b697
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 6b164727506042ad2f202e0cc797ab8ede1e2903
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="discoverlocks-rowset"></a>Набор строк DISCOVER_LOCKS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Предоставляет сведения о текущих установленных блокировках на сервере.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 Набор строк **DISCOVER_LOCKS** содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Description|  
|-----------------|--------------------|------------|-----------------|  
|**LOCK_CREATION_TIME**|**DBTYPE_DBTIMESTAMP**||Время на сервере в формате UTC в момент запроса блокировки.|  
|**LOCK_GRANT_TIME**|**DBTYPE_DBTIMESTAMP**||Время на сервере в формате UTC в момент предоставления блокировки на ресурс.|  
|**LOCK_ID**|**DBTYPE_GUID**||Уникальный идентификатор блокировки в виде идентификатора GUID.|  
|**LOCK_OBJECT_ID**|**DBTYPE_WSTR**||Уникальный идентификатор блокируемого объекта.|  
|**LOCK_STATUS**|**DBTYPE_I4**||Состояние блокировки.<br /><br /> 0 означает «Ожидание блокировки объекта».<br /><br /> 1 означает «Блокировка предоставлена».|  
|**LOCK_TRANSACTION_ID**|**DBTYPE_GUID**||Уникальный идентификатор транзакции в виде идентификатора GUID.|  
|**LOCK_TYPE**|**DBTYPE_I4**||Битовая маска типов блокировки; дополнительные сведения см. в подразделе «Примечания» этого раздела.|  
|**SPID**|**DBTYPE_I4**||Идентификатор сеанса.|  
  
 Этот набор строк схемы не отсортирован.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк **DISCOVER_LOCKS** может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|SPID|DBTYPE_I4|Необязательный параметр.|  
|LOCK_TRANSACTION_ID|DBTYPE_GUID|Необязательный параметр.|  
|LOCK_OBJECT_ID|DBTYPE_WSTR|Необязательный параметр.|  
|LOCK_STATUS|DBTYPE_I4|Необязательный параметр.|  
|LOCK_TYPE|DBTYPE_I4|Необязательный параметр.|  
|LOCK_MIN_TOTAL_MS|DBTYPE_I8|Необязательный параметр.|  
  
## <a name="remarks"></a>Remarks  
  
## <a name="lock-types"></a>Типы блокировок  
  
|Имя блокировки|Значение|Description|  
|---------------|-----------|-----------------|  
|LOCK_NONE|0x0000000|Блокировка отсутствует.|  
|LOCK_SESSION_LOCK|0x0000001|Неактивный сеанс; нарушения в работе под действием других блокировок не возникают.|  
|LOCK_READ|0x0000002|Блокировка чтения во время обработки.|  
|LOCK_WRITE|0x0000004|Блокировка записи во время обработки.|  
|LOCK_COMMIT_READ|0x0000008|Блокировка фиксации, общая.|  
|LOCK_COMMIT_WRITE|0x0000010|Блокировка фиксации, монопольная.|  
|LOCK_COMMIT_ABORTABLE|0x0000020|Аварийное прекращение работы в ходе выполнения фиксации.|  
|LOCK_COMMIT_INPROGRESS|0x0000040|Происходит фиксация.|  
|LOCK_INVALID|0x0000080|Недействительная блокировка.|  
  
## <a name="see-also"></a>См. также:  
 [Наборы строк схемы XML для аналитики](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
