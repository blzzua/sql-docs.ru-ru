---
title: "sys.sysaltfiles (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-compatibility-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.sysaltfiles_TSQL
- sys.sysaltfiles
- sysaltfiles_TSQL
- sysaltfiles
dev_langs:
- TSQL
helpviewer_keywords:
- sysaltfiles system table
- sys.sysaltfiles compatibility view
ms.assetid: 698dec23-5336-4108-87a5-f8e407f8da09
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6b24d30b5ca6279636fbc618ac98a939784ac5c7
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="syssysaltfiles-transact-sql"></a>sys.sysaltfiles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  В особых случаях содержит строки, соответствующие файлам в базе данных.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**fileid**|**smallint**|Идентификационный номер файла. Уникален для каждой базы данных.|  
|**groupid**|**smallint**|Идентификационный номер файловой группы.|  
|**size**|**int**|Размер файла, в страницах по 8 килобайт (КБ).|  
|**maxsize**|**int**|Максимальный размер файла, в страницах по 8 КБ.<br /><br /> 0 = не возрастает.<br /><br /> -1 = размер файла может увеличиваться до полного заполнения диска.<br /><br /> 268435456 = файл журнала может увеличиваться до 2 ТБ.<br /><br /> Примечание: Баз данных, обновленных с размером файла журнала неограниченного возвращают -1 для максимального размера файла журнала.|  
|**growth**|**int**|Предельный размер базы данных.<br /><br /> 0 = не возрастает. В зависимости от значения состояния может представлять собой либо процент от размера файла, либо число страниц: Если **состояние** равно 0x100000, **рост** процент размера файла; в противном случае — это количество страниц.|  
|**status**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**perf**|**int**|Зарезервировано.|  
|**dbid**|**smallint**|Идентификационный номер базы данных, которой принадлежит данный файл.|  
|**name**|**sysname**|Логическое имя файла.|  
|**filename**|**nvarchar(260)**|Имя физического устройства. Включает полный путь к файлу.|  
  
## <a name="see-also"></a>См. также  
 [Сопоставление системных таблиц с системными представлениями &#40; Transact-SQL &#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Представления совместимости (Transact-SQL)](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
