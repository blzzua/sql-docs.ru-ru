---
title: Набор строк DBSCHEMA_CATALOGS | Документы Microsoft
ms.custom: ''
ms.date: 03/03/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DBSCHEMA_CATALOGS
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DBSCHEMA_CATALOGS rowset
ms.assetid: f02dc75d-5442-4eea-b33a-567dc816be7a
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 493ffd66eb4bcddd0e4aaef7c79c4c771520be92
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="dbschemacatalogs-rowset"></a>Набор строк DBSCHEMA_CATALOGS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Определяет физические атрибуты, связанные с каталогами, доступными из системы управления базой данных (СУБД).  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 Набор строк **DBSCHEMA_CATALOGS** содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Description|  
|-----------------|--------------------|------------|-----------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|255|Имя каталога. Не может иметь значение null.|  
|**DESCRIPTION**|**DBTYPE_WSTR**||Понятное описание таблицы.|  
|**РОЛИ**|**DBTYPE_WSTR**||Разделенный запятыми список ролей, к которым относится текущий пользователь.<br /><br /> Символ звездочки (\*) включается как роль, если текущий пользователь является сервера или администратор базы данных.<br /><br /> **Username** присоединяется к **ROLES** , если одна из ролей использует динамическую безопасность.|  
|**DATE_MODIFIED**|**DBTYPE_DBTIMESTAMP**||Дата последнего изменения каталога.|  
  
 Набор строк отсортирован по полю **CATALOG_NAME**.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк **DBSCHEMA_CATALOGS** может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|Необязательно|  
  
## <a name="see-also"></a>См. также:  
 [Наборы строк схемы OLE DB](../../../analysis-services/schema-rowsets/ole-db/ole-db-schema-rowsets.md)  
  
  
