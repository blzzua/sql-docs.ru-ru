---
title: "Свойство NamedParameters (ADO) | Документы Microsoft"
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
- _Command::NamedParameters
helpviewer_keywords:
- NamedParameters property [ADO]
ms.assetid: 42409387-026c-435f-a9b1-bf4167095875
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1c7f49abcb642a958d693351307586b4cbf37548
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="namedparameters-property-ado"></a>Свойство NamedParameters (ADO)
Указывает, следует ли передавать имена параметров для поставщика.  
  
## <a name="remarks"></a>Remarks  
 Если это свойство имеет значение true, ADO передается значение **имя** свойства каждого параметра в **параметр** коллекции для [объект команды](../../../ado/reference/ado-api/command-object-ado.md). Поставщик использует имя параметра, чтобы соответствовать параметрам в **CommandText** или **CommandStream** свойства. Если это свойство имеет значение false (по умолчанию), имена параметров пропускаются, и поставщик использует порядок параметров для сопоставления значений для параметров в **CommandText** или **CommandStream** свойства.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Свойства CommandText (ADO)](../../../ado/reference/ado-api/commandtext-property-ado.md)   
 [Свойство CommandStream (ADO)](../../../ado/reference/ado-api/commandstream-property-ado.md)   
 [Коллекция Parameters (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)
