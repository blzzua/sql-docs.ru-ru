---
title: "Метод getPrecision (SQLServerParameterMetaData) | Документы Microsoft"
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
apiname: SQLServerParameterMetaData.getPrecision
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 8bd79484-bab6-423b-978f-d7ec7132ebeb
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 24ae94a05a20750fbfb8b80a9ab905753070ecbb
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="getprecision-method-sqlserverparametermetadata"></a>Метод getPrecision (SQLServerParameterMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает число десятичных разрядов для указанного параметра.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public int getPrecision(int param)  
```  
  
#### <a name="parameters"></a>Параметры  
 *param*  
  
 **Int** , указывающее индекс параметра.  
  
## <a name="return-value"></a>Возвращаемое значение  
 **Int** , указывающее точность заданного параметра.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getPrecision указывается с помощью метода getPrecision в интерфейсе java.sql.ParameterMetaData.  
  
 Для числовых типов этот метод возвращает число десятичных разрядов. Для символьных типов он возвращает максимальную длину в символах. Для двоичных типов он возвращает максимальную длину в байтах. Если число разрядов неизвестно, этот метод возвращает значение 0.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerParameterMetaData](../../../connect/jdbc/reference/sqlserverparametermetadata-methods.md)   
 [Элементы SQLServerParameterMetaData](../../../connect/jdbc/reference/sqlserverparametermetadata-members.md)   
 [Класс SQLServerParameterMetaData](../../../connect/jdbc/reference/sqlserverparametermetadata-class.md)  
  
  
