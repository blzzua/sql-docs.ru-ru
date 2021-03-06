---
title: "Типы приложений | Документы Microsoft"
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
- upgrading applications [ODBC], application types
- backward compatibility [ODBC], application and driver compatibility
- compatibility [ODBC], application and driver compatibility
- application upgrades [ODBC], application types
- application compatibility issues [ODBC]
ms.assetid: d346a64e-a32c-4153-a40f-5b53c2f57ef2
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4c84327d23fba9b97bb34ff290eff06704e586df
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="types-of-applications"></a>Типы приложений
Приложения ODBC можно классифицировать следующим образом:  
  
-   **Чистые ODBC 2.**  
     ***x* приложения** 32-разрядное приложение:  
  
    -   Вызывает только ODBC 2. *x* функции (включая функцию ODBC 1.0 **SQLSetParam**). К ним относятся ODBC 1. *x* приложений, которые были перенесены с 32-разрядным.  
  
    -   Ожидает ODBC 2. *x* поведением для функций, для которых изменения поведения. (См. [изменения поведения](../../../odbc/reference/develop-app/behavioral-changes.md) подробнее.)  
  
    -   Не были перекомпилированы с заголовками ODBC 3.5.  
  
-   **Чистые ODBC 2.**  
     ***x* повторной компиляции приложения** чисто ODBC 2. *x* приложение, которое были перекомпилированы с помощью ODBC 3.5 файлы заголовков, задав аргумент ODBCVER = 0x0250.  
  
-   **Чистые ODBC 2.**  
     ***x* Unicode в приложении** чисто ODBC 2. *x* повторной компиляции приложения, которая совместима с Юникодом и использует тип данных SQL_WCHAR.  
  
-   **Чистые Open Group и ISO**—**приложений, совместимых с ODBC** 32-разрядное приложение:  
  
    -   Вызов функции, определенные в стандартах Open Group или ISO CLI. (Эти функции могут содержать устаревшие функции 3.0).  
  
    -   Не используйте типы данных Юникода.  
  
    -   Ожидает, что поведение ODBC 3.0 для компонентов, для которых изменения поведения.  
  
-   **Чистые приложения ODBC 3.0** 32-разрядное приложение:  
  
    -   Компилируется с заголовками 3.0.  
  
    -   Вызывает любая функция ODBC 3.0, возможно, включая те, которые являются устаревшими.  
  
    -   Ожидает, что поведение ODBC 3.0 для компонентов, для которых изменения поведения.  
  
-   **Чистые приложения ODBC 3.5** 32 или 64-разрядного приложения:  
  
    -   Может использовать типы данных Юникода.  
  
    -   Вызывает любая функция ODBC 3.5, возможно, включая те, которые являются устаревшими.  
  
    -   Ожидает, что поведение ODBC 3.5 для компонентов, для которых изменения поведения.  
  
-   **Чистые ODBC 3.8 (или более поздней версии) приложения** 32-разрядное или 64-разрядных приложений:  
  
    -   Может использовать типы данных Юникода.  
  
    -   Вызывает любая функция ODBC 3.8, возможно, включая те, которые являются устаревшими.  
  
    -   Ожидает, что поведение ODBC 3.8 для компонентов, для которых изменения поведения.  
  
-   **Замена приложения** 32 или 64-разрядного приложения:  
  
    -   Реализует новые особенности поведения дублированных функций.  
  
    -   Использует новые функции в более поздней версии ODBC, только в пределах условного кода.  
  
    -   Ограничено условного код для обработки изменения поведения или зарегистрировался быть более ранней версии приложения ODBC.
