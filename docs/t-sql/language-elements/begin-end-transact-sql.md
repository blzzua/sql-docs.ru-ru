---
title: "BEGIN... END (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- BEGIN
- BEGIN_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- enclosing statements [SQL Server]
- BEGIN statement
- control-of-flow language [SQL Server], BEGIN...END statement
- BEGIN...END keyword
- grouping statements, BEGIN...END statement
- executing Transact-SQL statements together [SQL Server]
- statements [SQL Server], grouping
ms.assetid: fc2c7f76-f1f9-4f91-beef-bc8ef0da2feb
caps.latest.revision: 30
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1045a89eb41a7f84b4b2a2a5cbe305c67e776fb1
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="beginend-transact-sql"></a>BEGIN...END (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Включает в себя последовательность инструкций языка [!INCLUDE[tsql](../../includes/tsql-md.md)], позволяя выполнять группу инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)]. Ключевые слова BEGIN и END относятся к языку потока управления.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
BEGIN  
    { sql_statement | statement_block }   
END  
```  
  
## <a name="arguments"></a>Аргументы  
 { *sql_statement* | *statement_block* }  
 Любая допустимая инструкция или группа инструкций языка [!INCLUDE[tsql](../../includes/tsql-md.md)], определенная с помощью блока инструкций.  
  
## <a name="remarks"></a>Замечания  
 Блоки BEGIN...END могут быть вложенными.  
  
 Хотя все инструкции языка [!INCLUDE[tsql](../../includes/tsql-md.md)] допустимы в пределах блока BEGIN...END, некоторые инструкции языка [!INCLUDE[tsql](../../includes/tsql-md.md)] не следует группировать в пределах одного пакета (блока инструкций).  
  
## <a name="examples"></a>Примеры  
 В следующем примере ключевые слова `BEGIN` и `END` определяют ряд инструкций языка [!INCLUDE[tsql](../../includes/tsql-md.md)], которые будут выполняться вместе. Если не включить блок `BEGIN...END`, будут выполнены оба оператора `ROLLBACK TRANSACTION` и возвращены оба сообщения `PRINT`.  
  
```  
USE AdventureWorks2012;  
GO  
BEGIN TRANSACTION;  
GO  
IF @@TRANCOUNT = 0  
BEGIN  
    SELECT FirstName, MiddleName   
    FROM Person.Person WHERE LastName = 'Adams';  
    ROLLBACK TRANSACTION;  
    PRINT N'Rolling back the transaction two times would cause an error.';  
END;  
ROLLBACK TRANSACTION;  
PRINT N'Rolled back the transaction.';  
GO  
/*  
Rolled back the transaction.  
*/  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 В следующем примере `BEGIN` и `END` определите ряд [!INCLUDE[DWsql](../../includes/dwsql-md.md)] инструкций, запускаемых одновременно. Если `BEGIN...END` блок не включаются, приведенный ниже будет непрерывно.  
  
```  
-- Uses AdventureWorks  
  
DECLARE @Iteration Integer = 0  
WHILE @Iteration <10  
BEGIN  
    SELECT FirstName, MiddleName   
    FROM dbo.DimCustomer WHERE LastName = 'Adams';  
SET @Iteration += 1  
END;  
  
```  
  
## <a name="see-also"></a>См. также:  
 [ALTER TRIGGER (Transact-SQL)](../../t-sql/statements/alter-trigger-transact-sql.md)   
 [Язык управления выполнением &#40; Transact-SQL &#41;](~/t-sql/language-elements/control-of-flow.md)   
 [CREATE TRIGGER (Transact-SQL)](../../t-sql/statements/create-trigger-transact-sql.md)   
 [КОНЕЦ &#40; BEGIN... КОНЕЦ &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/end-begin-end-transact-sql.md)  
  
  


