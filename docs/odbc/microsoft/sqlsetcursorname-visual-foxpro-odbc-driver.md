---
title: "SQLSetCursorName (драйвер ODBC для Visual FoxPro) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLSetCursorName function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 2ac5a8b5-f084-405b-b0d7-546284dfa111
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 74410e39c16c2239471f3f2d328bf29a39dc7cec
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsetcursorname-visual-foxpro-odbc-driver"></a>SQLSetCursorName (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  Этот раздел содержит сведения по Visual FoxPro ODBC драйвера. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Поддержка: полный  
  
 Соответствия ODBC API: Уровень Core  
  
 Связывает имя курсора с дескриптором активный оператор, *hstmt*. **SQLSetCursorName** включается в API драйвера ODBC Visual FoxPro, так как он входит в состав функции API-интерфейса ODBC уровня ядра; его нельзя использовать с другими функциями API, драйвер поддерживает позиционированные обновления.  
  
 Дополнительные сведения см. в разделе [SQLSetCursorName](../../odbc/reference/syntax/sqlsetcursorname-function.md) в *справочнике программиста ODBC*.