---
title: "Метод setPortNumber (SQLServerDataSource) | Документы Microsoft"
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
apiname: SQLServerDataSource.setPortNumber
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 59c5fa23-bc1a-4142-af17-70e275f0b833
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6043aa18dd884c593c12cb4badbd78a9dda637f8
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="setportnumber-method-sqlserverdatasource"></a>Метод setPortNumber (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает номер порта, используемый для связи с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setPortNumber(int portNumber)  
```  
  
#### <a name="parameters"></a>Параметры  
 *номер_порта*  
  
 **Int** значение, содержащее номер порта.  
  
## <a name="remarks"></a>Замечания  
 Номер порта — номер порта TCP/IP, используемый при открытии подключения к сокету [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]. Если свойство portNumber не задано, [getPortNumber](../../../connect/jdbc/reference/getportnumber-method-sqlserverdatasource.md) метод возвращает значение по умолчанию 1433.  
  
> [!NOTE]  
>  Метод setPortNumber не выполняет проверку диапазона для переданное значение порта. Можно передать номер порта, который является недопустимым, например 99999, не вызовет ошибку.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
