---
title: "CDC.captured_columns (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- cdc.captured_columns
- cdc.captured_columns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- cdc.captured_columns
ms.assetid: 7bb4d408-d764-4ef6-802c-f271c8d39c2a
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e0f4ff663a64e2de3fa7a8247eee170907d1a624
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="cdccapturedcolumns-transact-sql"></a>cdc.captured_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает по одной строке для каждого столбца, отслеживаемого в экземпляре отслеживания. По умолчанию отслеживаются все столбцы в исходной таблице. Однако столбцы могут включаться или исключаться из процесса отслеживания, если исходная таблица включается для системы отслеживания измененных данных путем указания списка столбцов. Дополнительные сведения см. в разделе [sys.sp_cdc_enable_table &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sys-sp-cdc-enable-table-transact-sql.md).  
  
 Мы рекомендуем вам **не запрашивать системные таблицы непосредственно**. Вместо этого выполните [sys.sp_cdc_get_source_columns](../../relational-databases/system-stored-procedures/sys-sp-cdc-get-captured-columns-transact-sql.md) хранимой процедуры.  
   
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|Идентификатор исходной таблицы, которой принадлежит отслеживаемый столбец.|  
|**column_name**|**sysname**|Имя отслеживаемого столбца.|  
|**Идентификатор column_id**|**int**|Идентификатор отслеживаемого столбца в исходной таблице.|  
|**column_type**|**sysname**|Тип отслеживаемого столбца.|  
|**column_ordinal**|**int**|Порядковый номер столбца (начиная с 1) в исходной таблице. Метаданные столбца в исходной таблице исключаются. Порядковый номер 1 присваивается первому отслеживаемому столбцу.|  
|**is_computed**|**bit**|Указывает, что отслеживаемый столбец является вычисляемым столбцом в исходной таблице.|  
  
## <a name="see-also"></a>См. также:  
 [CDC.change_tables &#40; Transact-SQL &#41;](../../relational-databases/system-tables/cdc-change-tables-transact-sql.md)  
  
  
