---
title: "Метод nativeSQL (SQLServerConnection) | Документы Microsoft"
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
apiname: SQLServerConnection.nativeSQL
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 2188a6e1-792f-47bd-b207-1d01741231b2
caps.latest.revision: "14"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b78fd5757d79f5a4f89b3b0e5bc8292d47d78cc2
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="nativesql-method-sqlserverconnection"></a>Метод nativeSQL (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Преобразовывает заданную инструкцию SQL в соответствии с грамматикой SQL сервера базы данных.  
  
> [!NOTE]  
>  Этот метод не поддерживается в настоящее время [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.lang.String nativeSQL(java.lang.String sql)  
```  
  
#### <a name="parameters"></a>Параметры  
 *SQL*  
  
 Объект **строка** содержащее инструкцию SQL.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект **строка** содержащее преобразованную инструкцию SQL.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод nativeSQL указывается с помощью метода nativeSQL в интерфейсе java.sql.Connection.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
