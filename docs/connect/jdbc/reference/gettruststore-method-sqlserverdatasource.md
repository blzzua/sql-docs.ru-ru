---
title: "Метод getTrustStore (SQLServerDataSource) | Документы Microsoft"
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
apiname: getTrustStore Method (SQLServerDataSource)
apilocation: getTrustStore Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: 8f5850e4-8627-49a8-ba0e-b1f4014322a5
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: bbff42d43e1bc07dcb163234cab70fcdd9d0582f
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="gettruststore-method-sqlserverdatasource"></a>Метод getTrustStore (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает путь к файлу сертификата trustStore (включая имя файла).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.lang.String getTrustStore()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект **строка** , содержащий путь (включая имя файла) к файлу сертификата trustStore, или значение null, если значение не задано.  
  
## <a name="remarks"></a>Замечания  
 Если свойство trustStore не задано, [getTrustStore](../../../connect/jdbc/reference/gettruststore-method-sqlserverdatasource.md) метод возвращает значение null.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
