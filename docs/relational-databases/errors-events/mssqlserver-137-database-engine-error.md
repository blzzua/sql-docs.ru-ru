---
title: "MSSQLSERVER_137 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 137 (Database Engine error)
ms.assetid: 47fb4212-2165-4fec-bc41-6d548465d7be
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0c242db0377a97305c26e35b53e165346af87815
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver137"></a>MSSQLSERVER_137
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|137|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|P_SCALAR_VAR_NOTFOUND|  
|Текст сообщения|Должна быть объявлена скалярная переменная «%.*ls».|  
  
## <a name="explanation"></a>Объяснение  
Эта ошибка происходит, если переменная используется в скрипте SQL без предварительного объявления этой переменной. Следующий пример возвращает ошибку 137 для обеих инструкций (SET и SELECT), так как переменная **@mycol** не объявлена.  
  
SET @mycol = 'ContactName';  
  
SELECT @mycol;  
  
Одной из трудноуловимых причин этой ошибки является использование переменной, которая объявлена вне инструкции EXECUTE. Например, переменная **@mycol**, указанная в инструкции SELECT, является локальной по отношению к инструкции SELECT и поэтому находится вне инструкции EXECUTE.  
  
USE AdventureWorks2012;  
  
GO  
  
DECLARE @mycol nvarchar(20);  
  
SET @mycol = 'Name';  
  
EXECUTE ('SELECT @mycol FROM Production.Product;');  
  
## <a name="user-action"></a>Действие пользователя  
Убедитесь в том, что все переменные, используемые в скрипте SQL, объявляются перед их применением в любом месте скрипта.  
  
Перепишите скрипт так, чтобы в инструкции EXECUTE не применялись ссылки на переменные, которые объявлены вне этой инструкции. Например:  
  
USE AdventureWorks2012;  
  
GO  
  
DECLARE @mycol nvarchar(20) ;  
  
SET @mycol = 'Name';  
  
EXECUTE ('SELECT ' + @mycol + ' FROM Production.Product';) ;  
  
## <a name="see-also"></a>См. также:  
[EXECUTE (Transact-SQL)](~/t-sql/language-elements/execute-transact-sql.md)  
[Инструкции SET (Transact-SQL)](~/t-sql/statements/set-statements-transact-sql.md)  
[DECLARE @local_variable (Transact-SQL)](~/t-sql/language-elements/declare-local-variable-transact-sql.md)  
  
