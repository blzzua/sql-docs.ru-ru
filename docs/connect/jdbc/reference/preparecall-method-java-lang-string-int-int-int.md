---
title: "Метод prepareCall (java.lang.String, int, int, int) | Документы Microsoft"
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
apiname: SQLServerConnection.prepareCall (java.lang.String, int, int, int)
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 81104fd5-75b0-4540-9f48-c3dbf59a8564
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 67154127b6428a0b41960b6b822c3e727d6224f5
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="preparecall-method-javalangstring-int-int-int"></a>Метод prepareCall (java.lang.String, int, int, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Создает [SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md) объект, который формирует [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекты с заданным типом, параллелизма и возможностью сохранения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.CallableStatement prepareCall(java.lang.String sql,  
                                              int nType,  
                                              int nConcur,  
                                              int nHold)  
```  
  
#### <a name="parameters"></a>Параметры  
 *SQL*  
  
 Объект **строка** содержащее инструкцию SQL.  
  
 *nType*  
  
 **Int** , указывающее тип результирующего набора.  
  
 *nConcur*  
  
 **Int** , указывающее тип параллелизма результирующего набора.  
  
 *nHold*  
  
 **Int** , указывающее возможность сохранения результирующего набора.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект CallableStatement.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод prepareCall указывается с помощью метода prepareCall в интерфейсе java.sql.Connection.  
  
## <a name="see-also"></a>См. также:  
 [Метод prepareCall &#40; SQLServerConnection &#41;](../../../connect/jdbc/reference/preparecall-method-sqlserverconnection.md)   
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
