---
title: Функция SQLWriteFileDSN | Документы Microsoft
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
- SQLWriteFileDSN
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLWriteFileDSN
helpviewer_keywords:
- SQLWriteFileDSN [ODBC]
ms.assetid: 9e18f56f-1061-416b-83d4-ffeec42ab5a9
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 973c27fb58411e0fd3ddc482a0a8cbee3d929ee8
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="sqlwritefiledsn-function"></a>Функция SQLWriteFileDSN
**Соответствия**  
 Появился в версии: ODBC 3.0  
  
 **Сводка**  
 **SQLWriteFileDSN** записывает сведения об файловый DSN.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
BOOL SQLWriteFileDSN(  
     LPCSTR     lpszFileName,  
     LPCSTR     lpszAppName,  
     LPCSTR     lpszKeyName,  
     LPCSTR     lpszString);  
```  
  
## <a name="arguments"></a>Аргументы  
 *lpszFileName*  
 [Вход] Указатель на имя файла источника данных. Расширение DSN добавляется для всех имен файлов, уже имеют расширение имени DSN.  
  
 *lpszAppName*  
 [Вход] Указатель на имя приложения. Это «ODBC» для раздела ODBC.  
  
 *lpszKeyName*  
 [Вход] Указатель на имя ключа для чтения. Зарезервированные ключевые слова в разделе «Комментарии».  
  
 *lpszString*  
 [Выход] Указывает строку, связанную с ключом, которые требуется записать. Максимальная длина строки, на который указывает этот аргумент составляет не более 32 767 байт.  
  
## <a name="returns"></a>Возвращает  
 Функция возвращает значение TRUE, если он прошел успешно, FALSE в случае неудачи.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLWriteFileDSN** возвращает значение FALSE, связанный с ним  *\*pfErrorCode* значение можно получить путем вызова **SQLInstallerError**. В следующей таблице перечислены  *\*pfErrorCode* значения, которые могут быть возвращены **SQLInstallerError** и описание каждого из них в контексте этой функции.  
  
|*\*pfErrorCode*|Ошибка|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Установщик Общие ошибки|Произошла ошибка для которого нет ошибок определенного установщика.|  
|ODBC_ERROR_INVALID_PATH|Путь установки недопустимый|Путь к имени файла, указанного в *lpszFileName* недопустимый аргумент.|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|Недопустимый тип запроса|*LpszAppName*, *lpszKeyName*, или *lpszString* аргумент имеет значение NULL.|  
  
## <a name="comments"></a>Комментарии  
 ODBC оставляет за собой [ODBC] Имя раздела, в котором хранятся сведения о соединении. Зарезервированные ключевые слова для этого раздела совпадают с зарезервированным для строки подключения в **SQLDriverConnect**. (Дополнительные сведения см. в разделе [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) описание функции.)  
  
 Приложения могут использовать эти зарезервированные ключевые слова для записи информации файловый DSN. Если приложению требуется создать или изменить строку соединения, связанный с Источником данных, оно может вызвать **SQLWriteFileDSN** для любого из зарезервированных ключевых слов строки подключения в разделе [ODBC].  
  
 Если *lpszString* аргумент является указателем null, ключевое слово, на который указывает *lpszKeyName* аргумент будут удалены из файла DSN с. Если *lpszString* и *lpszKeyName* аргументы — оба неопределенные указатели, раздел, на который указывает *lpszAppName* аргумент будут удалены из файла DSN с.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|При чтении информации из файловых источников данных|[SQLReadFileDSN](../../../odbc/reference/syntax/sqlreadfiledsn-function.md)|
