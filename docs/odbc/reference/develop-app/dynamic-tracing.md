---
title: "Отслеживание | Документы Microsoft"
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
- tracing options [ODBC], dynamic
- dynamic tracing [ODBC]
ms.assetid: ebe58a83-a7b0-4747-86c8-2af2940471ef
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 51ea74b8b54bf9d9e26bedf2733147e8552ce08f
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="dynamic-tracing"></a>Отслеживание
Трассировку можно включить или отключить в любой момент запуска приложения. Это позволяет приложению для любого количества вызовов функции трассировки.  
  
 Переменная **ODBCSharedTraceFlag** устанавливается для включения трассировки динамически. Эта переменная используется совместно все работающие копии диспетчера драйверов. Любое приложение присваивает этой переменной, включена ли трассировка для всех приложений ODBC, которые в настоящее время запущен. Чтобы включить трассировку off при включении динамической трассировки, приложение вызывает **SQLSetConnectAttr** SQL_ATTR_TRACE присваивается SQL_TRACE_OFF. Этот вызов станет выключение трассировки только для этого приложения. Приложения, которые связаны с библиотекой Odbc32.lib можно изменять использование этой переменной. Данные трассировки могут отображаться в окне, в режиме реального времени, вместо файла трассировки, который должен быть открыт после сеанса ODBC. Элементы управления можно добавить на экран приложения, чтобы включить или отключить трассировку на будут.  
  
 Трассировки, библиотеки DLL, поставляемых с ODBC 3*.x* не является потокобезопасным. Не гарантируется, что файл журнала записывается правильно при включенной трассировке глобальные (переменная **ODBCSharedTraceFlag** задано) и более чем одним приложением записывает в файл трассировки в то же время. Это условие не возвращает ошибку.
