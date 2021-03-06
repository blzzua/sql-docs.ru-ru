---
title: "Операторы сравнения (Transact-SQL) | Документы Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- expressions [SQL Server], testing
- operators [Transact-SQL], comparison
- testing expressions
- Boolean data type
- Boolean expressions
- comparing expressions
- comparison operators [SQL Server]
ms.assetid: b0cc68ef-3029-484c-a917-0c15dcbc230d
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Active
ms.openlocfilehash: cd8dcf23064d6caae62d10065c9aa3731823e99b
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="comparison-operators-transact-sql"></a>Операторы сравнения (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Операторы сравнения позволяют проверить, одинаковы ли два выражения. Операторы сравнения можно применять ко всем выражениям, за исключением выражений типов **text**, **ntext** и **image**. Операторы сравнения [!INCLUDE[tsql](../../includes/tsql-md.md)] приведены в следующей таблице:  
  
|Оператор|Значение|  
|--------------|-------------|  
|[= (равно)](../../t-sql/language-elements/equals-transact-sql.md)|Равно|  
|[> (больше)](../../t-sql/language-elements/greater-than-transact-sql.md)|Больше чем|  
|[< (меньше)](../../t-sql/language-elements/less-than-transact-sql.md)|Меньше чем|  
|[>= (больше или равно)](../../t-sql/language-elements/greater-than-or-equal-to-transact-sql.md)|Больше или равно|  
|[<= (меньше или равно)](../../t-sql/language-elements/less-than-or-equal-to-transact-sql.md)|Меньше или равно|  
|[<> (не равно)](../../t-sql/language-elements/not-equal-to-transact-sql-traditional.md)|Не равно|  
|[!= (не равно)](../../t-sql/language-elements/not-equal-to-transact-sql-exclamation.md)|Не равно (не определено стандартом ISO)|  
|[!< (не меньше)](../../t-sql/language-elements/not-less-than-transact-sql.md)|Не меньше (не определено стандартом ISO)|  
|[!> (не больше чем)](../../t-sql/language-elements/not-greater-than-transact-sql.md)|Не больше (не определено стандартом ISO)|  
  
## <a name="boolean-data-type"></a>Тип данных Boolean  
 Результат выполнения оператора сравнения имеет тип данных **Boolean**. Он имеет три значения: TRUE, FALSE и UNKNOWN. Выражения, возвращающие значения типа **Boolean**, называются логическими.  
  
 В отличие от других типов данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], тип **Boolean** не может быть типом столбца таблицы или переменной и не может быть возвращен в результирующем наборе.  
  
 Если параметр SET ANSI_NULLS имеет значение ON, оператор, в число операндов которого входит хотя бы одно выражение NULL, возвращает UNKNOWN. Когда параметр SET ANSI_NULLS имеет значение OFF, действуют те же правила, однако если оба выражения равны NULL, то оператор равенства (=) возвращает TRUE. Например, если параметр SET ANSI_NULLS имеет значение OFF, при обработке выражения NULL = NULL будет возвращено TRUE.  
  
 Выражения со значениями типа **Boolean** используются в предложении WHERE для фильтрации строк, удовлетворяющих условиям поиска, и в инструкциях языка управления потоком, таких как IF и WHILE, например:  
  
```  
-- Uses AdventureWorks  
  
DECLARE @MyProduct int;  
SET @MyProduct = 750;  
IF (@MyProduct <> 0)  
   SELECT ProductID, Name, ProductNumber  
   FROM Production.Product  
   WHERE ProductID = @MyProduct;  
```  
  
## <a name="see-also"></a>См. также:  
 [Выражения (Transact-SQL)](../../t-sql/language-elements/expressions-transact-sql.md)  
 [Операторы (Transact-SQL)](../../t-sql/language-elements/operators-transact-sql.md)  
  
  
