---
title: sys.Routes (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/30/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- routes
- routes_TSQL
- sys.routes
- sys.routes_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.routes catalog view
ms.assetid: 8fc65915-8bd6-425b-95d9-6a8468cb1e48
caps.latest.revision: 33
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 21420e923b4120f547026c6a6a0d96d86deac782
ms.sourcegitcommit: 059fc64ba858ea2adaad2db39f306a8bff9649c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/04/2018
---
# <a name="sysroutes-transact-sql"></a>sys.routes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  Данное представление каталога содержит одну строку для каждого маршрута. Компонент Service Broker использует маршруты для определения сетевого адреса службы.   

[!INCLUDE[ssMIlimitation](../../includes/sql-db-mi-limitation.md)]
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Имя маршрута, уникальное в пределах базы данных. Не допускает значения NULL.|  
|**route_id**|**int**|Идентификатор маршрута. Не допускает значения NULL.|  
|**principal_id**|**int**|Идентификатор участника базы данных, которому принадлежит маршрут. Допускает значение NULL.|  
|**remote_service_name**|**nvarchar(256)**|Имя удаленной службы. Допускает значение NULL.|  
|**broker_instance**|**nvarchar(128)**|Идентификатор брокера, на котором расположена удаленная служба. Допускает значение NULL.|  
|**lifetime**|**datetime**|Дата и время истечения срока действия маршрута. Обратите внимание, что данное значение не использует местный часовой пояс. Вместо этого значение отображает время истечения срока действия в формате UTC. Допускает значение NULL.|  
|**address**|**nvarchar(256)**|Сетевой адрес, по которому компонент Service Broker отправляет сообщения удаленной службе. Допускает значение NULL. Для экземпляра управляемого базы данных SQL адрес должен быть локальным.|  
|**mirror_address**|**nvarchar(256)**|Сетевой адрес участника зеркального отображения для сервера, указанного в адресе. Допускает значение NULL.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
  
