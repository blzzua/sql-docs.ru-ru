---
title: "sys.database_filestream_options (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- database_filestream_options
- sys.database_filestream_options_TSQL
- database_filestream_options_TSQL
- sys.database_filestream_options
dev_langs:
- TSQL
helpviewer_keywords:
- sys.database_filestream_options catalog view
ms.assetid: 3383c607-0bbc-456a-ab37-7230f4cbf0e9
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e142ba218eb5474bb45f488c87a4c41e0d2390a7
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="sysdatabasefilestreamoptions-transact-sql"></a>sys.database_filestream_options (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Отображает сведения об уровне нетранзакционного доступа к данным FILESTREAM в каждой из включенных таблиц FileTable. Содержит по одной строке для каждой базы данных в экземпляре SQL Server.  
  
 Дополнительные сведения о таблицах Filetable см. в разделе [FileTables &#40; SQL Server &#41; ](../../relational-databases/blob/filetables-sql-server.md).  
  
  
|Столбец|Тип|Описание|  
|------------|----------|-----------------|  
|**database_id**|**int**|Идентификатор базы данных. Это значение уникально в рамках экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**directory_name**|**nvarchar(255)**|Каталог на уровне базы данных для всех пространств имен FileTable:|  
|**non_transacted_access**|**tinyint**|Включенный уровень нетранзакционного доступа к данным FILESTREAM. Уровень доступа, установленное параметром NON_TRANSACTED_ACCESS **CREATE DATABASE** или **инструкции ALTER DATABASE** инструкции.<br /><br /> Этот параметр имеет одно из следующих значений:<br /><br /> 0 — не включено. Это значение по умолчанию. Этот уровень устанавливается путем задания значения **OFF** для **NON_TRANSACTED_ACCESS** параметр.<br /><br /> 1 — доступ только для чтения. Этот уровень устанавливается путем задания значения **READ_ONLY** для **NON_TRANSACTED_ACCESS** параметр.<br /><br /> 3 — полный доступ. Этот уровень устанавливается путем задания значения **полного** для **NON_TRANSACTED_ACCESS** параметр.<br /><br /> 5 — переход в состояние READONLY.<br /><br /> 6 — переход в состояние OFF.|  
|**non_transacted_access_desc**|**nvarchar(60)**|Описание уровня нетранзакционного доступа, определенное в non_transacted_access.<br /><br /> Этот параметр имеет одно из следующих значений:<br /><br /> NONE — значение по умолчанию.<br /><br /> READ_ONLY<br /><br /> ПОЛНОЕ<br /><br /> IN_TRANSITION_TO_READ_ONLY<br /><br /> IN_TRANSITION_TO_OFF|  
  
## <a name="see-also"></a>См. также  
 [Включение необходимых компонентов для таблицы FileTable](../../relational-databases/blob/enable-the-prerequisites-for-filetable.md)  
  
  
