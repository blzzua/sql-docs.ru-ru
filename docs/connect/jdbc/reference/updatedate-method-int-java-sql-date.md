---
title: "Метод updateDate (int, java.sql.Date) | Документы Microsoft"
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
apiname: SQLServerResultSet.updateDate (int, java.sql.Date)
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: c5fb1292-a5cf-4cdd-8c4a-d1679944a6d0
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 96e1dea99c4e324ce20ce6e5b0457a93ea657116
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="updatedate-method-int-javasqldate"></a>Метод updateDate (int, java.sql.Date)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Обновляет указанный столбец значением даты по заданному индексу столбца.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void updateDate(int index,  
                       java.sql.Date x)  
```  
  
#### <a name="parameters"></a>Параметры  
 *Индекс*  
  
 **Int** , указывающее индекс столбца.  
  
 *x*  
  
 Значение даты.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод updateDate указывается с помощью метода updateDate в интерфейсе java.sql.ResultSet.  
  
## <a name="see-also"></a>См. также:  
 [Метод updateDate &#40; SQLServerResultSet &#41;](../../../connect/jdbc/reference/updatedate-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
