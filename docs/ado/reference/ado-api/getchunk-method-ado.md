---
title: "Метод GetChunk (ADO) | Документы Microsoft"
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
- Field20::raw_GetChunk
- Field20::GetChunk
helpviewer_keywords:
- GetChunk method [ADO]
ms.assetid: fc268e22-205b-44a3-9038-ffed51e23e10
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b479146e26196e42836ce381e3f5e555dd0a9a6b
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="getchunk-method-ado"></a>Метод GetChunk (ADO)
Возвращает все или часть, содержимое большие текстовые или двоичные данные [поле](../../../ado/reference/ado-api/field-object.md) объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
variable = field.GetChunk(Size)  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает **Variant**.  
  
#### <a name="parameters"></a>Параметры  
 *Размер*  
 Объект **длинные** выражение, которое равно числу байт или символов, которые требуется извлечь.  
  
## <a name="remarks"></a>Remarks  
 Используйте **GetChunk** метод **поле** объекта для извлечения всех или части его долго двоичных или символьных данных. В ситуациях, где ограничена системной памяти, можно использовать **GetChunk** метод для обработки длинные значения в части, а не полностью.  
  
 Данные, **GetChunk** вызов возвращает назначается *переменной*. Если *размер* больше, чем оставшиеся данные **GetChunk** метод возвращает оставшиеся данные без заполнения *переменной* пробелами. Если поле не заполнено, **GetChunk** метод возвращает значение null.  
  
 Каждый последующий **GetChunk** вызов получает данные, начиная с которого предыдущей **GetChunk** вызова было остановлено. Тем не менее если необходимо извлечь данные из одного поля, а затем возможность задать или прочитать значение другого поля в текущей записи ADO предполагается, что после завершения извлечения данных из первого поля. При вызове метода **GetChunk** метод на первое поле, ADO интерпретирует вызов как новый **GetChunk** операции и начинается при считывании начала данных. Доступ к полям в других [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объектов, не являющихся клоны первого **записей** объекта не приведет к нарушению **GetChunk** операций.  
  
 Если **adFldLong** бит в [атрибуты](../../../ado/reference/ado-api/attributes-property-ado.md) свойство **поле** , присваивается значение **True**, можно использовать **GetChunk**  метод для этого поля.  
  
 Если отсутствует текущая запись. При использовании **GetChunk** метод **поле** объекта, возникает ошибка 3021 (текущая запись).  
  
> [!NOTE]
>  **GetChunk** метод не выполняет операций **поле** объектов [записи](../../../ado/reference/ado-api/record-object-ado.md) объекта. Он не осуществляет никаких операций и приведет к ошибке во время выполнения.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Field](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>См. также  
 [AppendChunk и пример GetChunk методы (Visual Basic)](../../../ado/reference/ado-api/appendchunk-and-getchunk-methods-example-vb.md)   
 [AppendChunk и пример методы GetChunk (VC ++)](../../../ado/reference/ado-api/appendchunk-and-getchunk-methods-example-vc.md)   
 [Метод AppendChunk (ADO)](../../../ado/reference/ado-api/appendchunk-method-ado.md)   
 [Свойство Attributes (ADO)](../../../ado/reference/ado-api/attributes-property-ado.md)
