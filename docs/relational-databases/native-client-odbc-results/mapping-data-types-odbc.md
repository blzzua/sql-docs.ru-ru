---
title: "Сопоставление типов данных (ODBC) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-results
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- mapping data types [ODBC]
- result sets [ODBC], data types
- ODBC data types, mapping
- SQL Server Native Client ODBC driver, result sets
- ODBC applications, result sets
- data types [ODBC], mapping
- sql_variant data type
- SQL Server Native Client ODBC driver, data types
ms.assetid: 4ba0924d-9fca-4c48-aced-0a8d817b3dde
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4f7d92d0580f7c56a17f1de332204622eee15948
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="mapping-data-types-odbc"></a>Сопоставление типов данных (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Maps драйвер ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] типов данных SQL в типы данных ODBC SQL. В последующих разделах обсуждаются типы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL с типами данных ODBC SQL, с которыми они сопоставляются. В разделах также обсуждаются типы данных ODBC SQL и соответствующие им типы данных ODBC C, а также поддерживаемые преобразования и преобразования по умолчанию.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Timestamp** типа данных аналогичному типу данных ODBC SQL_BINARY или SQL_VARBINARY, так как значения в **timestamp** столбцы не **datetime** значений, но **binary(8)** или **varbinary(8)** значения, которые определяют последовательность [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для строки. Если драйвер ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] встречает значение типа SQL_C_WCHAR (Юникод), что означает нечетное число байт, то последний нечетный байт усекается.  
  
## <a name="dealing-with-sqlvariant-data-type-in-odbc"></a>Работа с типом данных sql_variant в ODBC  
 **Sql_variant** столбец может содержать любой из типов данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , за исключением больших объектов (LOB), такие как **текст**, **ntext**, и  **изображение**. Например, столбец может содержать **smallint** значения для некоторых строк **float** значения в других строках и **char/nchar** значения в оставшейся.  
  
 **Sql_variant** тип данных аналогичен **Variant** Microsoft Visual Basic® типу данных.  
  
### <a name="retrieving-data-from-the-server"></a>Получение данных с сервера  
 ODBC отсутствует понятие типа variant, ограничить использование **sql_variant** тип данных с помощью драйвера ODBC в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], если привязка задана, **sql_variant** тип данных должен быть привязан к одному из документированных типов данных ODBC. **SQL_CA_SS_VARIANT_TYPE**, новый атрибут, относящиеся к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента возвращает тип данных экземпляра в **sql_variant** столбца для пользователя.  
  
 Если привязка не указана, [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md) функцию можно использовать для определения типа данных экземпляра в **sql_variant** столбца.  
  
 Для получения **sql_variant** данных выполните следующие действия.  
  
1.  Вызовите **SQLFetch** чтобы перейти к получаемой строке.  
  
2.  Вызовите **SQLGetData**, указав SQL_C_BINARY для данного типа и 0 для длины данных. Это заставит драйвер считать **sql_variant** заголовок. Этот заголовок содержит тип данных этого экземпляра в **sql_variant** столбца. **SQLGetData** возвращает размер (в байтах) значение.  
  
3.  Вызовите [SQLColAttribute](../../relational-databases/native-client-odbc-api/sqlcolattribute.md) , указав **SQL_CA_SS_VARIANT_TYPE** в качестве его значения атрибута. Эта функция возвращает тип данных C экземпляра в **sql_variant** столбца клиенту.  
  
 Фрагмент кода, демонстрирующий вышеуказанные шаги:  
  
```  
while ((retcode = SQLFetch (hstmt))==SQL_SUCCESS)  
{  
    if (retcode != SQL_SUCCESS && retcode != SQL_SUCCESS_WITH_INFO)  
    {  
        SQLError (NULL, NULL, hstmt, NULL,   
                    &lNativeError,szError,MAX_DATA,&sReturned);  
        printf_s ("%s\n",szError);  
        goto Exit;  
    }  
    retcode = SQLGetData (hstmt, 1, SQL_C_BINARY,   
                                pBuff,0,&Indicator);//Figure out the length  
    if (retcode != SQL_SUCCESS_WITH_INFO && retcode != SQL_SUCCESS)  
    {  
        SQLError (NULL, NULL, hstmt, NULL, &lNativeError,   
                    szError,MAX_DATA,&sReturned);  
        printf_s ("%s\n",szError);  
        goto Exit;  
    }  
    printf_s ("Byte length : %d ",Indicator); //Print out the byte length  
  
    int iValue = 0;  
    retcode = SQLColAttribute (hstmt, 1, SQL_CA_SS_VARIANT_TYPE, NULL,   
                                        NULL,NULL,&iValue);  //Figure out the type  
    printf_s ("Sub type = %d ",iValue);//Print the type, the return is C_type of the column]  
  
// Set up a new binding or do the SQLGetData on that column with   
// the appropriate type  
}  
```  
  
 Если пользователь создает привязку с помощью [SQLBindCol](../../relational-databases/native-client-odbc-api/sqlbindcol.md), драйвер считывает метаданные и данные. Затем драйвер преобразует данные к соответствующему типу ODBC, указанному в привязке.  
  
### <a name="sending-data-to-the-server"></a>Отправка данных на сервер  
 **SQL_SS_VARIANT**, новый тип данных для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента используется для данных, отправляемых **sql_variant** столбца. При отправке данных на сервер с помощью параметров (например, INSERT INTO имя_таблицы VALUES (?,?)), [SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md) используется для указания сведений о параметрах, включая тип C и соответствующий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] типа. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Драйвер ODBC собственного клиента будет преобразовать тип данных C в один из соответствующих **sql_variant** подтипы.  
  
## <a name="see-also"></a>См. также  
 [Результаты обработки &#40; ODBC &#41;](../../relational-databases/native-client-odbc-results/processing-results-odbc.md)  
  
  
