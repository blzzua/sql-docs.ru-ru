---
title: Функция ConfigDSN | Документы Microsoft
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
- ConfigDSN
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- ConfigDSN
helpviewer_keywords:
- ConfigDSN [ODBC]
ms.assetid: 01ced74e-c575-4a25-83f5-bd7d918123f8
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b82eb128f125415d3dbdb24ffc616dbeccc5e938
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="configdsn-function"></a>Функция ConfigDSN
**Соответствия**  
 Версии появился: ODBC 1.0  
  
 **Сводка**  
 **ConfigDSN** добавляет, изменяет или удаляет источники данных из сведений о системе. Он может запрашивать у пользователя сведения о соединении. Он может быть в DLL-Библиотека драйвера или отдельных DLL-файлов установки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
BOOL ConfigDSN(  
     HWND     hwndParent,  
     WORD     fRequest,  
     LPCSTR   lpszDriver,  
     LPCSTR   lpszAttributes);  
```  
  
## <a name="arguments"></a>Аргументы  
 *hwndParent*  
 [Вход] Дескриптор родительского окна. Функция не будет отображать все диалоговые окна, если маркер имеет значение null.  
  
 *fRequest*  
 [Вход] Тип запроса. *FRequest* аргумент должен иметь один из следующих значений:  
  
 ODBC_ADD_DSN: Добавьте новый источник данных.  
  
 ODBC_CONFIG_DSN: Настройка (изменить) существующего источника данных.  
  
 Значение ODBC_REMOVE_DSN: Удаление существующего источника данных.  
  
 *lpszDriver*  
 [Вход] Описание драйвера (обычно имя СУБД связанные) пользователям вместо имени физического драйвера.  
  
 *lpszAttributes*  
 [Вход] Двойной завершающий список атрибутов в форме пар «ключевое слово значение». Дополнительные сведения см. в разделе «Комментарии».  
  
## <a name="returns"></a>Возвращает  
 Функция возвращает значение TRUE, если он прошел успешно, FALSE в случае неудачи.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **ConfigDSN** возвращает значение FALSE, связанный с ним  *\*pfErrorCode* значение передается буфера установщика ошибок с помощью вызова **SQLPostInstallerError** и можно получить, вызвав **SQLInstallerError**. В следующей таблице перечислены  *\*pfErrorCode* значения, которые могут быть возвращены **SQLInstallerError** и описание каждого из них в контексте этой функции.  
  
|*\*pfErrorCode*|Ошибка|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_INVALID_HWND|Недопустимый дескриптор окна|*HwndParent* недопустимый аргумент.|  
|ODBC_ERROR_INVALID_KEYWORD_VALUE|Пары "недопустимое ключевое слово значение"|*LpszAttributes* аргумент содержит синтаксическую ошибку.|  
|ODBC_ERROR_INVALID_NAME|Недопустимое имя драйвера или преобразователь|*LpszDriver* недопустимый аргумент. Он не найден в реестре.|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|Недопустимый тип запроса|*FRequest* аргумент не является одним из следующих:<br /><br /> ЗНАЧЕНИЕ ODBC_REMOVE_DSN ODBC_CONFIG_DSN ODBC_ADD_DSN|  
|ODBC_ERROR_REQUEST_FAILED|*Запрос* сбой|Не удалось выполнить операцию, запрошенную *fRequest* аргумент.|  
|ODBC_ERROR_DRIVER_SPECIFIC|Ошибка драйвера или преобразователь|Ошибка драйвера, для которого нет определенных ошибок установщика ODBC. *SzError* аргумента в вызове **SQLPostInstallerError** функция должна содержать сообщении об ошибке драйвера.|  
  
## <a name="comments"></a>Комментарии  
 **ConfigDSN** получения сведений о соединении из установщика DLL как список атрибутов в форме пар «ключевое слово значение». Каждая пара заканчивается нулевым байтом, и завершается нулевым байтом весь список. (То есть две пустые байты отмечающий конец списка.) Не допускаются пробелы вокруг знака равенства в паре «ключевое_слово значение». **ConfigDSN** может принимать ключевые слова, которые не являются допустимым ключевые слова для **SQLBrowseConnect** и **SQLDriverConnect**. **ConfigDSN** не обязательно поддержки все ключевые слова, которые являются доступными ключевыми словами для **SQLBrowseConnect** и **SQLDriverConnect**. (**ConfigDSN** не принимает **ДРАЙВЕР** ключевое слово.) Ключевые слова, используемые **ConfigDSN** функция должна поддерживать все возможности, необходимые для повторного создания источника данных, с помощью средства установки АВТОМАТИЧЕСКИ установщика. При использовании **ConfigDSN** значения и значения строки подключения совпадают, следует использовать одинаковые ключевые слова.  
  
 Как и в **SQLBrowseConnect** и **SQLDriverConnect**, ключевые слова и их значения не должны содержать **[] {} (),? \*=! @** символов, а значение **DSN** ключевое слово не может состоять только из пробелов. Из-за грамматики реестра ключевые слова и имена источников данных не может содержать обратную косую черту (\\) символов.  
  
 **ConfigDSN** должен вызывать **SQLValidDSN** проверить длину имени источника данных и убедитесь, что включены недопустимых символов в имени. Если имя источника данных имеет длину более SQL_MAX_DSN_LENGTH или содержит недопустимые символы, **SQLValidDSN** возвращает сообщение об ошибке и **ConfigDSN** возвращает сообщение об ошибке. Кроме того, длина имени источника данных проверяется по **SQLWriteDSNToIni**.  
  
 Например чтобы настроить источник данных, требуется идентификатор пользователя, пароль и имя базы данных, программа установки может передать следующие пары ключ значение:  
  
```  
DSN=Personnel Data\0UID=Smith\0PWD=Sesame\0DATABASE=Personnel\0\0  
```  
  
 Дополнительные сведения об этих ключевых словах см. в разделе [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) и документацию для каждого драйвера.  
  
 Для отображения диалогового окна, *hwndParent* не может иметь значение null.  
  
## <a name="adding-a-data-source"></a>Добавление источника данных  
 Если имя источника данных передается в **ConfigDSN** в *lpszAttributes*, **ConfigDSN** проверяет, что имя является допустимым. Если имя источника данных совпадает с существующим именем источника данных и *hwndParent* имеет значение null, **ConfigDSN** перезаписывает существующее имя. Если он совпадает с существующим именем и *hwndParent* не равно null, **ConfigDSN** предлагает пользователю перезаписать существующее имя.  
  
 Если *lpszAttributes* содержит достаточно информации для подключения к источнику данных **ConfigDSN** можно добавить источник данных или открыть диалоговое окно, с помощью которого пользователь может изменить сведения о соединении. Если *lpszAttributes* не содержит достаточно информации для подключения к источнику данных **ConfigDSN** необходимо определить данные, необходимые; Если *hwndParent* не равно null, отображается диалоговое окно для получения сведений от пользователя.  
  
 Если **ConfigDSN** отображает диалоговое окно, он должен отображать все сведения о соединении, переданный в *lpszAttributes*. В частности, если было передано имя источника данных, **ConfigDSN** отображает это имя, но не разрешает пользователю изменять его. **ConfigDSN** можно указать значения по умолчанию для сведений о соединении, не переданный в *lpszAttributes*.  
  
 Если **ConfigDSN** не удается получить сведения для завершения подключения для источника данных, она возвращает значение FALSE.  
  
 Если **ConfigDSN** можно получить сведения о завершения соединения для источника данных, он вызывает метод **SQLWriteDSNToIni** в программе установки библиотеку DLL для добавления новой спецификации источника данных в файл Odbc.ini (или реестра). **SQLWriteDSNToIni** добавляет имя источника данных в раздел [источники данных ODBC], создает раздел спецификации источника данных и добавляет **ДРАЙВЕР** ключевого слова with описание драйверов, как его значение. **ConfigDSN** вызовы **SQLWritePrivateProfileString** в программе установки библиотеку DLL для добавления любого дополнительных ключевых слов и значений, используемых драйвером.  
  
## <a name="modifying-a-data-source"></a>Изменение источника данных  
 Чтобы изменить источник данных, имя источника данных должны быть переданы **ConfigDSN** в *lpszAttributes*. **ConfigDSN** проверяет, является имя источника данных в файле Odbc.ini (или в реестре).  
  
 Если *hwndParent* имеет значение null, **ConfigDSN** использует эти сведения в *lpszAttributes* для изменения сведений в файле Odbc.ini (или реестра). Если *hwndParent* не равно null, **ConfigDSN** отображает диалоговое окно, используя сведения в *lpszAttributes*; Дополнительные сведения, которые отсутствуют в *lpszAttributes* , он использует данные из сведений о системе. Пользователь может изменять сведения, прежде чем **ConfigDSN** сохраняет его в сведениях о системе.  
  
 Если источник данных был изменен, **ConfigDSN** сначала вызывает **SQLRemoveDSNFromIni** в установщик DLL, чтобы удалить существующие данные источника спецификации из файла Odbc.ini (или из реестра). Затем следует инструкциям в предыдущем разделе, чтобы добавить новую спецификацию источника данных. Если имя источника данных не был изменен, **ConfigDSN** вызовы **SQLWritePrivateProfileString** в установщике DLL для внесения других изменений. **ConfigDSN** не может удалить или изменить значение **драйвер** ключевое слово.  
  
## <a name="deleting-a-data-source"></a>Удаление источника данных  
 Чтобы удалить источник данных, имя источника данных должны быть переданы **ConfigDSN** в *lpszAttributes*. **ConfigDSN** проверяет, является имя источника данных в файле Odbc.ini (или в реестре). Затем он вызывает **SQLRemoveDSNFromIni** в установщике DLL удаление источника данных.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Добавление, изменение или удаление источника данных|[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)|  
|Получение значения из файла Odbc.ini или в реестре|[SQLGetPrivateProfileString](../../../odbc/reference/syntax/sqlgetprivateprofilestring-function.md)|  
|Удаление источника данных по умолчанию|[SQLRemoveDefaultDataSource](../../../odbc/reference/syntax/sqlremovedefaultdatasource-function.md)|  
|Удаление имени источника данных из Odbc.ini (или раздела реестра)|[SQLRemoveDSNFromIni](../../../odbc/reference/syntax/sqlremovedsnfromini-function.md)|  
|Добавление имени источника данных Odbc.ini (или раздела реестра)|[SQLWriteDSNToIni](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)|  
|Запись значения в файле Odbc.ini и реестр|[SQLWritePrivateProfileString](../../../odbc/reference/syntax/sqlwriteprivateprofilestring-function.md)|
