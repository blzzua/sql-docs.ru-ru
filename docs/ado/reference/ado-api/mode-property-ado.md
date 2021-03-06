---
title: "Свойство режима (ADO) | Документы Microsoft"
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
- Connection15::Mode
- _Stream::Mode
- _Record::Mode
helpviewer_keywords:
- Mode property [ADO]
ms.assetid: 808661eb-0d7c-4e6d-8e40-9dc3bef3d77a
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 032780415e0869c5994b4630546131b4ad51e8c4
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="mode-property-ado"></a>Свойство режима (ADO)
Указывает имеющиеся права на изменение данных в [подключения](../../../ado/reference/ado-api/connection-object-ado.md), [запись](../../../ado/reference/ado-api/record-object-ado.md), или [поток](../../../ado/reference/ado-api/stream-object-ado.md) объекта.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает [ConnectModeEnum](../../../ado/reference/ado-api/connectmodeenum.md) значение. Значение по умолчанию для **подключения** — **adModeUnknown**. Значение по умолчанию для **запись** объект **adModeRead**. Значение по умолчанию для **поток** связанные с базового источника (открыть URL-адрес как источник или как значение по умолчанию **поток** из **запись**) —  **adModeRead**. Значение по умолчанию для **поток** не связан с основной источник (экземпляр в памяти) — **adModeUnknown**.  
  
## <a name="remarks"></a>Remarks  
 Используйте **режим** свойство, чтобы задать или получить разрешения на доступ используется поставщиком для текущего соединения. Можно задать **режим** свойства только если **подключения** объект закрыт.  
  
 Для **поток** объекта, если режим доступа не указано, оно наследуется из источника, используемую для открытия **поток** объекта. Например если **поток** открывается из **запись** объекта по умолчанию, он открыт в том же режиме как **записи**.  
  
 Это свойство является чтение и запись, пока объект находится закрыто, только для чтения, пока открыт объект.  
  
> [!NOTE]
>  **Удаленное использование службы данных** при использовании на стороне клиента **подключения** объекта, **режим** свойству можно присвоить только значение **adModeUnknown**.  
  
## <a name="applies-to"></a>Объект применения  
  
||||  
|-|-|-|  
|[Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)|[Объект Record (ADO)](../../../ado/reference/ado-api/record-object-ado.md)|[Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)|  
  
## <a name="see-also"></a>См. также  
 [IsolationLevel и пример свойства режима (Visual Basic)](../../../ado/reference/ado-api/isolationlevel-and-mode-properties-example-vb.md)   
 [IsolationLevel и пример свойства режима (VC ++)](../../../ado/reference/ado-api/isolationlevel-and-mode-properties-example-vc.md)   
