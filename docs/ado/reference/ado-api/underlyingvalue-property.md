---
title: "Свойство UnderlyingValue | Документы Microsoft"
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
- Field20::GetUnderlyingValue
- Field20::get_UnderlyingValue
- Field20::UnderlyingValue
helpviewer_keywords:
- UnderlyingValue property
ms.assetid: 00a0c8b8-8b63-433f-95b8-020ab05874a0
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 739852d4cbfa4aaf2cf45a59b81b60e23617597f
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="underlyingvalue-property"></a>Свойство UnderlyingValue
Указывает текущее значение [поле](../../../ado/reference/ado-api/field-object.md) объекта в базе данных.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает **Variant** значение, указывающее значение **поля**.  
  
## <a name="remarks"></a>Remarks  
 Используйте **UnderlyingValue** свойство для возврата текущего значения поля из базы данных. Значение поля в **UnderlyingValue** свойство-значение, являются видимыми для транзакции и может быть результатом последнее обновление другой транзакцией. Он может отличаться от [OriginalValue](../../../ado/reference/ado-api/originalvalue-property-ado.md) свойство, которое отражает значение, которое изначально было возвращено [записей](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
 Это похоже на использование [Resync](../../../ado/reference/ado-api/resync-method.md) метода, но **UnderlyingValue** свойство возвращает только значение для указанного поля текущей записи. Это то же самое значение, которое [Resync](../../../ado/reference/ado-api/resync-method.md) метод используется для замены [значение](../../../ado/reference/ado-api/value-property-ado.md) свойства.  
  
 При использовании этого свойства и **OriginalValue** можно устранить конфликты, возникающие из пакета обновления.  
  
## <a name="record"></a>Записей  
 Для [запись](../../../ado/reference/ado-api/record-object-ado.md) объектов, это свойство будет пустым для полей, перед тем как добавить [обновление](../../../ado/reference/ado-api/update-method.md) вызывается.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Field](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>См. также  
 [OriginalValue и UnderlyingValue-пример свойства (Visual Basic)](../../../ado/reference/ado-api/originalvalue-and-underlyingvalue-properties-example-vb.md)   
 [OriginalValue и пример свойства UnderlyingValue (VC ++)](../../../ado/reference/ado-api/originalvalue-and-underlyingvalue-properties-example-vc.md)   
 [Свойство OriginalValue (ADO)](../../../ado/reference/ado-api/originalvalue-property-ado.md)   
 [Метод Resync](../../../ado/reference/ado-api/resync-method.md)
