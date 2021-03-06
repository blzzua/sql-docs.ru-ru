---
title: "Метод isCurrency (SQLServerResultSetMetaData) | Документы Microsoft"
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
apiname: SQLServerResultSetMetaData.isCurrency
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 7fe25d90-693c-4d3b-9dd2-0f8351c5a9ed
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7b3138fc8d5e4b12c1144385d84d8c6ed564e50b
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="iscurrency-method-sqlserverresultsetmetadata"></a>Метод isCurrency (SQLServerResultSetMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Указывает, содержит ли указанный столбец значения денежных сумм.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean isCurrency(int column)  
```  
  
#### <a name="parameters"></a>Параметры  
 *столбец*  
  
 **Int** , указывающее индекс столбца.  
  
## <a name="return-value"></a>Возвращаемое значение  
 **значение true,** Если столбец имеет значение денежных сумм. В противном случае — **false**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод isCurrency указывается с помощью метода isCurrency в интерфейсе java.sql.ResultSetMetaData.  
  
 Этот метод будет возвращать **true** только с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] типов данных money и smallmoney.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-methods.md)   
 [Элементы SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-members.md)   
 [Класс SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)  
  
  
