---
title: "SQLDescribeCol | Документы Microsoft"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-api
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLDescribeCol function
ms.assetid: ffbf34c6-8268-434f-829a-82009a6cda59
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 06d4431256c20928a053f8d913b961bb38c99409
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2018
---
# <a name="sqldescribecol"></a>SQLDescribeCol
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Для выполненных инструкций [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента не требуется опрашивать сервер для описания столбцов результирующего набора. В этом случае **SQLDescribeCol** не приводит к обращению к серверу. Как [SQLColAttribute](../../relational-databases/native-client-odbc-api/sqlcolattribute.md)и[SQLNumResultCols](../../relational-databases/native-client-odbc-api/sqlnumresultcols.md), вызов **SQLDescribeCol** для подготовленных, но не выполненных инструкций приводит к обращению к серверу.  
  
 Когда инструкция [!INCLUDE[tsql](../../includes/tsql-md.md)] или пакет инструкций возвращает несколько результирующих наборов строк, то столбец, на который ссылается исходный столбец, можно создать в отдельной таблице или сослаться на абсолютно другой столбец результирующего набора. **SQLDescribeCol** должен вызываться для каждого набора. При изменении результирующего набора приложение должно осуществить повторную привязку значений данных перед выборкой результатов строк. Дополнительные сведения об обработке несколько результирующих наборов возвращает см. в разделе [SQLMoreResults](../../relational-databases/native-client-odbc-api/sqlmoreresults.md).  
  
 Когда несколько результирующих наборов формируется подготовленным пакетом инструкций SQL, атрибуты столбцов сообщаются только для первого результирующего набора.  
  
 Для типов данных больших значений, значение, возвращаемое в *DataTypePtr* SQL_VARCHAR, SQL_VARBINARY или SQL_NVARCHAR. Значение SQL_SS_LENGTH_UNLIMITED в *ColumnSizePtr* указывает, что размер «unlimited».  
  
 Усовершенствования в компоненте database engine, начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] разрешить SQLDescribeCol получать более точные описания ожидаемых результатов. Эти более точные результаты могут отличаться от значения, возвращаемые методом SQLDescribeCol в предыдущих версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в разделе [Metadata Discovery](../../relational-databases/native-client/features/metadata-discovery.md).  
  
## <a name="sqldescribecol-support-for-enhanced-date-and-time-features"></a>Поддержка функцией SQLDescribeCol улучшенных возможностей работы с данными в формате даты-времени  
 Для типов даты-времени возвращаются следующие значения.  
  
||*DataTypePtr*|*ColumnSizePtr*|*DecimalDigitsPtr*|  
|-|-------------------|---------------------|------------------------|  
|datetime|SQL_TYPE_TIMESTAMP|23|3|  
|smalldatetime|SQL_TYPE_TIMESTAMP|16|0|  
|date|SQL_TYPE_DATE|10|0|  
|time|SQL_SS_TIME2|8, 10..16|0..7|  
|datetime2|SQL_TYPE_TIMESTAMP|19, 21..27|0..7|  
|datetimeoffset|SQL_SS_TIMESTAMPOFFSET|26, 28..34|0..7|  
  
 Дополнительные сведения см. в разделе [даты и времени усовершенствования &#40; ODBC &#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqldescribecol-support-for-large-clr-udts"></a>Поддержка функцией SQLDescribeCol определяемых пользователем типов больших данных CLR  
 **SQLDescribeCol** поддерживает большие определяемые пользователем типы (UDT). Дополнительные сведения см. в разделе [Large CLR User-Defined типы &#40; ODBC &#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>См. также  
 [SQLDescribeCol, функция](http://go.microsoft.com/fwlink/?LinkID=59338)   
 [Сведения о реализации API-интерфейса ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
