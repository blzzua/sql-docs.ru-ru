---
title: "SQLGetInfo (драйвера текстового файла) | Документы Microsoft"
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
- SQLGetInfo function [ODBC], Text File Driver
- text file driver [ODBC], SQLGetInfo
ms.assetid: 6b7a630e-47f8-4ee1-b2a7-476bc1d0b0d4
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7e8a4b2d890fa257b29049ca4374f475a4b80f57
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="sqlgetinfo-text-file-driver"></a>SQLGetInfo (драйвера текстового файла)
> [!NOTE]  
>  В этом разделе сведения текстовый файл драйвера. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 **SQLGetInfo** поддерживает тип данных SQL_FILE_USAGE. Возвращаемое значение равно 16-разрядное целое число, которое показывает, как драйвер непосредственно обрабатывает файлы в источнике данных:  
  
-   SQL_FILE_NOT_SUPPORTED — Драйвер не драйвер среднего уровня.  
  
-   SQL_FILE_TABLE — Драйвер одноуровневых обрабатывает файлы в источнике данных, как таблицы.  
  
-   SQL_FILE_QUALIFIER — Драйвер одноуровневых обрабатывает файлы в источнике данных как квалификатор.  
  
 Драйвер ODBC возвращает SQL_FILE_TABLE для Textdriver, так как каждый файл — это таблица.  
  
## <a name="sqldbmsver"></a>SQL_DBMS_VER  
  
|ISAM|Version|Формат номера версий|  
|----------|-------------|-------------------------------|  
|Текст|1.0|01.00.0000|  
  
## <a name="sqlcatalogusage"></a>SQL_CATALOG_USAGE  
 SQL_QU_DML_STATEMENTS &#124; SQL_QU_TABLE_DEFINITION  
  
## <a name="sqltimedatefunctions"></a>SQL_TIMEDATE_FUNCTIONS  
 SQL_FN_TD_CURDATE &#124;  SQL_FN_TD_CURTIME &#124;  SQL_FN_TD_DAYOFMONTH &#124;  SQL_FN_TD_DAYOFWEEK &#124; SQL_FN_TD_DAYOFYEAR &#124;  SQL_FN_TD_HOUR &#124; SQL_FN_TD_MINUTE &#124; SQL_FN_TD_MONTH &#124;  SQL_FN_TD_NOW &#124; SQL_FN_TD_SECOND &#124; SQL_FN_TD_WEEK &#124; SQL_FN_TD_YEAR
