---
title: "MONTH (Transact-SQL) | Документы Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- MONTH_TSQL
- MONTH
dev_langs:
- TSQL
helpviewer_keywords:
- values [SQL Server], date and time
- dates [SQL Server], functions
- month of year [SQL Server]
- date and time [SQL Server], MONTH
- dateparts [SQL Server], month
- functions [SQL Server], date and time
- dates [SQL Server], MONTH
- MONTH function [SQL Server]
ms.assetid: 9dd8aff7-b0fc-45df-b316-ead14ee9b8b7
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 9fff55128e9e5eda2d78646826ddeca2a25e6b56
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="month-transact-sql"></a>MONTH (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает целое число, представляющее месяц указанной даты *date*.  
  
 Обзор всех типов данных и функций даты и времени в языке [!INCLUDE[tsql](../../includes/tsql-md.md)] см. в статье [Типы данных и функции даты и времени (Transact-SQL)](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
MONTH ( date )  
```  
  
## <a name="arguments"></a>Аргументы  
 *date*  
 Выражение, которое можно привести к значению типа **time**, **date**, **smalldatetime**, **datetime**, **datetime2** или **datetimeoffset**. Аргумент *date* может быть выражением, выражением столбца, определяемой пользователем переменной или строковым литералом.  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 **int**  
  
## <a name="return-value"></a>Возвращаемое значение  
 Функция MONTH возвращает то же значение, что и функция [DATEPART](../../t-sql/functions/datepart-transact-sql.md) (**month**, *date*).  
  
 Если дата *date* содержит только компонент времени, возвращаемое значение равно 1, базовому месяцу.  
  
## <a name="examples"></a>Примеры  
 Следующая инструкция возвращает значение `4`. Порядковый номер месяца.  
  
```  
SELECT MONTH('2007-04-30T01:01:01.1234567 -07:00');  
```  
  
 Следующая инструкция возвращает значение `1900, 1, 1`. В качестве значения аргумента *date* задается число `0`. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] интерпретирует `0` как 1 января 1900 г.  
  
```  
SELECT YEAR(0), MONTH(0), DAY(0);  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 В приведенном ниже примере возвращается `4`. Порядковый номер месяца.  
  
```  
-- Uses AdventureWorks  
  
SELECT TOP 1 MONTH('2007-04-30T01:01:01.1234')   
FROM dbo.DimCustomer;  
```  
  
 В приведенном ниже примере возвращается `1900, 1, 1`. В качестве значения аргумента *date* задается число `0`. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] интерпретирует `0` как 1 января 1900 г.  
  
```  
-- Uses AdventureWorks  
  
SELECT TOP 1 YEAR(0), MONTH(0), DAY(0) FROM dbo.DimCustomer;  
```  
  
## <a name="see-also"></a>См. также:  
 [Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)  
  
  

