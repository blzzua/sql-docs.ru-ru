---
title: "Свойство AdvancedProperties (класс SqlService) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: wmi
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- AdvancedProperties Property (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
helpviewer_keywords:
- AdvancedProperties property
ms.assetid: 63bcb7e2-1f78-4961-b4b9-1b635a89079b
caps.latest.revision: 
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 32cc8f44db211fa2c3b69a7a5a952ee2ea40811e
ms.sourcegitcommit: 0d904c23663cebafc48609671156c5ccd8521315
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2018
---
# <a name="advancedproperties-property-sqlservice-class"></a>Свойство AdvancedProperties (класс SqlService)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Получает или задает массив ссылок на объекты, содержащие дополнительные свойства для **SqlService** объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.AdvancedProperties [= value]  
```  
  
## <a name="parts"></a>Компоненты  
 *объект*  
 Объект [класса SqlService](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) , представляющий службу.  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Массив [класс SqlServiceAdvancedProperty](../../../relational-databases/wmi-provider-configuration-classes/sqlserviceadvancedproperty-class/sqlserviceadvancedproperty-class.md) объекты, содержащие дополнительные свойства для **SqlService** объекта.  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>См. также:  
 [Запуск и остановка служб](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
