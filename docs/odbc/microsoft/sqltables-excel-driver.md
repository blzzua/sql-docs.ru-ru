---
title: "SQLTables (драйвер Excel) | Документы Microsoft"
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
- Excel driver [ODBC], SQLTables
- SQLTables function [ODBC], Excel Driver
ms.assetid: 9410b686-4b5b-4b51-b5ef-f9d2e7a48faa
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 083f0813418dc366f14acc11be79c9eb68f5550d
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="sqltables-excel-driver"></a>SQLTables (драйвер Excel)
> [!NOTE]  
>  В этом разделе сведения драйвера Excel. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Аргумент|Комментарии|  
|--------------|--------------|  
|*szTableOwner*|Единственным допустимым аргументом для *szTableOwner* имеет значение NULL, так как ни один из драйверов не поддерживает имена владельцев. С *szTableOwner* значение NULL, возвращаются все таблицы. В столбце TABLE_OWNER возвращается значение NULL.|  
|*szTableQualifier*|Microsoft Excel 3.0 или 4.0 драйвера вместе, при вызове метода **SQLTables** со значением для *szTableQualifier* , но имя существующей таблицы, драйвер создает таблицу с таким именем.<br /><br /> В столбце TABLE_QUALIFIER **SQLTables** возвращает путь к каталогу.|  
|*SzTableType*|Для Microsoft Excel 3.0 или 4.0 «TABLE» является поддерживается только тип таблицы.<br /><br /> Для более поздних версий файлов Microsoft Excel «SYSTEM TABLE» возвращается для имена листов (таблицы с «$» со стороны) и «TABLE» возвращается для таблиц в листах.|
