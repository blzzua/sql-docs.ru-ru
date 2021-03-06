---
title: "sys.dm_os_loaded_modules (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/18/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_os_loaded_modules
- dm_os_loaded_modules
- sys.dm_os_loaded_modules_TSQL
- dm_os_loaded_modules_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_loaded_modules dynamic management view
ms.assetid: 56c7743a-b568-4943-bd3b-73c57d9d641c
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9e33e71c94cffe6b455be1b5a5fc0e22732e60f0
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmosloadedmodules-transact-sql"></a>sys.dm_os_loaded_modules (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает по строке для каждого модуля, загруженного в адресное пространство сервера.  
  
> [!NOTE]  
>  Вызов его из [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], используйте имя **sys.dm_pdw_nodes_os_loaded_modules**.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**base_address**|**varbinary(8)**|Адрес модуля в процессе.|  
|**file_version**|**varchar(23)**|Версия файла. Отображается в следующем формате:<br /><br /> x.x:x.x|  
|**product_version**|**varchar(23)**|Версия продукта. Отображается в следующем формате:<br /><br /> x.x:x.x|  
|**debug**|**бит**|1 = Модуль является отладочной версией загруженного модуля.|  
|**patched**|**бит**|1 = Модуль был обновлен.|  
|**prerelease**|**бит**|1 = Модуль является предварительной версией загруженного модуля.|  
|**private_build**|**бит**|1 = Модуль является внутренней сборкой загруженного модуля.|  
|**special_build**|**бит**|1 = Модуль является специальной сборкой загруженного модуля.|  
|**language**|**int**|Язык сведений о версии модуля.|  
|**компании**|**nvarchar(256)**|Имя компании, создавшей модуль.|  
|**Описание**|**nvarchar(256)**|Описание модуля.|  
|**name**|**nvarchar(255)**|Имя модуля. Включает полный путь к модулю.|  
|**pdw_node_id**|**int**|**Применяется к**: [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Идентификатор для узла, это распределение.|  
  
## <a name="permissions"></a>Разрешения  
 необходимо разрешение VIEW SERVER STATE на сервере.  
  
## <a name="see-also"></a>См. также  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Относящиеся к операционной системе SQL Server динамические административные представления &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  
