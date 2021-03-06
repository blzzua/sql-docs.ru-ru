---
title: "Пример диагностики на основе файла драйвера | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- file-based driver diagnostic [ODBC]
- diagnostic information [ODBC], examples
- error messages [ODBC], diagnostic messages
ms.assetid: 0575fccd-4641-478d-a3cc-5a764e35bae2
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c8b4fab8c7d39acbffc73959ec06adb830716003
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="file-based-driver-diagnostic-example"></a>Пример диагностики на основе файла драйвера
Драйвер файловой действует и как драйвер ODBC, так и в качестве источника данных. Таким образом создается ошибок и предупреждений в качестве компонента из соединений ODBC и в качестве источника данных. Поскольку это компонент, который взаимодействует с диспетчером драйверов, он форматирует и возвращает аргументы для **SQLGetDiagRec**.  
  
 Например, если драйвер Microsoft® dBASE не удалось выделить достаточный объем памяти, могут возвращать следующие значения из **SQLGetDiagRec**:  
  
```  
SQLSTATE:         "HY001"  
Native Error:      42052  
Diagnostic Msg:   "[Microsoft][ODBC dBASE Driver]Unable to allocate sufficient memory."  
```  
  
 Так как эта ошибка не была связана с источником данных, драйвер добавлен только префиксы диагностическое сообщение для поставщика ([Microsoft]) и драйвер ([ODBC драйвера dBASE]).  
  
 Если драйвер не удалось найти файл Employee.dbf, он может возвращать следующие значения из **SQLGetDiagRec**:  
  
```  
SQLSTATE:         "42S02"  
Native Error:      -1305  
Diagnostic Msg:   "[Microsoft][ODBC dBASE Driver][dBASE]No such table or object"  
```  
  
 Поскольку эта ошибка была связана с источником данных, драйвер добавляются в формат файла источника данных ([dBASE]) как префикс диагностическое сообщение. Драйвер также использовался компонента, сопряженный с источником данных, он добавлен префиксов для поставщика ([Microsoft]) и драйвер ([ODBC драйвера dBASE]).
