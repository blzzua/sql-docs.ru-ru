---
title: "Исходное свойство (запись ADO) | Документы Microsoft"
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
- _Record::Source
- _Record::PutRefSource
- _Record::GetSource
- _Record::put_Source
- _Record::putref_Source
- _Record::get_Source
helpviewer_keywords:
- Source property [ADO Record]
ms.assetid: 2c18279e-6f35-4af0-b12e-8f1543d9ed20
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1ea9472275b0dbaa8a1a88ba70c21e8b6576af14
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="source-property-ado-record"></a>Свойство Source (ADO запись)
Указывает источник данных или объекта, представленного [записи](../../../ado/reference/ado-api/record-object-ado.md).  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает **Variant** значение, указывающее, сущности, представленной **записи**.  
  
## <a name="remarks"></a>Remarks  
 **Источника** возвращает *источника* аргумент **запись** объекта [откройте](../../../ado/reference/ado-api/open-method-ado-record.md) метод. Он может содержать строку абсолютный или относительный URL-адрес. Абсолютный URL-адрес может быть использован без параметра [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) свойства, чтобы открыть непосредственно **записи** объекта. Неявный **подключения** в этом случае создается объект.  
  
 **Источника** свойство также может содержать ссылку на уже открыта **набора записей**, чтобы открыть **записи** объект, представляющий текущую строку в  **Набор записей**.  
  
 **Источника** свойство также может содержать ссылку на [команда](../../../ado/reference/ado-api/command-object-ado.md) объекта, который возвращает одну строку данных от поставщика.  
  
 Если **ActiveConnection** свойство задано, то **источника** свойство должно указывать на какой-либо объект, который существует в пределах данного соединения. Например, в древовидной структурой пространства имен Если **источника** содержит абсолютный URL-адрес, оно должно указывать на узел, который существует в области узла, идентифицируемого выражением URL-адреса в строке подключения. Если **источника** свойство содержит относительный URL-адрес, а затем проходит проверку в контексте задается **ActiveConnection** свойство.  
  
 **Источника** свойство является чтение и запись при **запись** объект закрывается и доступно только для чтения при **записи** открыт объект.  
  
> [!NOTE]
>  URL-адреса, с помощью схемы http автоматически вызывает [поставщик Microsoft OLE DB для публикаций в Интернете](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Дополнительные сведения см. в разделе [абсолютные и относительные URL-адреса](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Record (ADO)](../../../ado/reference/ado-api/record-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Свойство Source (ошибка)](../../../ado/reference/ado-api/source-property-ado-error.md)   
 [Свойство Source (объект Recordset ADO)](../../../ado/reference/ado-api/source-property-ado-recordset.md)
