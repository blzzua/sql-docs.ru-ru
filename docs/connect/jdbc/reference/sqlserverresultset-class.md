---
title: "Класс SQLServerResultSet | Документы Microsoft"
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
ms.assetid: eaffcff1-286c-459f-83da-3150778480c9
caps.latest.revision: "17"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 254aa0bfb009eb852656ca62c4cba19fc8a03e39
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="sqlserverresultset-class"></a>Класс SQLServerResultSet
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Представляет результирующий набор JDBC.  
  
 **Пакет:** com.microsoft.sqlserver.jdbc  
  
 **Реализует:** [ISQLServerResultSet](../../../connect/jdbc/reference/isqlserverresultset-interface.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final class SQLServerResultSet  
```  
  
## <a name="remarks"></a>Замечания  
 Существует два типа результирующих наборов: на стороне клиента и на стороне сервера.  
  
 Результирующие наборы на стороне клиента используются в случае, если результаты могут быть размещены в памяти клиента. Эти результаты обеспечивают наибольшую производительность и считываются при [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] полностью из базы данных. Эти результирующие наборы не вводят дополнительную нагрузку на базу данных, вызываемой в результате создания курсоров на стороне сервера. Однако данные типы результирующих наборов нельзя обновлять.  
  
 Результирующие наборы на стороне сервера используются в случае, если результаты не могут быть размещены в памяти клиента или существует необходимость обновления результирующего набора. Для данного типа результирующего набора драйвер JDBC создает курсор на стороне сервера и, незаметно для пользователя, извлекает строки результирующего набора по мере того, как он выполняет прокрутку результатов.  
  
 Класс SQLServerResultSet предоставляет множество методов, которые позволяют обновить результирующий набор с любым собственным типом данных Java и множеством типов объектов Java.  
  
 Этот класс поддерживает развертывание в класс SQLServerResultSet, ISQLServerResultSet, интерфейс и интерфейс java.sql.ResultSet. Дополнительные сведения см. в разделе [оболочки и интерфейсы](../../../connect/jdbc/wrappers-and-interfaces.md).  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Справочник по API для драйвера JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
