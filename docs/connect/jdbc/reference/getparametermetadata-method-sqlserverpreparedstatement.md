---
title: "Метод (SQLServerPreparedStatement) getParameterMetaData | Документы Microsoft"
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
apiname: SQLServerPreparedStatement.getParameterMetaData
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: c2876dec-ce29-4b61-9d74-ec3173b8cba5
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 730f30d3f810185defbfbababc85e49d63ae2ed4
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="getparametermetadata-method-sqlserverpreparedstatement"></a>getParameterMetaData метод (SQLServerPreparedStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Извлекает количество, типы и свойства параметров этого [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final java.sql.ParameterMetaData getParameterMetaData()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект [SQLServerParameterMetaData](../../../connect/jdbc/reference/sqlserverparametermetadata-class.md) объекта.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getParameterMetaData указывается с помощью метода getParameterMetaData в интерфейсе java.sql.PreparedStatement.  
  
## <a name="see-also"></a>См. также:  
 [Члены SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [Класс SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
