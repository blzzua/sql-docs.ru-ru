---
title: "SQLGetTypeInfo (драйвера dBASE) | Документы Microsoft"
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
- SQLGetTypeInfo function [ODBC], dBASE Driver
- DBase driver [ODBC], SQLGetTypeInfo
ms.assetid: 6e9ce02b-97c7-4c1a-91e0-829df7459c84
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 791072c29eac366794b80869e2138c3aaffde56e
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="sqlgettypeinfo-dbase-driver"></a>SQLGetTypeInfo (драйвера dBASE)
> [!NOTE]  
>  В этом разделе сведения dBASE специфические для драйвера. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Имя типа (TYPE_NAME), возвращаемых в таблицу, полученных при **SQLGetTypeInfo** будет именем, наиболее часто используется в источнике данных.  
  
 SQL_ALL_EXCEPT_LIKE будет возвращаться в столбце с возможностью поиска для байта, счетчик, Double, Single, Long и короткого типов данных. (LIKE возможность достигается путем преобразования значения в символ с помощью преобразования канонические функции ODBC, затем сравнение.)
