---
title: "Метод refreshRow (SQLServerResultSet) | Документы Microsoft"
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
apiname: SQLServerResultSet.refreshRow
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 048fe245-157f-4fd8-be75-ce54b83e02b3
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5f1a7c8a4a5381291d21f35adba178f05bc83f3f
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="refreshrow-method-sqlserverresultset"></a>Метод refreshRow (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Обновляет текущую строку, записывая последнее значение из базы данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void refreshRow()  
```  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод refreshRow указывается с помощью метода refreshRow в интерфейсе java.sql.ResultSet.  
  
 Этот метод не может быть вызван при нахождении курсора в строке вставки.  
  
 Этот метод обеспечивает для приложения способ явно указать драйверу JDBC на необходимость повторного извлечения строк из базы данных. Приложению может потребоваться вызвать этот метод при [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] кэшировании или выполнении повторного извлечения последнего значения строки из базы данных. Если размер выборки больше 1, драйвер JDBC может одновременно обновить несколько строк.  
  
 Все повторно извлеченные значения должны соответствовать уровню изоляции транзакции и чувствительности курсора. Если этот метод вызывается после вызова метода обновления, но перед вызовом метода [updateRow](../../../connect/jdbc/reference/updaterow-method-sqlserverresultset.md) , обновления, внесенные в строку, теряются. Вызов этого метода, вероятнее всего, приведет к снижению производительности.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
