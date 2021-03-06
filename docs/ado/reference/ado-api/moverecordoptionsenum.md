---
title: "MoveRecordOptionsEnum | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- MoveRecordOptionsEnum
helpviewer_keywords:
- MoveRecordOptionsEnum enumeration [ADO]
ms.assetid: f53c2ce4-1021-4a45-92b8-775e8bebad99
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d42dbc66f84a3b087401063ee3a53a00f2f37105
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="moverecordoptionsenum"></a>MoveRecordOptionsEnum
Задает поведение [запись](../../../ado/reference/ado-api/record-object-ado.md) объекта [MoveRecord](../../../ado/reference/ado-api/moverecord-method-ado.md) метод.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adMoveUnspecified**|-1|По умолчанию. Выполняет операцию перемещения по умолчанию: завершится ошибкой, если целевой файл или каталог уже существует, и операция обновляет гипертекстовых ссылок.|  
|**adMoveOverWrite**|1|Перезаписывает конечный файл или каталог, даже если он уже существует.|  
|**adMoveDontUpdateLinks**|2|Изменяет поведение по умолчанию **MoveRecord** метод, не обновляя гипертекстовые ссылки источника **записи**. Поведение по умолчанию зависит от возможностей поставщика. Операция перемещения обновляет ссылки, поддерживает ли поставщик. Если поставщик не может исправить ссылки или если это значение не указано, перемещение успешно, даже если ссылки не будут исправлены.|  
|**adMoveAllowEmulation**|4|Запросы, поставщик пытаться имитировать перемещения (с помощью загрузки, загрузки и операции удаления). Если попытка переместить **записи** завершается ошибкой, поскольку URL-адрес назначения находится на другом сервере или обслуживаемых разными поставщиками, чем источник это может вызвать увеличение задержки или потери данных, из-за возможности другого поставщика при Перемещение ресурсов между поставщиками.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Эти константы не имеют эквивалентов ADO/WFC.  
  
## <a name="applies-to"></a>Объект применения  
 [Метод MoveRecord (ADO)](../../../ado/reference/ado-api/moverecord-method-ado.md)
