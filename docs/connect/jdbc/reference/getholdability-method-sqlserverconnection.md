---
title: "Метод (SQLServerConnection) getHoldability | Документы Microsoft"
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
apiname: SQLServerConnection.getHoldability
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: b1644791-c36a-4837-86c4-9299537ee1c2
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9c7004b0720e285eaf031be2b79588caf3577325
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="getholdability-method-sqlserverconnection"></a>getHoldability метод (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Извлекает значение текущего удержания [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекты, созданные с помощью этого [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public int getHoldability()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **Int** значение, которое содержит один из следующих уровней удержания:  
  
 HOLD_CURSORS_OVER_COMMIT  
  
 CLOSE_CURSORS_AT_COMMIT  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getHoldability указывается с помощью метода getHoldability в интерфейсе java.sql.Connection.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
