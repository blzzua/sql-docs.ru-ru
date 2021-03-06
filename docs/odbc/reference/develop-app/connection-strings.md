---
title: "Строки подключения | Документы Microsoft"
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
- data sources [ODBC], connection functions
- connecting to driver [ODBC], connection strings
- functions [ODBC], data source or driver connections
- connection strings [ODBC], about connection strings
- connecting to data source [ODBC], connection strings
- connecting to data source [ODBC], functions
- connecting to driver [ODBC], functions
- connection functions [ODBC]
- ODBC drivers [ODBC], connection functions
ms.assetid: 724c7b86-300a-4fa9-ad96-4afa0fdcb3e9
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3abf812d73f780533a77a42498bfde4c299996d5
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="connection-strings"></a>Строки соединения
Строка подключения содержит сведения, которые используются для установления подключения. Полная строка подключения содержит все сведения, необходимые для установления соединения. Строка подключения — это последовательность пар "ключевое слово значение", разделенных точкой с запятой. (Полный синтаксис строки соединения см. в разделе [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) описание функции.) Строка подключения используется:  
  
-   **SQLDriverConnect**, который завершает строку подключения, взаимодействие с пользователем.  
  
-   **SQLBrowseConnect**, которой завершается строка подключения итеративного с источником данных.  
  
 **SQLConnect** не использует строку подключения; с помощью **SQLConnect** является аналогом подключение с помощью строки подключения с ровно три пары ключ значение (имя источника данных, и при необходимости, пользователь идентификатор и пароль) .
