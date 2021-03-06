---
title: Событие WillExecute (ADO) | Документы Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: article
apitype: COM
f1_keywords:
- WillExecute
- Connection::WillExecute
helpviewer_keywords:
- WillExecute event [ADO]
ms.assetid: dd755e46-f589-48a3-93a9-51ff998d44b5
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: dafc71b9f9da6dde5cf9ef7acf7909236441f656
ms.sourcegitcommit: d6b1695c8cbc70279b7d85ec4dfb66a4271cdb10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2018
---
# <a name="willexecute-event-ado"></a>Событие WillExecute (ADO)
**WillExecute** событие вызывается непосредственно перед выполнением ожидающие команды для подключения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
WillExecute Source, CursorType, LockType, Options, adStatus, pCommand, pRecordset, pConnection  
```  
  
#### <a name="parameters"></a>Параметры  
 *Source*  
 Объект **строка** , содержащий команду SQL или имя хранимой процедуры.  
  
 *CursorType*  
 Объект [CursorTypeEnum](../../../ado/reference/ado-api/cursortypeenum.md) , содержащее тип курсора для **записей** , будет открыт. С помощью этого параметра можно изменить курсор на любой тип во время **записей**[метода Open (набора записей ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md) операции. *CursorType* для любой другой операции будут игнорироваться.  
  
 *LockType*  
 Объект [LockTypeEnum](../../../ado/reference/ado-api/locktypeenum.md) , содержащий тип блокировки для **записей** , будет открыт. С помощью этого параметра можно изменить блокировку для любого типа во время **RecordsetOpen** операции. *LockType* игнорируется для любой другой операции.  
  
 *Параметры*  
 Объект **длинные** значение, указывающее параметры, которые могут использоваться для выполнения команды или открыть **записей**.  
  
 *adStatus*  
 [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) значение состояния, которые могут быть **adStatusCantDeny** или **adStatusOK** при вызове этого события. Если это **adStatusCantDeny**, это событие не может запросить отмену отложенной операции.  
  
 *pCommand*  
 [Команда Objects (ADO)](../../../ado/reference/ado-api/command-object-ado.md) объектов, для которого применяется это уведомление о событии.  
  
 *pRecordset*  
 [Объекта набора записей (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md) объектов, для которого применяется это уведомление о событии.  
  
 *pConnection*  
 [Объект соединения (ADO)](../../../ado/reference/ado-api/connection-object-ado.md) объектов, для которого применяется это уведомление о событии.  
  
## <a name="remarks"></a>Замечания  
 Объект **WillExecute** событие может происходить из-за соединения.  [Выполнить метод (соединение ADO)](../../../ado/reference/ado-api/execute-method-ado-connection.md), [выполнить метод (команда ADO)](../../../ado/reference/ado-api/execute-method-ado-command.md), или [метода Open (набора записей ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md) метод *pConnection* следует параметр всегда содержать допустимую ссылку на **подключения** объекта. Если это событие из-за **Connection.Execute**, *pRecordset* и *командной* параметры имеют значение **ничего не**. Если это событие из-за **Recordset.Open**, *pRecordset* параметр будет ссылаться **записей** объекта и *командной* параметр имеет значение **ничего не**. Если это событие из-за **Command.Execute**, *командной* параметр будет ссылаться **команда** объекта и *pRecordset* параметр имеет значение **ничего не**.  
  
 **WillExecute** позволяет проверять и изменять параметры ожидается выполнение. Это событие может вернуть запрос отмены ожидания выполнения команды.  
  
> [!NOTE]
>  Если исходный источник для **команда** представляет собой поток, определяемое [свойство CommandStream (ADO)](../../../ado/reference/ado-api/commandstream-property-ado.md) свойства, назначив новую строку для **WillExecute *** источника* параметр изменяет источник **команда**. **CommandStream** свойство будет очищено и [свойства CommandText (ADO)](../../../ado/reference/ado-api/commandtext-property-ado.md) свойство будет добавлено в новый источник. Исходный поток, определяемое **CommandStream** будут выпущены и становятся недоступными.  
  
 Если диалект новые строки исходного кода отличается от исходного значения [свойство Dialect](../../../ado/reference/ado-api/dialect-property.md) свойство (который значение соответствовало **CommandStream**), должен быть указан правильный диалект, задав **диалект** свойства объекта команды ссылается *командной*.  
  
## <a name="see-also"></a>См. также  
 [Пример модели событий ADO (VC ++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Сводка обработчик событий ADO](../../../ado/guide/data/ado-event-handler-summary.md)   
 [Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)
