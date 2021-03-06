---
title: "sys.syscomments (Transact-SQL) | Документы Microsoft"
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
- sys.syscomments_TSQL
- syscomments
- syscomments_TSQL
- sys.syscomments
dev_langs:
- TSQL
helpviewer_keywords:
- sys.syscomments compatibility view
- syscomments system table
ms.assetid: 767dd410-6bc9-4c4a-ab0f-6d2cf6163426
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 9a49d0a12cbf6e8f0c07cf6913786a0b437f1d0a
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="syssyscomments-transact-sql"></a>sys.syscomments (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит записи для всех представлений, правил, значений по умолчанию, триггеров, ограничений CHECK и DEFAULT, а также для всех хранимых процедур в базе данных. **Текст** столбец содержит инструкции исходных определений SQL.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Рекомендуется вместо этого используйте представление sys.sql_modules. Дополнительные сведения см. в разделе [sys.sql_modules &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md).  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**идентификатор**|**int**|Идентификатор объекта, к которому применяется текст.|  
|**number**|**smallint**|Номер внутри группирования процедур, если группирование существует.<br /><br /> 0 = записи не являются процедурами.|  
|**colid**|**smallint**|Последовательный номер строки для определения объекта с длиной более 4 000 символов.|  
|**status**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**ctext**|**varbinary(8000)**|Приблизительное число байтов в инструкции определения SQL.|  
|**texttype**|**smallint**|0 = пользовательский комментарий<br /><br /> 1 = системный комментарий<br /><br /> 4 = зашифрованный комментарий|  
|**language**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**шифрование**|**бит**|Указывает, применялось ли к определению процедуры запутывание.<br /><br /> 0 = запутывание не применялось;<br /><br /> 1 = запутывание применялось.<br /><br /> **\*\*Важные \* \***  позволяет замаскировать определения хранимых процедур, используется инструкция CREATE PROCEDURE с ключевым словом ENCRYPTION.|  
|**compressed**|**бит**|Всегда возвращает значение 0. Это означает, что процедура сжата.|  
|**text**|**nvarchar(4000)**|Фактический текст инструкции определения SQL.<br /><br /> Семантика расшифрованных выражений соответствует исходному тексту, однако правильность синтаксиса не гарантируется. Например, пробельные символы удаляются из расшифрованного выражения.<br /><br /> Это [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]-представление, совместимое получает информацию из текущих [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] структуры и может возвращать больше символов, чем **nvarchar(4000)** определения. **sp_help** возвращает **nvarchar(4000)** как тип данных текстового столбца. При работе с **syscomments** рассмотрите возможность использования **nvarchar(max)**. Не следует использовать для новых разработок **syscomments**.|  
  
## <a name="see-also"></a>См. также  
 [Сопоставление системных таблиц с системными представлениями &#40; Transact-SQL &#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Представления совместимости (Transact-SQL)](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
