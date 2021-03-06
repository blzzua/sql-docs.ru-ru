---
title: "Метод updateBytes (SQLServerResultSet) | Документы Microsoft"
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
apiname: SQLServerResultSet.updateBytes
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 3050c836-fbb3-4475-99e5-05637a48a932
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 347f9eda7315ee112eaa09709fb2ef3d8c9eb513
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="updatebytes-method-sqlserverresultset"></a>Метод updateBytes (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Обновляет указанный столбец с массивом **байтов** значения.  
  
## <a name="overload-list"></a>Список перегрузок  
  
|Имя|Description|  
|----------|-----------------|  
|[updateBytes (int, byte &#91; &#93;)](../../../connect/jdbc/reference/updatebytes-method-int-byte.md)|Обновляет указанный столбец с массивом **байтов** значения заданному индексу столбца.|  
|[updateBytes (java.lang.String, byte &#91; &#93;)](../../../connect/jdbc/reference/updatebytes-method-java-lang-string-byte.md)|Обновляет указанный столбец с массивом **байтов** значения заданному имени столбца.|  
  
## <a name="remarks"></a>Замечания  
 В предыдущей версии [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)], можно использовать SQLServerResultSet.updateBytes для преобразования значений между массивами байтов и [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] тип данных **даты**, **время**,  **datetime2**, или **datetimeoffset**. Теперь при вызове этого метода с такими типами данных возникает исключение, указывающее, что такое преобразование не поддерживается.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
