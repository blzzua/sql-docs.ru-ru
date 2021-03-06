---
title: "Метод getURL (SQLServerDatabaseMetaData) | Документы Microsoft"
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
apiname: SQLServerDatabaseMetaData.getURL
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: fcb66851-db5f-4ae8-b728-d129480b6f42
caps.latest.revision: "20"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: cbc569dbd45ede9429b6299e2f37d7f7a5cb269c
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="geturl-method-sqlserverdatabasemetadata"></a>Метод getURL (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает URL-адрес для этой базы данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.lang.String getURL()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект **строка** , содержащий URL-адрес.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getURL указывается с помощью метода getURL в интерфейсе java.sql.DatabaseMetaData.  
  
 При использовании [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] базы данных, этот метод возвращает **строка** значение, которое содержит следующие сведения:  
  
-   Значение URL-адреса — «jdbc:sqlserver://»  
  
-   Необязательные свойства подключения, таких как **serverName**, **instanceName**, и **номер_порта**  
  
-   Другие свойства подключения свойства пользователем, и все соединения с драйвером пустым или отличными от null значения по умолчанию, за исключением **userName**, **пароль**, и **integratedSecurity**.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
