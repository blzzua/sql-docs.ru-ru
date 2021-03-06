---
title: "ADOX перечисляемые константы | Документы Microsoft"
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
- enumerated constants [ADOX]
ms.assetid: 9d91f511-d46f-44ef-97ef-77bf93836186
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 880c49c4cfda1faf32313ac919939bcba734ced5
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="adox-enumerated-constants"></a>ADOX перечисляемые константы
Чтобы упростить отладку, константы перечисления ADOX списка значение для каждой константы. Тем не менее это значение исключительно рекомендации и может меняться от одного выпуска ADOX в другой. Код только должны зависеть от имени, а не фактического значения перечислимых констант.  
  
 Определены следующие константы перечисления.  
  
|Перечисление|Описание|  
|-----------------|-----------------|  
|[ActionEnum](../../../ado/reference/adox-api/actionenum.md)|Указывает тип действия, выполняемые при **SetPermissions** вызывается.|  
|[AllowNullsEnum](../../../ado/reference/adox-api/allownullsenum.md)|Указывает, проиндексировано ли записи со значениями null.|  
|[ColumnAttributesEnum](../../../ado/reference/adox-api/columnattributesenum.md)|Задает характеристики **столбца**.|  
|[DataTypeEnum](../../../ado/reference/ado-api/datatypeenum.md)|Указывает тип данных **поле**, **параметр**, или **свойства**.|  
|[InheritTypeEnum](../../../ado/reference/adox-api/inherittypeenum.md)|Указывает, каким образом объекты будут наследовать разрешения, установленные с **SetPermissions**.|  
|[KeyTypeEnum](../../../ado/reference/adox-api/keytypeenum.md)|Указывает тип **ключ**: внешний, первичный или уникальный.|  
|[ObjectTypeEnum](../../../ado/reference/adox-api/objecttypeenum.md)|Указывает тип объекта базы данных, для которого требуется задать разрешения или его владельца.|  
|[RightsEnum](../../../ado/reference/adox-api/rightsenum.md)|Указывает на объект права и разрешения для группы или пользователя.|  
|[RuleEnum](../../../ado/reference/adox-api/ruleenum.md)|Указывает правило, когда **ключ** удаляется.|  
|[SortOrderEnum](../../../ado/reference/adox-api/sortorderenum.md)|Задает последовательность сортировки для индексированного столбца.|  
  
## <a name="see-also"></a>См. также  
 [Справочник по API ADOX](../../../ado/reference/adox-api/adox-api-reference.md)   
 [Расширения ADO для языка описания данных и безопасности (ADOX)](../../../ado/guide/extensions/ado-extensions-for-data-definition-language-and-security-adox.md)
