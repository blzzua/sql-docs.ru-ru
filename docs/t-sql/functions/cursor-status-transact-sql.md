---
title: "CURSOR_STATUS (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CURSOR_STATUS
- CURSOR_STATUS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- status information [SQL Server], cursors
- CURSOR_STATUS function
- cursors [SQL Server], status information
ms.assetid: 3a4a840e-04f8-43bd-aada-35d78c3cb6b0
caps.latest.revision: 37
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e88dd4f14d8bd6fc90c40df101bfd9b2895bf229
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="cursorstatus-transact-sql"></a>CURSOR_STATUS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Скалярная функция, позволяющая при вызове хранимой процедуры определить, вернула ли она курсор и результирующий набор для данного параметра.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
CURSOR_STATUS   
     (  
          { 'local' , 'cursor_name' }   
          | { 'global' , 'cursor_name' }   
          | { 'variable' , 'cursor_variable' }   
     )  
```  
  
## <a name="arguments"></a>Аргументы  
'local'  
Константа, показывающая, что источник курсора — это имя локального курсора.
  
"*cursor_name*"  
Имя курсора. Имя курсора должно соответствовать требованиям, предъявляемым к идентификаторам.
  
'global'   
Константа, показывающая, что источник курсора — это имя глобального курсора.
  
'variable'   
Константа, показывающая, что источник курсора — это локальная переменная.
  
"*cursor_variable*"  
Имя переменной курсора. Переменная курсора должна быть определена с **курсор** тип данных.
  
## <a name="return-types"></a>Возвращаемые типы
**smallint**
  
|Возвращаемое значение|Имя курсора|Переменная курсора|  
|---|---|---|
|1|Результирующий набор курсора включает как минимум одну строку.<br /><br /> В случае статических и управляемых набором ключей курсоров результирующий набор включает как минимум одну строку.<br /><br /> В случае динамических курсоров результирующий набор может включать одну или более строк или не включать их.|Курсор, выделенный этой переменной, открыт.<br /><br /> В случае статических и управляемых набором ключей курсоров результирующий набор включает как минимум одну строку.<br /><br /> В случае динамических курсоров результирующий набор может включать одну или более строк или не включать их.|  
|0|Результирующий набор курсора пуст.*|Курсор, выделенный этой переменной, открыт, но результирующий набор пуст.*|  
|-1|Курсор закрыт.|Курсор, выделенный этой переменной, закрыт.|  
|-2|Неприменимо.|Возможны следующие варианты:<br /><br /> ранее вызванная процедура не назначила этой переменной с аргументом OUTPUT никакой курсор;<br /><br /> ранее вызванная процедура назначила этой переменной с аргументом OUTPUT курсор, но при завершении процедуры он находился в закрытом состоянии. Таким образом, курсор освобождается и не возвращается вызвавшей процедуре.<br /><br /> Объявленной переменной курсора никакой курсор не назначен.|  
|–3|Курсор с указанным именем не существует.|Переменная курсора с указанным именем не существует или существует, но ей еще не выделен курсор.|  
  
*Динамические курсоры никогда не возвращают этот результат.
  
## <a name="examples"></a>Примеры  
В следующем примере используется функция `CURSOR_STATUS` для отображения состояния курсора до и после его открытия и закрытия.
  
```sql
CREATE TABLE #TMP  
(  
   ii int  
)  
GO  
  
INSERT INTO #TMP(ii) VALUES(1)  
INSERT INTO #TMP(ii) VALUES(2)  
INSERT INTO #TMP(ii) VALUES(3)  
  
GO  
  
--Create a cursor.  
DECLARE cur CURSOR  
FOR SELECT * FROM #TMP  
  
--Display the status of the cursor before and after opening  
--closing the cursor.  
  
SELECT CURSOR_STATUS('global','cur') AS 'After declare'  
OPEN cur  
SELECT CURSOR_STATUS('global','cur') AS 'After Open'  
CLOSE cur  
SELECT CURSOR_STATUS('global','cur') AS 'After Close'  
  
--Remove the cursor.  
DEALLOCATE cur  
  
--Drop the table.  
DROP TABLE #TMP  
  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
`After declare`
  
`---------------`
  
 `-1`  
  
`After Open`
  
`----------`
  
 `1`  
  
`After Close`
  
`-----------`
  
 `-1`  
  
## <a name="see-also"></a>См. также:
[Функции работы с курсорами &#40; Transact-SQL &#41;](../../t-sql/functions/cursor-functions-transact-sql.md)  
[Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)
  
  
