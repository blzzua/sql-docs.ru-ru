---
title: "Метод getReference (SQLServerDataSource) | Документы Microsoft"
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
apiname: SQLServerDataSource.getReference
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: b3fb1a97-86ee-4977-adca-c35ae199dbb3
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a0d24fa8c02c24c8d35a031bf0e7b49c35b12424
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="getreference-method-sqlserverdatasource"></a>Метод getReference (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает ссылку на это [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public javax.naming.Reference getReference()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект ссылки.  
  
## <a name="remarks"></a>Замечания  
 Этот метод getReference указывается с помощью метода getReference в интерфейсе javax.naming.Referenceable.  
  
 До появления [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] версии 3.0 драйвера JDBC, если метод SQLServerDataSource.setTrustStorePassword вызывался в объекте SQLServerDataSource, пароль будет присутствовать в объекте, возвращаемом SQLServerDataSource.getReference, что объект, который будет использоваться для Создание дополнительных подключений. В версии 3.0 драйвера JDBC необходимо установить пароль для объекта, возвращаемого SQLServerDataSource.getReference, перед установлением соединения с объектом.  
  
 Кроме того, если SQLServerDataSource.setTrustStorePassword задается перед привязкой свойств источника данных, необходимо вызвать метод SQLServerDataSource.setTrustStorePassword перед получением соединения. Например:  
  
```  
ctx = new InitialContext(System.getProperties());  
  
SQLServerDataSource ds1 = (SQLServerDataSource) ctx.lookup(jndiName);  
  
ds1.setTrustStorePassword("XXXXX");  
Connection con = ds1.getConnection("user", "XXXXXX");  
  
ctx.rebind(jndiName, ds1);  
SQLServerDataSource ds2 = (SQLServerDataSource) ctx.lookup(jndiName);  
ds2.setTrustStorePassword("XXXXX");   // reset the truststore password  
con = ds2.getConnection("user", "XXXXXX");   // provide userid and password again  
```  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
