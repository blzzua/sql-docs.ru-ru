---
title: "ORDER BY-список выражений | Документы Microsoft"
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
- ORDER BY clause [ODBC]
- SQL grammar [ODBC], order by clause
ms.assetid: 5ef88186-a99f-4e2c-a3f3-98a42d4f03a5
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9a42adc746cac2cf701cc3e02c95bcaf6e883277
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="order-by-expression-list"></a>ORDER BY-список выражений
Выражения могут использоваться в предложении ORDER BY. Например, в следующих предложениях Таблица упорядочена по три ключевых выражений: a + b, c + d и e.  
  
```  
SELECT * FROM emp  
ORDER BY a+b,c+d,e  
```  
  
 Порядок не разрешена для набора функции или выражения, содержащего функцию set.
