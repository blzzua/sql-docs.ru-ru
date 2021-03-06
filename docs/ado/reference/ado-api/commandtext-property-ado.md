---
title: "Свойства CommandText (ADO) | Документы Microsoft"
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
- Command15::CommandText
helpviewer_keywords:
- CommandText property [ADO]
ms.assetid: 4dd7e82a-8da5-4a4e-b439-11a29286fa0e
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1edaf4f4d9e4132547bfa1c44308806743ed98e1
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="commandtext-property-ado"></a>Свойства CommandText (ADO)
Показывает, что текст команды должна быть выдан для поставщика.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает **строка** значение, содержащее команды поставщика, например инструкцию SQL, имя таблицы, относительный URL-адрес или вызов хранимой процедуры. Значение по умолчанию — пустая строка (»»).  
  
## <a name="remarks"></a>Remarks  
 Используйте **CommandText** свойство задает или возвращает текст команды, представленного [команда](../../../ado/reference/ado-api/command-object-ado.md) объекта. Обычно это будет инструкция SQL, но также может быть любого типа инструкции команды распознаются поставщиком, например вызов хранимой процедуры. Инструкции SQL должен иметь определенный, диалект или версию, поддерживаемую обработчиком запросов поставщика.  
  
 Если [Готово](../../../ado/reference/ado-api/prepared-property-ado.md) свойство **команда** , присваивается значение **True** и **команда** объект привязан к открытое соединение при установке **CommandText** свойство ADO подготавливает запроса (то есть скомпилированную форму запроса, хранимых поставщиком) при вызове [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md) или [откройте](../../../ado/reference/ado-api/open-method-ado-connection.md)методы.  
  
 В зависимости от [CommandType](../../../ado/reference/ado-api/commandtype-property-ado.md) могут изменять параметр свойства ADO **CommandText** свойство. Можно прочитать **CommandText** свойство в любое время, чтобы увидеть действительный текст команды ADO, будет использоваться во время выполнения.  
  
 Используйте **CommandText** свойство задание или возврат указать относительный URL-адрес ресурса, например файла или каталога. Ресурс является относительно расположения, явно указано, абсолютный URL-адрес, или неявно открытого [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объекта.  
  
> [!NOTE]
>  URL-адреса, с помощью схемы http автоматически вызывает [поставщик Microsoft OLE DB для публикаций в Интернете](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Дополнительные сведения см. в разделе [абсолютные и относительные URL-адреса](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [ActiveConnection CommandText, CommandTimeout, CommandType, размер и направление-пример свойства (Visual Basic)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [ActiveConnection CommandText, CommandTimeout, CommandType, размер и направление примере свойства (VC ++)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [Requery-метод](../../../ado/reference/ado-api/requery-method.md)   
 [ActiveConnection, CommandText, CommandTimeout, CommandType, размер и направление-пример свойства (JScript)](../../../ado/reference/ado-api/activeconnection-commandtext-timeout-type-size-example-jscript.md)
