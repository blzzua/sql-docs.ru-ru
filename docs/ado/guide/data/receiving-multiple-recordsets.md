---
title: "Получение нескольких наборов записей | Документы Microsoft"
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
helpviewer_keywords:
- receiving multiple Recordsets [ADO]
- Recordset object [ADO], receiving multiple Recordsets
ms.assetid: 2a7ad7a6-f00d-4355-b0b5-d0ab957b0566
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 42c33de51f0de6c2de821ddb82b1e337ba47eb87
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="receiving-multiple-recordsets"></a>Получение нескольких наборов записей
[Поставщик Microsoft OLE DB для SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md) поддерживает возврат нескольких **записей** объектов одной команды, содержащего несколько инструкций SQL, один **записей**каждой инструкции SQL. Порядок, в котором **записей**, будут возвращены, следуя порядку, в которой инструкций SQL помещаются в тексте команды.  
  
 Поставщик Microsoft OLE DB для SQL Server также возвращает несколько результирующих наборов в ADO, если команда содержит предложение COMPUTE. Например, команду, содержащую следующую инструкцию SQL будут возвращать результаты в двух **записей** объектов: один для набора строк (*ProductID*, *ProductName*, *UnitPrice*), а другой — для среднюю цену всех продуктов в таблице.  
  
```  
SELECT ProductID, ProductName, UnitPrice   
  FROM PRODUCTS   
  COMPUTE AVG(UnitPrice)  
```  
  
 Можно использовать **Recordset.NextRecordset** метода для перечисления двух объектов.  
  
 Дополнительные сведения см. в разделе [NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md).
