---
title: "Поддержка SQLGetInfo | Документы Microsoft"
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
- compatibility [ODBC], SQLGetInfo
- backward compatibility [ODBC], SQLGetInfo
- SQLGetInfo function [ODBC], support
ms.assetid: 57326f57-daba-46b6-b0be-6c97213b9ef1
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c276373e01ab45c8c0464869296a121f8388884f
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="sqlgetinfo-support"></a>Поддержка SQLGetInfo
Когда ODBC 2. *x* приложение вызывает **SQLGetInfo** ODBC 3*.x* драйвера, *свойство* должен поддерживаться аргументы в следующей таблице.  
  
|*Свойство*|Возвращает|  
|----------------|-------------|  
|SQL_ALTER_TABLE (ODBC 2.0) **Примечание:** этот тип не является устаревшей; устарели и битовой маски, в столбце справа.|Битовая маска SQLINTEGER предложения в перечислении **ALTER TABLE** инструкции, поддерживаемые источником данных.<br /><br /> Следующие битовые маски используются для определения, какие предложения поддерживаются:<br /><br /> SQL_AT_DROP_COLUMN = поддерживается возможность удалять столбцы. Приводит к cascade ли ограничить поведение, определяемым драйвером. (ODBC 2.0)<br /><br /> SQL_AT_ADD_COLUMN = возможность добавления поддерживается несколько столбцов в одной инструкции ALTER TABLE. Этот бит не объединяются с другими SQL_AT_ADD_COLUMN_XXX bits или SQL_AT_CONSTRAINT_XXX bits. (ODBC 2.0)|  
|SQL_FETCH_DIRECTION (ODBC 1.0)<br /><br /> Тип данных был введен в ODBC 1.0; с версией, в которой он был представлен меткой каждой битовой маски.|Битовая маска SQLINTEGER, перечисление параметров направления поддерживаемых выборки.<br /><br /> Следующие битовые маски используются в сочетании с флагом, чтобы определить, какие параметры поддерживаются:<br /><br /> SQL_FD_FETCH_RELATIVE (ODBC 1.0) (ODBC 1.0) SQL_FD_FETCH_NEXT SQL_FD_FETCH_FIRST (ODBC 1.0) (ODBC 1.0) SQL_FD_FETCH_LAST SQL_FD_FETCH_PRIOR (ODBC 1.0) SQL_FD_FETCH_ABSOLUTE (ODBC 1.0) SQL_FD_FETCH_BOOKMARK (ODBC 2.0)|  
|SQL_LOCK_TYPES (ODBC 2.0)|Типы SQLINTEGER битовой маски, перечисления поддерживаемых блокировки для *fLock* аргумент в **SQLSetPos**.<br /><br /> Следующие битовые маски используются вместе с флагом, чтобы определить, какие типы блокировок поддерживаются:<br /><br /> SQL_LCK_NO_CHANGE SQL_LCK_EXCLUSIVE SQL_LCK_UNLOCK|  
|SQL_ODBC_API_CONFORMANCE (ODBC 1.0)|SQLSMALLINT значение, указывающее уровень соответствия ODBC.<br /><br /> SQL_OAC_NONE = нет<br /><br /> SQL_OAC_LEVEL1 = поддерживается уровня 1<br /><br /> SQL_OAC_LEVEL2 = поддерживается уровня 2|  
|SQL_ODBC_SQL_CONFORMANCE (ODBC 1.0)|SQLSMALLINT, обозначающее грамматику SQL, поддерживаемых драйвером. В разделе [грамматику SQL приложение C:](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md) для определения уровней совместимости SQL.<br /><br /> SQL_OSC_MINIMUM = минимальное грамматики поддерживается<br /><br /> SQL_OSC_CORE = поддерживается грамматику ядра<br /><br /> SQL_OSC_EXTENDED = расширенный грамматики поддерживается|  
|SQL_POS_OPERATIONS (ODBC 2.0)|Битовая маска SQLINTEGER поддерживаемые операции в перечислении **SQLSetPos**.<br /><br /> Чтобы определить, какие параметры поддерживаются следующие битовые маски используются для вместе с флагом:<br /><br /> SQL_POS_POSITION (ODBC 2.0) (ODBC 2.0) SQL_POS_REFRESH SQL_POS_UPDATE (ODBC 2.0) (ODBC 2.0) SQL_POS_DELETE SQL_POS_ADD (ODBC 2.0)|  
|SQL_POSITIONED_STATEMENTS (ODBC 2.0)|Битовая маска SQLINTEGER перечисление поддерживаемых позиционированных инструкций SQL.<br /><br /> Следующие битовые маски используются для определения, какие операторы поддерживаются:<br /><br /> SQL_PS_POSITIONED_DELETE SQL_PS_POSITIONED_UPDATE SQL_PS_SELECT_FOR_UPDATE|  
|SQL_SCROLL_CONCURRENCY (ODBC 1.0)|Битовая маска SQLINTEGER, перечисление параметров управления параллелизма, поддерживаемых для курсора.<br /><br /> Чтобы определить, какие параметры поддерживаются используются следующие битовые маски.<br /><br /> SQL_SCCO_READ_ONLY = курсор доступен только для чтения. Обновления не разрешены.<br /><br /> SQL_SCCO_LOCK = курсор использует самый низкий уровень блокировки достаточно, чтобы убедиться, что строки могут быть обновлены.<br /><br /> SQL_SCCO_OPT_ROWVER = курсор использует управление оптимистичным параллелизмом, сравнивая версии строк, такие как программа ROWID или Sybase TIMESTAMP.<br /><br /> SQL_SCCO_OPT_VALUES = курсор использует управление оптимистичным параллелизмом, сравнения значений.|  
|SQL_STATIC_SENSITIVITY (ODBC 2.0)|SQLINTEGER Битовая маска перечисление ли изменений приложению для статических и управляемых набором ключей курсора через **SQLSetPos** или позиционированного обновления или инструкций delete могут определяться с помощью этого приложения.<br /><br /> SQL_SS_ADDITIONS = Added строк являются видимыми для курсора; курсор можно прокрутить эти строки. Когда эти строки добавляются курсора зависит от драйвера.<br /><br /> SQL_SS_DELETIONS = удалено строк недоступны до текущей позиции курсора и не оставляйте «дыры» в результирующем наборе; После курсор прокручивается из удаленной строки, он не может возвращать для этой строки.<br /><br /> SQL_SS_UPDATES = обновления строк являются видимыми для курсора; Если курсор прокручивается и возвращает обновленную строку, данные, возвращенные курсором является обновленные данные, а не исходные данные. Этот параметр применяется только к статические курсоры или обновления на управляемые набором ключей курсоры, которые не обновить ключ. Этот параметр не применяется для динамического курсора или в случае, в котором в смешанном курсор изменяется ключ.<br /><br /> Является ли приложение может обнаружить изменения, внесенные в результирующий набор другим пользователям, включая другие курсоры в одном приложении, зависит от типа курсора.|  
  
 ODBC 3*.x* приложения, работа с ODBC 3*.x* драйвер не должен вызывать **SQLGetInfo** с *свойство* аргументы описано в Приведенный выше таблице, но следует использовать функции ODBC 3*.x* *свойство* аргументы, перечисленные в следующем абзаце. Не существует однозначного соответствия между *свойство* аргументы, используемые в ODBC 2. *x* и тех, которые используются в ODBC 3*.x*. ODBC 3*.x* приложения, работа с ODBC 2. *x* драйвера, с другой стороны, следует использовать *свойство* аргументы, описанные выше.  
  
 Некоторые типы сведений в приведенной выше таблице устарели и были заменены типами сведения атрибуты курсора. Эти устаревшие сведения типы: SQL_FETCH_DIRECTION, SQL_LOCK_TYPES, SQL_POS_OPERATIONS, SQL_POSITIONED_STATEMENTS, SQL_SCROLL_CONCURRENCY и SQL_STATIC_SENSITIVITY. Новые типы атрибуты курсора, SQL_XXX_CURSOR_ATTRIBUTES2 SQL_XXX_CURSOR_ATTRIBUTES1and, где XXX равно динамический, FORWARD_ONLY, KEYSET_DRIVEN или СТАТИЧЕСКИЙ. Каждый новый тип указывает возможности драйверов для типа одного курсора. Дополнительные сведения об этих параметрах см. в разделе [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) описание функции.
