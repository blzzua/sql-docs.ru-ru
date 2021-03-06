---
title: "Метод updateBinaryStream (java.io.InputStream, int) | Документы Microsoft"
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
apiname: SQLServerResultSet.updateBinaryStream (java.lang.String, java.io.InputStream, int)
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 9be246a7-85fa-49fc-ad79-aabe97f5b280
caps.latest.revision: "21"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2c496b4b5b5123baacf7e79f0110d8cff9fa2c0b
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="updatebinarystream-method-javalangstring-javaioinputstream-int"></a>Метод updateBinaryStream (java.lang.String, java.io.InputStream, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Обновляет значение двоичного потока в указанном столбце, в котором указывается заданное число байтов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void updateBinaryStream(java.lang.String columnLabel,  
                               java.io.InputStream x,  
                               int length)  
```  
  
#### <a name="parameters"></a>Параметры  
 *ColumnLabel состоит из*  
  
 AStringthat содержит метку столбца.  
  
 *x*  
  
 Объект, InputStream.  
  
 *length*  
  
 **Int** , указывающее длину потока.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод updateBinaryStream указывается с помощью метода updateBinaryStream в интерфейсе java.sql.ResultSet.  
  
 Этот метод передает байты от объекта InputStream для выбранных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] двоичных столбцов, таких как binary, varbinary, varbinary(max), изображение, xml и определяемого пользователем типа. В этом методе не поддерживается обновление символьных столбцов. Чтобы обновить символьный столбец с InputStream, используйте [updateAsciiStream](../../../connect/jdbc/reference/updateasciistream-method-sqlserverresultset.md) метод.  
  
 Если длина потока отличается от указанной в *длина* параметра, драйвер JDBC вызовет исключение при обновлении или вставке строки.  
  
 Если длина потока неизвестна, *длина* параметра может быть задано значение -1, чтобы указать, что драйвер будет принимать потоки независимо от их длины. Для sqljdbc4.jar рекомендуется использовать метод JDBC 4.0 [updateBinaryStream метод &#40;java.lang.String, java.io.InputStream &#41;](../../../connect/jdbc/reference/updatebinarystream-method-java-lang-string-java-io-inputstream.md) Если приложению нужно обновлять столбец из потока, длина которого совпадает с Неизвестный.  
  
## <a name="see-also"></a>См. также:  
 [Метод updateBinaryStream &#40; SQLServerResultSet &#41;](../../../connect/jdbc/reference/updatebinarystream-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
