---
title: "+ (унарный плюс) (Transact-SQL) | Документы Майкрософт"
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- Azure SQL Database
- SQL Server (starting with 2008)
f1_keywords:
- + (positive)
- +
- positive
dev_langs:
- TSQL
helpviewer_keywords:
- + (positive operator)
- positive operator (+)
- positive values [SQL Server]
ms.assetid: 0f31c5cc-3078-4f6a-9870-7eb1a98053fb
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: a6e211c1159d3f78e37226e8ad170ce84a7ce476
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="unary-operators---positive"></a>Унарные операторы — положительное значение
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает значение числового выражения (унарный оператор). Унарные операторы выполняют операцию только на одном выражении любого типа данных из категории числовых типов данных.   
  
|Оператор|Значение|  
|--------------|-------------|  
|[+ (положительное значение)](../../t-sql/language-elements/unary-operators-positive.md)|Числовое значение положительно.|  
|[- (отрицательное значение)](../../t-sql/language-elements/unary-operators-negative.md)|Числовое значение отрицательно.|  
|[~ (побитовое НЕ)](../../t-sql/language-elements/bitwise-not-transact-sql.md)|Возвращает поразрядное дополнение числа.|  
  
 Операторы + (знак «плюс») и - (знак «минус») можно использовать в любом выражении любого типа данных из категории числовых типов данных. Оператор ~ (побитовое НЕ) можно использовать только в выражениях любого типа данных из категории целочисленных типов данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
+ numeric_expression  
```  
  
## <a name="arguments"></a>Аргументы  
 *numeric_expression*  
 Любое допустимое выражение [expression](../../t-sql/language-elements/expressions-transact-sql.md) любого из типов данных категории числовых типов данных, кроме типов данных **datetime** и **smalldatetime**.  
  
## <a name="result-types"></a>Типы результата  
 Возвращает тип данных *numeric_expression*.  
  
## <a name="remarks"></a>Remarks  
 Хотя оператор унарного сложения может стоять перед любым числовым выражением, он не выполняет никаких действий со значением, полученным в результате вычисления выражения. В частности, оно не вернет положительное значение, если значение выражения отрицательно. Для получения положительного значения из отрицательного значения выражения предназначена функция [ABS](../../t-sql/functions/abs-transact-sql.md).  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-setting-a-variable-to-a-positive-value"></a>A. Присваивание переменной положительного значения  
 В следующем примере производится присваивание переменной положительного значения.  
  
```  
DECLARE @MyNumber decimal(10,2);  
SET @MyNumber = +123.45;  
SELECT @MyNumber;  
GO  
```  
  
 Результирующий набор:  
  
```  
-----------   
123.45            
  
(1 row(s) affected)  
```  
  
### <a name="b-using-the-unary-plus-operator-with-a-negative-value"></a>Б. Использование оператора «унарный плюс» с отрицательными значениями  
 Следующий пример показывает, как унарное сложение используется с отрицательными значениями и как с ними же используется функция ABS(). Функция ABS возвращает положительное значение выражения, а унарное сложение никак не влияет на него.  
  
```  
USE tempdb;  
GO  
DECLARE @Num1 int;  
SET @Num1 = -5;  
SELECT +@Num1, ABS(@Num1);  
GO  
```  
  
 Результирующий набор:  
  
```  
----------- -----------  
-5          5  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>См. также:  
 [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)   
 [Выражения (Transact-SQL)](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Операторы (Transact-SQL)](../../t-sql/language-elements/operators-transact-sql.md)   
 [ABS (Transact-SQL)](../../t-sql/functions/abs-transact-sql.md)  
  
  
