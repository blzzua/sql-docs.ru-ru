---
title: "Метод getObject (java.lang.String) (SQLServerResultSet) | Документы Microsoft"
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
apiname: SQLServerResultSet.getObject (java.lang.String)
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 59a975e8-bea8-42fe-8f34-5f18f2bbd415
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: cd6012f7fd0a75941ca2a2be7d22052a6b1a92cb
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="getobject-method-javalangstring-sqlserverresultset"></a>Метод getObject (java.lang.String) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Получает значение имени заданного столбца в текущей строке [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта в виде объекта на языке программирования Java.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.lang.Object getObject(java.lang.String columnName)  
```  
  
#### <a name="parameters"></a>Параметры  
 *columnName*  
  
 Объект **строка** , содержащее имя столбца.  
  
## <a name="return-value"></a>Возвращаемое значение  
 **Объекта** значение.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getObject указывается с помощью метода getObject в интерфейсе java.sql.ResultSet.  
  
 Этот метод вернет значение данного столбца в виде объекта Java. Объект Java будет иметь заданный по умолчанию тип, соответствующий типу SQL Server столбца и сопоставленный встроенным типам, указанным в спецификации JDBC. Если значение SQL NULL, то драйвер вернет значение Java NULL.  
  
 Этот метод также может быть использован для чтения абстрактных типов данных, относящихся к базе данных. В JDBC 2.0 API возможности метода getObject расширены и поддерживают материализацию данных определяемых пользователем типов SQL. Если столбец содержит структурированное или уникальное значение, поведение данного метода является, как если бы он был вызов `getObject(columnIndex, this.getStatement().getConnection().getTypeMap())`.  
  
 Начиная с версии [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] драйвера JDBC 3.0:  
  
-   Значение типа date будет возвращаться в виде объекта java.sql.Date.  
  
-   Значение типа time будет возвращаться в виде объекта java.sql.Time.  
  
-   Значение типа datetime2 будет возвращаться в виде объекта java.sql.Timestamp.  
  
-   Значение типа datetimeoffset будет возвращаться в виде объекта microsoft.sql.DateTimeOffset.  
  
## <a name="see-also"></a>См. также:  
 [Метод getObject &#40; SQLServerResultSet &#41;](../../../connect/jdbc/reference/getobject-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
