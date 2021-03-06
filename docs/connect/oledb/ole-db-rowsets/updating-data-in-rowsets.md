---
title: Обновление данных в наборах строк | Документы Microsoft
description: Обновление данных в наборах строк с помощью драйвера OLE DB для SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-rowsets
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- updating data [SQL Server]
- rowsets [OLE DB], updating data
- OLE DB Driver for SQL Server, rowsets
- OLE DB rowsets, updating data
- OLE DB Driver for SQL Server, data updates
- data updates [SQL Server], OLE DB
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: cc8816993330718218631335db1611cc0581d594
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2018
---
# <a name="updating-data-in-rowsets"></a>Обновление данных в наборах строк
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Драйвер OLE DB для SQL Server обновлений [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] данных, если потребитель обновляет изменяемый набор строк, который содержит данные. Изменяемый набор строк создается в том случае, если потребитель запрашивает поддержку либо для **IRowsetChange** или **IRowsetUpdate** интерфейса.  
  
 Все драйвер OLE DB для изменяемой SQL Server используйте наборы строк [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] курсоров для поддержки набора строк. Свойство DBPROP_LOCKMODE набора строк изменяет поведение управления параллелизмом [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в курсорах, а также определяет поведение выборки строки из набора строк и создание ошибок целостности данных в наборах строк, которые можно обновлять.  
  
 Драйвер OLE DB для SQL Server поддерживает синхронизацию строк до или после обновления.  
  
> [!NOTE]  
>  Интерфейс IRowChange::SetColumns может установить значения одного или более именованных столбцов объекта-строки.  
  
## <a name="in-this-section"></a>В этом разделе  
  
-   [Обновление данных в курсорах SQL Server](../../oledb/ole-db-rowsets/updating-data-in-sql-server-cursors.md)  
  
-   [Повторная синхронизация строк](../../oledb/ole-db-rowsets/updating-data-in-rowsets-resynchronizing-rows.md)  
  
## <a name="see-also"></a>См. также  
 [Наборы строк](../../oledb/ole-db-rowsets/rowsets.md)  
  
  
