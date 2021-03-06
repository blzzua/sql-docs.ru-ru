---
title: Команды SET ANSI | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- set ANSI command [ODBC]
ms.assetid: cf9a01b2-14bf-458c-a73c-2a58ddef32d8
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ef87baef7367068b5a22225f3bb9b4c3e1783ca6
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="set-ansi-command"></a>Команды SET ANSI
Определяет способ между строки разной длины сравнения с =-оператор в командах Visual FoxPro SQL.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SET ANSI ON | OFF  
```  
  
## <a name="arguments"></a>Аргументы  
 ON  
 (По умолчанию для драйвера, значение по умолчанию для Visual FoxPro — OFF). Дополняет понадобится более короткие строки с пустые значения для упростить длина строки равно тем больше времени. Две строки, затем последовательно сравниваемых символов для символа для их всей длины. Рассмотрим это сравнение.  
  
```  
'Tommy' = 'Tom'  
```  
  
 Результат равен False (. Е.) Если SET ANSI имеет значение on, так как при заполнении «Tom» становится «Tom» и строки «Том» и «Антон» не соответствуют символ.  
  
 == Оператор использует этот метод для сравнения в команды Visual FoxPro SQL.  
  
 OFF  
 Указывает, не дополняются пробелами это более короткие строки. Сравниваются две строки символа для символов, пока не будет достигнут конец более короткие строки. Рассмотрим это сравнение.  
  
```  
'Tommy' = 'Tom'  
```  
  
 Результатом является значение True (. Если SET ANSI отключен, так как T.) процедура сравнения останавливается после «Tom».  
  
## <a name="remarks"></a>Remarks  
 SET ANSI определяет ли более короткой двух строк дополняется пробелы при сравнении строк SQL. SET ANSI не оказывает влияния на ==-оператор; При использовании оператора ==, более короткая строка дополняется всегда пустые значения для сравнения.  
  
## <a name="string-order"></a>Строка заказа  
 В командах SQL порядок слева направо между двумя строками в сравнении не irrelevantswitching строку с одной стороны, = или ==-оператор на другую не влияет на результат сравнения.  
  
## <a name="see-also"></a>См. также:  
 [ВЫБЕРИТЕ - команда SQL](../../odbc/microsoft/select-sql-command.md)   
 [Команда SET EXACT](../../odbc/microsoft/set-exact-command.md)
