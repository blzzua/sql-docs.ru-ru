---
title: SQLSetStmtAttr (библиотека курсоров) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SQLSetStmtAttr function [ODBC], Cursor Library
ms.assetid: 6018a733-c2c8-4047-92ec-92cf85031767
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2d707170f7e321ce41d096da6651c0e825621713
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="sqlsetstmtattr-cursor-library"></a>SQLSetStmtAttr (библиотека курсоров)
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этой возможности в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Корпорация Майкрософт рекомендует использовать функциональность курсора драйвера.  
  
 В этом разделе рассматриваются вопросы применения **SQLSetStmtAttr** функции в библиотеку курсоров. Общие сведения о **SQLSetStmtAttr**, в разделе [SQLSetStmtAttr, функция](../../../odbc/reference/syntax/sqlsetstmtattr-function.md).  
  
 Библиотека курсоров поддерживает следующие атрибуты инструкций с **SQLSetStmtAttr**:  
  
|||  
|-|-|  
|SQL_ATTR_CONCURRENCY|SQL_ATTR_ROW_BIND_OFFSET_PTR|  
|SQL_ATTR_CURSOR_TYPE|SQL_ATTR_ROW_BIND_TYPE|  
|SQL_ATTR_FETCH_BOOKMARK_PTR|SQL_ATTR_ROWSET_ARRAY_SIZE|  
|SQL_ATTR_PARAM_BIND_OFFSET_PTR|SQL_ATTR_SIMULATE_CURSOR|  
|SQL_ATTR_PARAM_BIND_TYPE|SQL_ATTR_USE_BOOKMARKS|  
  
 Библиотека курсоров поддерживает только значения атрибута SQL_ATTR_CURSOR_TYPE инструкции SQL_CURSOR_FORWARD_ONLY и SQL_CURSOR_STATIC.  
  
 Для курсоров библиотеку курсоров поддерживает SQL_CONCUR_READ_ONLY значение атрибута инструкции SQL_ATTR_CONCURRENCY. Для описания статических курсоров библиотеку курсоров поддерживает SQL_CONCUR_READ_ONLY и SQL_CONCUR_VALUES значения атрибута инструкции SQL_ATTR_CONCURRENCY.  
  
 Библиотека курсоров поддерживает только значение атрибута инструкции SQL_ATTR_SIMULATE_CURSOR SQL_SC_NON_UNIQUE.  
  
 Несмотря на то, что спецификации ODBC поддерживает вызовы **SQLSetStmtAttr** с атрибутами SQL_ATTR_PARAM_BIND_TYPE или SQL_ATTR_ROW_BIND_TYPE после **SQLFetch** или **SQLFetchScroll**  был вызван, курсор не содержит библиотеки. Прежде чем его можно изменить тип привязки в библиотеку курсоров, приложение должно закрыть курсор. Библиотека курсоров поддерживает изменение SQL_ATTR_ROW_BIND_OFFSET_PTR, SQL_ATTR_PARAM_BIND_OFFSET_PTR, SQL_ATTR_ROWS_FETCHED_PTR и атрибуты инструкции SQL_ATTR_PARAMS_PROCESSED_PTR, когда курсор открыт.  
  
 Приложение может вызвать **SQLSetStmtAttr** с **атрибута** из SQL_ATTR_ROW_ARRAY_SIZE, чтобы изменить размер набора строк при открытом курсоре. Новый размер набора строк вступят в силу при очередном **SQLFetchScroll** или **SQLFetch** вызывается.  
  
 Библиотека курсоров поддерживает настройку SQL_ATTR_PARAM_BIND_OFFSET_PTR или SQL_ATTR_ROW_BIND_OFFSET_PTR атрибут инструкции для включения привязки смещения. Смещение привязки не будет использоваться для выполнения запросов к **SQLFetch** при использовании библиотеки курсоров ODBC 2. *x* драйвера.  
  
 Библиотека курсоров поддерживает присвоение атрибуту инструкции SQL_ATTR_USE_BOOKMARKS SQL_UB_VARIABLE.
