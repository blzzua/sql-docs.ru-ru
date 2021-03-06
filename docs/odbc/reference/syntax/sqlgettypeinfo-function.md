---
title: Функция SQLGetTypeInfo | Документы Microsoft
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
- SQLGetTypeInfo
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetTypeInfo
helpviewer_keywords:
- SQLGetTypeInfo function [ODBC]
ms.assetid: bdedb044-8924-4ca4-85f3-8b37578e0257
caps.latest.revision: 21
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 508b89f5ff60b5cf64a03d167bf1ad4476edb734
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="sqlgettypeinfo-function"></a>Функция SQLGetTypeInfo
**Соответствия**  
 Появился в версии: Полное соответствие стандартам 1.0 ODBC: ISO-92  
  
 **Сводка**  
 **SQLGetTypeInfo** возвращает сведения о типах данных, поддерживаемых источником данных. Драйвер возвращает сведения в виде результирующего набора SQL. Типы данных, предназначенные для использования в инструкции языка определения данных (DDL).  
  
> [!IMPORTANT]  
>  Приложения должны использовать имена типов, возвращаемых в столбце TYPE_NAME **SQLGetTypeInfo** результирующего набора **ALTER TABLE** и **CREATE TABLE** инструкции. **SQLGetTypeInfo** могут возвращать несколько строк с одинаковыми значениями в столбце DATA_TYPE.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SQLRETURN SQLGetTypeInfo(  
     SQLHSTMT      StatementHandle,  
     SQLSMALLINT   DataType);  
