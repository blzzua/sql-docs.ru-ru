---
title: "Метод setNClob (java.lang.String, java.io.Reader) | Документы Microsoft"
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
ms.assetid: a595679a-89b7-4b18-9ad2-d9cb13af2a28
caps.latest.revision: "15"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f5052aa87b787754e1d331bdcc6da4bf36a359a0
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="setnclob-method-javalangstring-javaioreader"></a>Метод setNClob (java.lang.String, java.io.Reader)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Присваивает указанному параметру указанный объект модуля чтения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final void setNClob(java.lang.String parameterName,  
              java.io.Reader reader)  
```  
  
#### <a name="parameters"></a>Параметры  
 *Имя_параметра*  
  
 Объект **строка** , содержащее имя параметра.  
  
 *Модуль чтения*  
  
 Объект модуля чтения.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод следует использовать для **NCHAR**, **NVARCHAR**, **NTEXT**, и **XML** типы данных параметров.  
  
 Этот метод setNClob указывается с помощью метода setNClob в интерфейсе java.sql.CallableStatement.  
  
## <a name="see-also"></a>См. также:  
 [Метод setNClob &#40; SQLServerCallableStatement &#41;](../../../connect/jdbc/reference/setnclob-method-sqlservercallablestatement.md)   
 [Элементы SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  
