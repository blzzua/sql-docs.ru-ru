---
title: "Type-свойство (столбец) (ADOX) | Документы Microsoft"
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
- _Column::Type
- _Column::GetType
- _Column::get_Type
- _Column::put_Type
- _Column::PutType
helpviewer_keywords:
- Type property [ADOX]
ms.assetid: 5c6718b6-f728-478a-8afb-5d17b0a91d1f
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 351f97881ab3fc50fe9caf2218ca832845db511a
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="type-property-column-adox"></a>Свойство Type (столбец) (ADOX)
Указывает тип данных столбца.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает **длинные** значение, которое может быть одним из [DataTypeEnum](../../../ado/reference/ado-api/datatypeenum.md) константы. Значение по умолчанию — **adVarWChar**.  
  
## <a name="remarks"></a>Remarks  
 Это свойство является чтение и запись, пока не [столбца](../../../ado/reference/adox-api/column-object-adox.md) объект добавляется в коллекцию или к другому объекту, после чего она доступна только для чтения.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Column (ADOX)](../../../ado/reference/adox-api/column-object-adox.md)  
  
## <a name="see-also"></a>См. также  
 [Пример свойства ParentCatalog (Visual Basic)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)   
 [Свойство Type (ключ) (ADOX)](../../../ado/reference/adox-api/type-property-key-adox.md)   
 [Свойство Type (Table) (ADOX)](../../../ado/reference/adox-api/type-property-table-adox.md)
