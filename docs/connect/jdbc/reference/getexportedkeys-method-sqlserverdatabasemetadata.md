---
title: "Метод getExportedKeys (SQLServerDatabaseMetaData) | Документы Microsoft"
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
apiname: SQLServerDatabaseMetaData.getExportedKeys
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 26888e61-b243-4a1b-922c-c0a451dcff4d
caps.latest.revision: "15"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 78a2ace3784458d21546379f7073091832af1496
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="getexportedkeys-method-sqlserverdatabasemetadata"></a>Метод getExportedKeys (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает описание столбцов внешнего ключа, который ссылается на столбцы первичного ключа заданной таблицы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.ResultSet getExportedKeys(java.lang.String cat,  
                                          java.lang.String schema,  
                                          java.lang.String table)  
```  
  
#### <a name="parameters"></a>Параметры  
 *CAT*  
  
 Объект **строка** , содержащее имя каталога.  
  
 *схемы*  
  
 Объект **строка** , содержащее имя схемы.  
  
 *table*  
  
 Объект **строка** , содержащее имя таблицы.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getExportedKeys указывается с помощью метода getExportedKeys в интерфейсе java.sql.DatabaseMetaData.  
  
 Метод getExportedKeys возвращает результирующий набор будет содержать следующие сведения:  
  
|Имя|Тип|Description|  
|----------|----------|-----------------|  
|PKTABLE_CAT|**Строковые значения**|Имя каталога, содержащего таблицу первичного ключа.|  
|PKTABLE_SCHEM|**Строковые значения**|Имя схемы таблицы первичного ключа.|  
|PKTABLE_NAME|**Строковые значения**|Имя таблицы первичного ключа.|  
|PKCOLUMN_NAME|**Строковые значения**|Имя столбца первичного ключа.|  
|FKTABLE_CAT|**Строковые значения**|Имя каталога, содержащего таблицу внешнего ключа.|  
|FKTABLE_SCHEM|**Строковые значения**|Имя схемы таблицы внешнего ключа.|  
|FKTABLE_NAME|**Строковые значения**|Имя таблицы внешнего ключа.|  
|FKCOLUMN_NAME|**Строковые значения**|Имя столбца внешнего ключа.|  
|KEY_SEQ|**короткий**|Порядковый номер столбца в первичном ключе из нескольких столбцов.|  
|UPDATE_RULE|**короткий**|Действие, применяемое к внешнему ключу, если операцией SQL является операция обновления. Может иметь одно из следующих значений.<br /><br /> importedKeyNoAction (3)<br /><br /> importedKeyCascade (0)<br /><br /> importedKeySetNull (2)<br /><br /> importedKeySetDefault (4)<br /><br /> importedKeyRestrict (1)|  
|DELETE_RULE|**короткий**|Действие, применяемое к внешнему ключу, если операцией SQL является операция удаления. Может иметь одно из следующих значений.<br /><br /> importedKeyNoAction (3)<br /><br /> importedKeyCascade (0)<br /><br /> importedKeySetNull (2)<br /><br /> importedKeySetDefault (4)<br /><br /> importedKeyRestrict (1)|  
|FK_NAME|**Строковые значения**|Имя внешнего ключа.|  
|PK_NAME|**Строковые значения**|Имя первичного ключа.|  
|DEFERRABILITY|**короткий**|Указывает, можно ли отложить вычисление ограничения внешнего ключа до фиксации. Может иметь одно из следующих значений.<br /><br /> importedKeyInitiallyDeferred (5)<br /><br /> importedKeyInitiallyImmediate (6)<br /><br /> importedKeyNotDeferrable (7)|  
  
> [!NOTE]  
>  Дополнительные сведения о данных, возвращаемых методом getExportedKeys см. в разделе «sp_fkeys (Transact-SQL)» в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] электронной документации.  
  
## <a name="example"></a>Пример  
 Ниже приведен пример, как использовать метод getExportedKeys для возврата сведений обо всех внешних ключах, которые ссылаются на первичные ключи таблицы Person.Contact в [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)] образца базы данных.  
  
```  
public static void executeGetExportedKeys(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getExportedKeys("AdventureWorks", "Person", "Contact");  
      ResultSetMetaData rsmd = rs.getMetaData();  
  
      // Display the result set data.  
      int cols = rsmd.getColumnCount();  
      while(rs.next()) {  
         for (int i = 1; i <= cols; i++) {  
            System.out.println(rs.getString(i));  
         }  
      }  
      rs.close();  
   }   
  
   catch (Exception e) {  
      e.printStackTrace();  
   }  
}  
```  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
