---
title: "SQLDriverConnect (драйвер Excel) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Excel driver [ODBC], SQLDriverConnect
- SQLDriverConnect function [ODBC], Excel Driver
ms.assetid: 285cb1ea-f461-4596-97f2-fc57af05dede
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 659789e73fa4ad85b0b79b599c6f253afdd566ec
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2018
---
# <a name="sqldriverconnect-excel-driver"></a>SQLDriverConnect (драйвер Excel)
> [!NOTE]  
>  В этом разделе сведения драйвера Excel. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 **SQLDriverConnect** позволяет подключаться к драйверу, без создания источника данных (DSN).  
  
 В строке подключения для всех драйверов поддерживаются следующие ключевые слова: **DSN**, **DBQ**, и **FIL**.  
  
 В следующей таблице показаны минимальное ключевых слов, необходимые для подключения к драйверу и приведен пример пар ключ значение, используемых с **SQLDriverConnect**. Полный список значений DRIVERID см. в разделе [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).  
  
> [!NOTE]  
>  Если DBQ или его значения не указан для Microsoft Excel 3.0 или 4.0 драйвера, драйвер подключается к текущему каталогу.  
  
|Драйвер|Необходимые ключевые слова|Примеры|  
|------------|-----------------------|--------------|  
|Microsoft Excel 3.0 или 4.0|Драйвер DriverID|Driver = {драйвер Microsoft Excel (*.xls)}; DBQ = c:\temp; DriverID = 278|  
|Microsoft Excel 5.0/7.0|Драйвер DriverID, DBQ|Driver = {драйвер Microsoft Excel (*.xls)}; DBQ=c:\temp\sample.xls; DriverID = 22|  
|Microsoft Excel 97 и более поздние версии|Драйвер DriverID, DBQ|Driver = {драйвер Microsoft Excel (*.xls)}; DBQ=c:\temp\sample.xls; DriverID = 790|
