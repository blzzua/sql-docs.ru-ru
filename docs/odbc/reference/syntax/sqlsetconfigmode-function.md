---
title: Функция SQLSetConfigMode | Документы Microsoft
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
apiname:
- SQLSetConfigMode
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLSetConfigMode
helpviewer_keywords:
- SQLSetConfigMode function [ODBC]
ms.assetid: 09eb88ea-b6f6-4eca-b19d-0951cebc6c0a
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3b9305a4b9cbbf8ce7316d1c3eccf71115e5f0fe
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="sqlsetconfigmode-function"></a>Функция SQLSetConfigMode
**Соответствия**  
 Появился в версии: ODBC 3.0  
  
 **Сводка**  
 **SQLSetConfigMode** задает режим конфигурации, который указывает, где в сведениях о системе Odbc.ini запись со списком значений источника данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
BOOL SQLSetConfigMode(  
     UWORD     wConfigMode);  
```  
  
## <a name="arguments"></a>Аргументы  
 *wConfigMode*  
 [Вход] Режим конфигурации установщика (в разделе «Комментарии»). Значение в *wConfigMode* может быть:  
  
 ODBC_USER_DSN  
  
 ODBC_SYSTEM_DSN  
  
 ODBC_BOTH_DSN  
  
## <a name="returns"></a>Возвращает  
 Функция возвращает значение TRUE, если он прошел успешно, FALSE в случае неудачи.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLSetConfigMode** возвращает значение FALSE, связанный с ним  *\*pfErrorCode* значение можно получить путем вызова **SQLInstallerError**. В следующей таблице перечислены  *\*pfErrorCode* значения, которые могут быть возвращены **SQLInstallerError** и описание каждого из них в контексте этой функции.  
  
|*\*pfErrorCode*|Ошибка|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_INVALID_PARAM_SEQUENCE|Недопустимый параметр последовательности|*WConfigMode* ODBC_USER_DSN, ODBC_SYSTEM_DSN или ODBC_BOTH_DSN не содержал аргумент.|  
  
## <a name="comments"></a>Комментарии  
 Эта функция используется для задания, где Odbc.ini запись со списком значений источника данных — сведения о системе. Если *wConfigMode* ODBC_USER_DSN, имя источника данных является пользовательское имя DSN и функция считывает из записи Odbc.ini в HKEY_CURRENT_USER. Если это ODBC_SYSTEM_DSN источника данных является системный DSN и функция считывает из записи Odbc.ini в HKEY_LOCAL_MACHINE. Если это ODBC_BOTH_DSN, предпринимается попытка HKEY_CURRENT_USER и в случае неудачи, используется HKEY_LOCAL_MACHINE.  
  
 Эта функция не влияет на **SQLCreateDataSource** и **SQLDriverConnect**. Режим конфигурации должна быть настроена, когда драйвер считывает данные из реестра, вызвав **SQLGetPrivateProfileString** или записывает в реестр, вызвав **SQLWritePrivateProfileString**. Вызовы **SQLGetPrivateProfileString** и **SQLWritePrivateProfileString** использовать режим конфигурации знать, какие части реестра для работы с.  
  
> [!CAUTION]  
>  **SQLSetConfigMode** должен вызываться только при необходимости; Если неправильно установлен режим, установщик ODBC не сможет работать правильно.  
  
 **SQLSetConfigMode** делает изменения реестра прямой режим конфигурации. Это помимо изменяет режим конфигурации с помощью вызова **SQLConfigDataSource**. Вызов **SQLConfigDataSource** задает режим конфигурации, чтобы различать пользователей и системных источников данных при изменении имени DSN. Перед возвратом, **SQLConfigDataSource** восстанавливает режим конфигурации BOTHDSN.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Создание источника данных|[SQLCreateDataSource](../../../odbc/reference/syntax/sqlcreatedatasource-function.md)|  
|Соединение с источником данных, используется поле строки или диалоговое окно соединения|[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)|  
|Получение режима конфигурации|[SQLGetConfigMode](../../../odbc/reference/syntax/sqlgetconfigmode-function.md)|
