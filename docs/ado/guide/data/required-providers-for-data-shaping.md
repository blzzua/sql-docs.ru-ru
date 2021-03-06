---
title: Необходимые поставщики данных формировать | Документы Microsoft
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
helpviewer_keywords:
- providers [ADO], data shaping
- data shaping [ADO], providers required
ms.assetid: d49d48d2-ac2d-4c11-895c-5a149b444620
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 577c377c4c8022272ffb7c55507d3fdc378aa440
ms.sourcegitcommit: d6b1695c8cbc70279b7d85ec4dfb66a4271cdb10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2018
---
# <a name="required-providers-for-data-shaping"></a>Для формирования данных службы необходимых поставщиков
Формирование данных обычно требует двух поставщиков. Поставщик услуг [службы Data Shaping Service для OLE DB](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md), предоставляющий формирования функциональные возможности и поставщика данных, например поставщик OLE DB для SQL Server данных, передает строки данных для заполнения формы [набора записей ](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
 В качестве значения можно указать имя поставщика услуг (MSDataShape) [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объекта [поставщика](../../../ado/reference/ado-api/provider-property-ado.md) свойства или ключевое слово строки подключения «поставщик = MSDataShape;».  
  
 Имя поставщика данных можно указать в качестве значения **поставщик данных** динамические свойства, которое добавляется к **подключения** объекта [свойства](../../../ado/reference/ado-api/properties-collection-ado.md) коллекции с помощью службы Data Shaping Service для OLE DB или ключевое слово строки соединения «**поставщик данных = *** поставщика*».  
  
 Поставщик данных не является обязательным, если **записей** не заполняется (например, как создано **записей** где столбцы создаются с помощью ключевого слова NEW). В этом случае указать "**поставщик данных =**none;».  
  
## <a name="example"></a>Пример  
  
```  
Dim cnn As New ADODB.Connection  
cnn.Provider = "MSDataShape"  
cnn.Open "Data Provider=SQLOLEDB;Integrated Security=SSPI;Database=Northwind"  
```  
  
## <a name="see-also"></a>См. также  
 [Пример формирования данных](../../../ado/guide/data/data-shaping-example.md)   
 [Грамматика формальных фигуры](../../../ado/guide/data/formal-shape-grammar.md)   
 [Общие сведения о командах формирования данных](../../../ado/guide/data/shape-commands-in-general.md)
