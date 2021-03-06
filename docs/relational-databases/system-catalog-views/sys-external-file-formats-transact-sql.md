---
title: "sys.external_file_formats (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: a89efb2c-0a3a-4b64-9284-6e93263e29ac
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 08318355eebbff784da00fc27303af1abbf17a31
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="sysexternalfileformats-transact-sql"></a>sys.external_file_formats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Содержит по одной строке для каждого формата внешнего файла в текущей базе данных для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssSDS](../../includes/sssds-md.md)], и [!INCLUDE[ssSDW](../../includes/sssdw-md.md)].  
  
 Содержит по одной строке для каждого формата внешнего файла на сервере для [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|file_format_id|**int**|Идентификатор объекта для формата внешнего файла.||  
|имя|**sysname**|Имя формата файла. в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и [!INCLUDE[ssSDW](../../includes/sssdw-md.md)], является уникальным для базы данных. В [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], он уникален для сервера.||  
|format_type|**tinyint**|Тип формата файла.|DELIMITEDTEXT, RCFILE, ORC, PARQUET.|  
|признак_конца_поля|**nvarchar(10)**|Format_type = DELIMITEDTEXT, признак конца поля.||  
|string_delimiter|**nvarchar(10)**|Format_type = DELIMITEDTEXT, это разделитель строк.||  
|date_format|**nvarchar(50)**|Format_type = DELIMITEDTEXT, это определяемые пользователем формат даты и времени.||  
|use_type_default|**бит**|Format_type = текста с ЗАПЯТЫМИ, указывает способ обработки отсутствующих значений при PolyBase, импорт данных из текстовых файлов HDFS в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)].|0 — сохранение отсутствующих значений строку «NULL».<br /><br /> 1 — сохранить отсутствующие значения как значение столбца по умолчанию.|  
|serde_method|**nvarchar(255)**|Format_type = RCFILE, метод сериализации или десериализации.||  
|признак_конца_строки|**nvarchar(10)**|Format_type = DELIMITEDTEXT, это строка символов, завершает каждой строки в файле внешних Hadoop.|Всегда «\n».|  
|кодировка|**nvarchar(10)**|Format_type = DELIMITEDTEXT, этот способ кодировки для внешнего файла Hadoop.|Всегда «UTF-8».|  
|data_compression|**nvarchar(255)**|Метод сжатия данных для внешних данных.|Format_type = DELIMITEDTEXT:<br /><br /> -«org.apache.hadoop.io.compress.DefaultCodec»<br />-   'org.apache.hadoop.io.compress.GzipCodec'<br /><br /> Format_type = RCFILE:<br /><br /> -«org.apache.hadoop.io.compress.DefaultCodec»<br /><br /> Format_type = ORC:<br /><br /> -«org.apache.hadoop.io.compress.DefaultCodec»<br />-«org.apache.hadoop.io.compress.SnappyCodec»<br /><br /> Format_type = PARQUET:<br /><br /> -   'org.apache.hadoop.io.compress.GzipCodec'<br />-«org.apache.hadoop.io.compress.SnappyCodec»|  
  
## <a name="permissions"></a>Разрешения  
 Видимость метаданных в представлениях каталогов ограничивается защищаемыми объектами, которыми пользователь владеет или на которые ему были предоставлены разрешения. Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [sys.external_data_sources &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-external-data-sources-transact-sql.md)   
 [sys.external_tables &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-external-tables-transact-sql.md)   
 [CREATE EXTERNAL FILE FORMAT (Transact-SQL)](../../t-sql/statements/create-external-file-format-transact-sql.md)  
  
  
