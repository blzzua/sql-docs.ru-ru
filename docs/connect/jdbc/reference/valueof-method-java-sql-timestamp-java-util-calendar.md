---
title: "Метод valueOf (java.sql.Timestamp, java.util.Calendar) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7320c383-0b06-446d-963b-7005e50324a2
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 138a53f22791390600ed21e535a7c26597f46321
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="valueof-method-javasqltimestamp-javautilcalendar"></a>Метод valueOf (java.sql.Timestamp, java.util.Calendar)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Создает **DateTimeOffset** объект, представляющий точку во времени с определенным смещением относительно среднего времени по Гринвичу заданному значению java.sql.Timestamp и значению java.util.Calendar, указывающему смещение.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public static DateTimeOffset valueOf(java.sql.Timestamp timestamp, java.util.Calendar calendar)  
```  
  
#### <a name="parameters"></a>Параметры  
 *timestamp*  
  
 Значениеjava.sql.Timestamp.  
  
 *Календарь*  
  
 Значение смещения.  Компоненты даты и времени *календаря* устанавливается в соответствии с *timestamp* значение.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает объект DateTimeOffset, представляющий точку во времени, заданную объектом java.sql.Timestamp в объект заданного java.util.Calendar часового пояса.  
  
## <a name="remarks"></a>Замечания  
 Этот метод также задает объект java.util.Calendar до точки во времени, заданную объектом java.sql.Timestamp.  
  
## <a name="see-also"></a>См. также:  
 [Класс DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md)   
 [Элементы DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-members.md)  
  
  
