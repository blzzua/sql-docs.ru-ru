---
title: "SQLStatistics (драйвера текстового файла) | Документы Microsoft"
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
- text file driver [ODBC], SQLStatistics
- SQLStatistics function [ODBC], Text File Driver
ms.assetid: 311afc01-d656-425f-be43-4a8e7cbc9a97
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1228d60c046d2633e46f93e162684365d84c3c47
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="sqlstatistics-text-file-driver"></a>SQLStatistics (драйвера текстового файла)
> [!NOTE]  
>  В этом разделе сведения текстовый файл драйвера. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|столбцом|Комментарии|  
|------------|--------------|  
|TABLE_QUALIFIER|Путь к каталогу.<br /><br /> Соответствие шаблону не поддерживается в *szTableQualifier* аргумент.|  
|TABLE_OWNER|В этом столбце возвращается значение NULL, так как имя владельца не поддерживается.|  
|TABLE_NAME|Имя таблицы без разделителей.<br /><br /> Соответствие шаблону не поддерживается в *szTableName* аргумент.|  
|INDEX_QUALIFIER|Всегда возвращается значение NULL.|  
|INDEX_NAME|Зависящих от индекса.|  
|TYPE|Для ТИПА будет возвращаться только SQL_TABLE_STAT или SQL_INDEX_OTHER.|  
|SEQ_IN_INDEX|Зависящих от индекса.|  
|COLUMN_NAME|Зависящих от индекса.|  
|COLLATION|Зависящих от индекса.|  
|PAGES|Всегда возвращается значение NULL.|  
  
 Фильтрация основана на уникальность ( *fUnique* аргумент). *FAccuracy* параметр учитывается.