```  
  
## <a name="arguments"></a>Аргументы  
 *StatementHandle*  
 [Вход] Дескриптор инструкции для результирующего набора.  
  
 *Тип данных*  
 [Вход] Тип данных SQL. Это должно быть одно из значений в [типов данных SQL](../../../odbc/reference/appendixes/sql-data-types.md) раздел типы данных приложение D: или типа данных SQL специфические для драйвера. SQL_ALL_TYPES указывает, что должны быть возвращены сведения обо всех типах данных.  
  
## <a name="returns"></a>Возвращает  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, значение SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLGetTypeInfo** возвращает значение SQL_ERROR или SQL_SUCCESS_WITH_INFO, соответствующее значение SQLSTATE можно получить, вызвав **SQLGetDiagRec** с *HandleType* из SQL _HANDLE_STMT и *обработки* из *StatementHandle*. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые **SQLGetTypeInfo** и описание каждого из них в контексте этой функции; нотации «(DM)» предшествует описания SQLSTATE, возвращаемых диспетчером драйверов. Код возврата, связанные с каждым из значений SQLSTATE — это SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Ошибка|Description|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Информационное сообщение, относящиеся к драйверу. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|01S02|Значение параметра изменено|Атрибут указанного оператора недопустимый из-за условий работы реализации, поэтому был временно заменены примерно такое же значение. (Вызов **SQLGetStmtAttr** для определения временно подставляемого значения.) Заменяющее значение допустимо для *StatementHandle* до закрытия курсора. Атрибуты инструкции, которые могут быть изменены представляют собой: SQL_ATTR_CONCURRENCY, SQL_ATTR_CURSOR_TYPE, атрибута SQL_ATTR_KEYSET_SIZE, значения SQL_ATTR_MAX_LENGTH, SQL_ATTR_MAX_ROWS, SQL_ATTR_QUERY_TIMEOUT и SQL_ATTR_SIMULATE_CURSOR. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|08S01|Сбой связи|Сбой в канале связи между драйвером и источника данных, к которому был подключен драйвер перед обработкой функции было завершено.|  
|24000|Недопустимое состояние курсора|Курсор был открыт на *StatementHandle,* и **SQLFetch** или **SQLFetchScroll** бы была вызвана. Если эта ошибка возвращается диспетчером драйверов **SQLFetch** или **SQLFetchScroll** не вернула значение SQL_NO_DATA и возвращается с помощью драйвера, если **SQLFetch** или **SQLFetchScroll** вернула значение SQL_NO_DATA.<br /><br /> Результирующий набор был открыт на *StatementHandle*, но **SQLFetch** или **SQLFetchScroll** не был вызван.|  
|40001|Сбой сериализации|Транзакции выполнен откат из-за взаимоблокировку ресурсов в другой транзакции.|  
|40003|Неизвестный завершение операторов|Сбой подключения во время выполнения этой функции и не удается определить состояние транзакции.|  
|HY000|Общая ошибка|Произошла ошибка, для которой было нет определенных SQLSTATE и для которого был определен SQLSTATE не зависит от реализации. Сообщение об ошибке, возвращенные **SQLGetDiagRec** в  *\*MessageText* буфера описывает ошибку и его причины.|  
|HY001|Ошибка выделения памяти|Драйверу не удалось выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY004|Недопустимый тип данных SQL|Значение, указанное для аргумента *DataType* был допустимым идентификатором типа данных ODBC SQL, ни идентификатор типа данных, поддерживаемых драйвером.|  
|HY008|Операция отменена|Асинхронная обработка была включена для *StatementHandle*, затем вызова функции и до выполнения, **SQLCancel** или **SQLCancelHandle** был вызывается на *StatementHandle*. Затем функция была вызвана снова на *StatementHandle*.<br /><br /> Функция была вызвана, и до выполнения, **SQLCancel** или **SQLCancelHandle** был вызван для *StatementHandle* из другого потока в многопоточные приложения.|  
|HY010|Ошибка последовательности функций|(DM) был вызван асинхронно выполняемой функции для дескриптора соединения, с которым связан *StatementHandle*. Выполняется при этом асинхронной функция **SQLGetTypeInfo** была вызвана функция.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, или **SQLMoreResults** был вызван для *StatementHandle* и возвращается SQL_PARAM_DATA_ ЭТОТ ПАРАМЕТР ДОСТУПЕН. До получения данных для всех параметров потоковой вызове этой функции.<br /><br /> (DM) был вызван асинхронно выполняемой функции (не данный файл) для *StatementHandle* и все еще выполняется, при вызове этой функции.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, или **SQLSetPos** был вызван для  *StatementHandle* и возвращается значение SQL_NEED_DATA. Эта функция был вызван перед отправкой данных для всех параметров с данными времени выполнения или столбцов.|  
|HY013|Ошибка управления памятью|Не удалось обработать вызов функции, поскольку базовые объекты памяти будет недоступен, возможно из-за нехватки памяти.|  
|HY117|Соединение будет приостановлена из-за неизвестной транзакции состояния. Только отключиться и разрешены функции, доступные только для чтения.|(DM) Дополнительные сведения о состоянии приостановки см. в разделе [функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Дополнительная возможность не реализована|Сочетание текущих настроек атрибуты инструкции SQL_ATTR_CONCURRENCY и SQL_ATTR_CURSOR_TYPE не поддерживается драйвером или источником данных.<br /><br /> Атрибут инструкции SQL_ATTR_USE_BOOKMARKS было задано значение SQL_UB_VARIABLE, а атрибут инструкции SQL_ATTR_CURSOR_TYPE был задан тип курсора, для которого драйвер не поддерживает закладки.|  
|HYT00|Время ожидания истекло|Время ожидания запроса истекло раньше, чем источник данных вернул результирующий набор. Время ожидания задается с помощью **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT.|  
|HYT01|Время ожидания соединения истекло|Время ожидания соединения истекло раньше, чем ответил на запрос источника данных. Время ожидания задается с помощью **SQLSetConnectAttr**, sql_attr_connection_timeout не учитывается.|  
|IM001|Драйвер не поддерживает эту функцию|(DM) драйвер, соответствующий *StatementHandle* не поддерживает функцию.|  
|IM017|В режиме асинхронное уведомление отключена опроса|При использовании модели уведомление опроса отключен.|  
|IM018|**SQLCompleteAsync** не был вызван для завершения предыдущей асинхронной операции на этот дескриптор.|Если предыдущего вызова функции с дескриптором возвращает SQL_STILL_EXECUTING и уведомлений в режиме **SQLCompleteAsync** должен вызываться для этого после обработки и выполнения операции с дескриптором.|  
  
## <a name="comments"></a>Комментарии  
 **SQLGetTypeInfo** возвращает результаты в виде стандартных результирующий набор, упорядоченный по значению DATA_TYPE, а затем по степени соответствия типа данных аналогичному для соответствующего типа данных ODBC SQL. Типы данных, определенные в источнике данных имеют приоритет над определяемым пользователем типам данных. Таким образом порядок сортировки не обязательно согласуется, но может быть обобщенный как DATA_TYPE сначала, следуют TYPE_NAME, оба по возрастанию. Предположим, что источник данных определенных типов данных INTEGER и СЧЕТЧИКА, котором значение СЧЕТЧИКА не заданы с автоматическим приращением, а также был определен, когда определяемых пользователем типов данных WHOLENUM. Они будут возвращены в целое число, порядок и WHOLENUM и СЧЕТЧИКОВ, так как WHOLENUM строго соответствует данных ODBC SQL типа SQL_INTEGER, пока тип данных заданы с автоматическим приращением, несмотря на то, что поддерживается источником данных, не наиболее точно соответствуют типу данных ODBC SQL. Сведения о том, как эти сведения может использоваться в разделе [инструкции DDL](../../../odbc/reference/develop-app/ddl-statements.md).  
  
 Если *DataType* аргумент указывает тип данных, который является действительным для версии поддерживаются драйвером ODBC, но не поддерживается драйвером, то возвращается пустой результирующий набор.  
  
> [!NOTE]  
>  Дополнительные сведения о общего использования, аргументы и возвращаемые данные функций каталога ODBC см. в разделе [функций каталога](../../../odbc/reference/develop-app/catalog-functions.md).  
  
 Следующие столбцы были переименованы для ODBC 3. *x*. Имя столбца изменения не влияют на обратной совместимости так, как привязать приложений, номер столбца.  
  
|Столбец ODBC 2.0|ODBC 3. *x* столбца|  
|---------------------|-----------------------|  
|PRECISION|COLUMN_SIZE|  
|MONEY|FIXED_PREC_SCALE|  
|AUTO_INCREMENT|AUTO_UNIQUE_VALUE|  
  
 Следующие столбцы были добавлены в набор результатов, возвращенных **SQLGetTypeInfo** для ODBC 3. *x*:  
  
-   SQL_DATA_TYPE  
  
-   INTERVAL_PRECISION  
  
-   SQL_DATETIME_SUB  
  
-   NUM_PREC_RADIX  
  
 В следующей таблице перечислены столбцы в результирующем наборе. Дополнительные столбцы вслед за столбец 19 (INTERVAL_PRECISION) можно определить с помощью драйвера. Приложение должно получить доступ к от драйвера отсчет от конца результирующего набора, а не порядковый номер явное указание. Дополнительные сведения см. в разделе [данные, возвращаемые функциями каталога](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md).  
  
> [!NOTE]  
>  **SQLGetTypeInfo** не может возвратить все типы данных. Например драйвер не может возвратить определяемым пользователем типам данных. Приложения могут использовать любой допустимый тип данных, независимо от того, он возвращается в виде **SQLGetTypeInfo**. Типы данных, возвращенных **SQLGetTypeInfo** поддерживаемые источника данных. Они предназначены для использования в инструкции языка определения данных (DDL). Драйверы может возвращать результирующий набор данных с помощью типов данных, отличных от типов, возвращаемых **SQLGetTypeInfo**. При создании результирующего набора функции каталога, драйвер может использовать тип данных, который не поддерживается источником данных.  
  
|Имя столбца|столбцом<br /><br /> number|Тип данных|Комментарии|  
|-----------------|-----------------------|---------------|--------------|  
|ФУНКЦИЯ TYPE_NAME (ODBC 2.0)|1|Varchar not NULL|Имя типа данных зависит от источника данных; Например «CHAR()», «VARCHAR()», «MONEY», «ДЛИННОЕ VARBINARY» или «() CHAR FOR BIT DATA». Приложения должны использовать это имя в **CREATE TABLE** и **ALTER TABLE** инструкции.|  
|ТИП ДАННЫХ (ODBC 2.0)|2|Smallint, не NULL|Тип данных SQL. Это может быть тип данных SQL драйвера или тип данных ODBC SQL. Для типов данных даты-времени или интервала этот столбец возвращает имя четкими данных (например, SQL_TYPE_TIME или SQL_INTERVAL_YEAR_TO_MONTH). Список допустимых типов данных ODBC SQL см. в разделе [типов данных SQL](../../../odbc/reference/appendixes/sql-data-types.md) в типах данных приложение D:. Сведения о типах данных драйвера SQL см. в документации драйвера.|  
|COLUMN_SIZE (ODBC 2.0)|3|Целочисленный|Столбец максимальный размер, который сервер поддерживает этот тип данных. Для числовых данных это максимальная точность. Строковые данные это длина в символах. Для типов данных datetime это длина в символах строкового представления (при условии, что максимально допустимой точности доли секунды). Для типов данных, где размер столбца не применяется, будет возвращено значение NULL. Для типа данных interval, это число символов в символьном представлении интервала литерала (см. в соответствии с определением точности; интервала [длина типа данных Interval](../../../odbc/reference/appendixes/interval-data-type-length.md) в типах данных приложение D:).<br /><br /> Дополнительные сведения о размер столбца. в разделе [размер столбца, десятичных цифр, длина в октетах передачи и отображаемый размер](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) в типах данных приложение D:.|  
|LITERAL_PREFIX (ODBC 2.0)|4|Varchar|Символ или символы, используемые в качестве префикса; например знак кавычки (') для символьных типов данных или 0 x для двоичных типов данных; Для типов данных, где неприменимо литеральный префикс, будет возвращено значение NULL.|  
|LITERAL_SUFFIX (ODBC 2.0)|5|Varchar|Символ или символы, используемые для завершения литералом. например знак кавычки (') для символьных типов данных; Для типов данных, где суффикс литерала не применим, будет возвращено значение NULL.|  
|CREATE_PARAMS (ODBC 2.0)|6|Varchar|Список ключевых слов, разделенных запятыми, каждому параметру, приложение может указать в круглые скобки, при использовании имени, который возвращается в поле TYPE_NAME. Ключевые слова в списке может быть любым из следующих: длина, точность или масштаб. Они отображаются в порядке, что синтаксис требует использовать их. Например, будет CREATE_PARAMS для десятичной записи «точность, масштаб»; CREATE_PARAMS для VARCHAR будет равно «длина». Возвращается значение NULL, если нет параметров для определения типа данных; Например, целое число со знаком.<br /><br /> Драйвер предоставляет CREATE_PARAMS текст на языке страны или региона, где он используется.|  
|ДОПУСКАЮЩИЕ ЗНАЧЕНИЯ NULL (ODBC 2.0)|7|Smallint, не NULL|Является ли тип данных допускает значение NULL:<br /><br /> SQL_NO_NULLS, если тип данных не может принимать значение NULL.<br /><br /> SQL_NULLABLE, если тип данных допускает значения NULL.<br /><br /> SQL_NULLABLE_UNKNOWN, если неизвестно, допускает ли столбец значения NULL.|  
|CASE_SENSITIVE (ODBC 2.0)|8|Smallint, не NULL|Является ли регистр в параметрах сортировки и сравнения в символьный тип данных:<br /><br /> SQL_TRUE, если тип данных в символьный тип данных и с учетом регистра.<br /><br /> Значение SQL_FALSE, если тип данных не в символьный тип данных или не учитывает регистр.|  
|ДЛЯ ПОИСКА (ODBC 2.0)|9|Smallint, не NULL|Как тип данных используется в **ГДЕ** предложения:<br /><br /> SQL_PRED_NONE, если столбец не может использоваться в **ГДЕ** предложения. (Это то же, что значение SQL_UNSEARCHABLE в ODBC 2. *x*.)<br /><br /> SQL_PRED_CHAR, если столбец может использоваться в **ГДЕ** предложение, но только с **как** предиката. (Это то же, что значение SQL_LIKE_ONLY в ODBC 2. *x*.)<br /><br /> SQL_PRED_BASIC, если столбец может использоваться в **ГДЕ** предложение со всеми операторами сравнения, за исключением **как** (сравнение, количественные сравнение **BETWEEN**,  **DISTINCT**, **в**, **соответствия**, и **UNIQUE**). (Это то же, что значение SQL_ALL_EXCEPT_LIKE в ODBC 2. *x*.)<br /><br /> SQL_SEARCHABLE, если столбец может использоваться в **ГДЕ** предложение с любым оператором сравнения.|  
|UNSIGNED_ATTRIBUTE (ODBC 2.0)|10|Smallint|Является ли тип данных без знака:<br /><br /> SQL_TRUE, если тип данных без знака.<br /><br /> Если тип данных имеет подпись значение SQL_FALSE.<br /><br /> Если атрибут не применим к типу данных или тип данных не является числом, возвращается значение NULL.|  
|FIXED_PREC_SCALE (ODBC 2.0)|11|Smallint, не NULL|Предопределенными ли тип данных фиксированной точности и масштаба (они зависящее от источника данных), такие как тип данных money:<br /><br /> SQL_TRUE, если он имеет предопределенные фиксированные точность и масштаб.<br /><br /> Значение SQL_FALSE, если он не имеет предопределенных фиксированные точность и масштаб.|  
|AUTO_UNIQUE_VALUE (ODBC 2.0)|12|Smallint|Является ли тип данных автоматически увеличивающимся:<br /><br /> SQL_TRUE, если тип данных является автоматическим приращением.<br /><br /> Значение SQL_FALSE, если тип данных не является автоматическим приращением.<br /><br /> Если атрибут не применим к типу данных или тип данных не является числом, возвращается значение NULL.<br /><br /> Приложение может вставлять значение в столбец с этим атрибутом, но обычно не удается обновить значения в столбце.<br /><br /> После вставки в столбец автоприращения уникальное значение вставляется в столбец во время операции вставки. Приращение не определен, но данные, определяемые источником. Приложение не следует предполагать, что столбцом с автоматическим приращением начиная с любой определенной точке или шагом на любой определенное значение.|  
|LOCAL_TYPE_NAME (ODBC 2.0)|13|Varchar|Локализованная версия имени зависит от источника данных типа данных. Если локализованное имя не поддерживается источником данных, возвращается значение NULL. Это имя предназначено для отображения только, как диалоговые окна.|  
|MINIMUM_SCALE (ODBC 2.0)|14|Smallint|Минимальный масштаб типа данных в источнике данных. Если тип данных имеет фиксированный масштаб, это значение содержится и в столбце MINIMUM_SCALE, и в столбце MAXIMUM_SCALE. Например столбец SQL_TYPE_TIMESTAMP могут иметь фиксированный масштаб для долей секунды. Для типов данных, к которым понятие масштаба не применимо, возвращается значение NULL. Дополнительные сведения см. в разделе [размер столбца, десятичных цифр, длина в октетах передачи и отображаемый размер](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) в типах данных приложение D:.|  
|MAXIMUM_SCALE (ODBC 2.0)|15|Smallint|Максимальный масштаб типа данных в источнике данных. Для типов данных, к которым понятие масштаба не применимо, возвращается значение NULL. Если максимальный масштаб не определен отдельно в источнике данных, но вместо этого определяется как максимальной точности, этот столбец содержит то же значение в столбце COLUMN_SIZE. Дополнительные сведения см. в разделе [размер столбца, десятичных цифр, длина в октетах передачи и отображаемый размер](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) в типах данных приложение D:.|  
|SQL_DATA_TYPE (ODBC 3.0)|16|Smallint, не NULL|Значение типа данных SQL, как оно отображается в поле SQL_DESC_TYPE дескриптора. Этот столбец содержит то же, что и столбец DATA_TYPE, за исключением типов данных datetime и интервал.<br /><br /> Для типов данных datetime и интервала SQL_DATA_TYPE поля в результирующем наборе будет возвращать SQL_INTERVAL или SQL_DATETIME и поле SQL_DATETIME_SUB вернет дополнительным кодом для конкретного типа данных interval или даты и времени. (См. [типы данных приложение D:](../../../odbc/reference/appendixes/appendix-d-data-types.md).)|  
|SQL_DATETIME_SUB (ODBC 3.0)|17|Smallint|Если значение SQL_DATA_TYPE равно SQL_DATETIME или SQL_INTERVAL, этот столбец содержит даты и времени или интервала дополнительным кодом. Для типов данных, за исключением даты и времени и интервала это поле имеет значение NULL.<br /><br /> Для интервала или типа данных datetime SQL_DATA_TYPE поля в результирующем наборе будет возвращать SQL_INTERVAL или SQL_DATETIME и поле SQL_DATETIME_SUB вернет дополнительным кодом для конкретного типа данных interval или даты и времени. (См. [типы данных приложение D:](../../../odbc/reference/appendixes/appendix-d-data-types.md).)|  
|NUM_PREC_RADIX (ODBC 3.0)|18|Целочисленный|Если тип данных является приблизительный числовой тип, этот столбец содержит значение 2, чтобы указать, что COLUMN_SIZE указывает число битов. Для точных числовых типов этот столбец содержит значение 10, чтобы указать, что COLUMN_SIZE указывает количество цифр дробной части. В противном случае этот столбец содержит значение NULL.|  
|INTERVAL_PRECISION (ODBC 3.0)|19|Smallint|Если тип данных является типом данных интервал, этот столбец содержит значение начальные точности интервала. (См. [точность типа данных Interval](../../../odbc/reference/appendixes/interval-data-type-precision.md) в типах данных приложение г.) В противном случае этот столбец содержит значение NULL.|  
  
 Сведения об атрибутах можно применять для типов данных или для определенных столбцов в результирующем наборе. **SQLGetTypeInfo** возвращает сведения о атрибуты, связанные с типами данных. **SQLColAttribute** возвращает сведения об атрибутах, связанных со столбцами в результирующий набор.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Привязка к столбцу в результирующем наборе буфера|[Функция SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Отмена обработки инструкции|[Функция SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Возврат сведений о столбце в результирующий набор|[Функция SQLColAttribute](../../../odbc/reference/syntax/sqlcolattribute-function.md)|  
|Выборка блока данных или прокрутке результирующего набора|[Функция SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Выборка одной строки или блока данных в направлении только вперед|[Функция SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Возврат сведений о драйверу или источнику данных|[Функция SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)|  
  
## <a name="see-also"></a>См. также:  
 [Справочник по API-интерфейса ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
