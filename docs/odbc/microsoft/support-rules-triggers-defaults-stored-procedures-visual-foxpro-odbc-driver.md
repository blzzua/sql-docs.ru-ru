---
title: "Поддержка для правила, триггеры, значения по умолчанию и хранимые процедуры | Документы Microsoft"
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
- Visual FoxPro ODBC driver [ODBC], stored procedures
- FoxPro ODBC driver [ODBC], commands and functions
- commands for FoxPro ODBC driver [ODBC]
- FoxPro ODBC driver [ODBC], default values
- FoxPro ODBC driver [ODBC], triggers
- stored procedures [ODBC], Visual FoxPro ODBC driver
- Visual FoxPro ODBC driver [ODBC], rules
- FoxPro commands and functions [ODBC]
- rules [ODBC]
- Visual FoxPro ODBC driver [ODBC], default values
- FoxPro ODBC driver [ODBC], rules
- functions [ODBC], Visual FoxPro
- default values [ODBC]
- Visual FoxPro ODBC driver [ODBC], commands and functions
- Visual FoxPro ODBC driver [ODBC], triggers
- FoxPro ODBC driver [ODBC], stored procedures
- Visual FoxPro commands and functions [ODBC]
ms.assetid: e449de20-d6ca-4902-9f8e-814eb6e86650
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c2fcdf0a9a7af2f34a2a0d87495d00ddf3373d3a
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2018
---
# <a name="support-for-rules-triggers-default-values-and-stored-procedures-visual-foxpro-odbc-driver"></a>Поддержка для правила, триггеры, значения по умолчанию и хранимые процедуры (Visual FoxPro драйвер ODBC)
Не удается создать правила Visual FoxPro, триггеры, значения по умолчанию или хранимых процедур с помощью драйвера ODBC для Visual FoxPro. Тем не менее приложения могут взаимодействовать с существующие правила, триггеры, значения по умолчанию или хранимых процедур, как создаются, обновляет или удаляет Visual FoxPro данные, хранящиеся в базе данных.  
  
 В следующей таблице перечислены Visual FoxPro команды и функции, которые поддерживаются драйвером ODBC для Visual FoxPro, если команды и функции существуют в правила, триггеры, значения по умолчанию или хранимых процедур.  
  
 Если ваше приложение взаимодействует с данными, правила, триггеры, значения по умолчанию, или вызывать хранимые процедуры других Visual FoxPro команд или функций, драйвер выдает ошибку. В разделе [неподдерживаемых Visual FoxPro команд и функций](../../odbc/microsoft/unsupported-visual-foxpro-commands-and-functions-visual-foxpro-odbc-driver.md) список команд и функций, не поддерживается драйвером.  
  
> [!TIP]  
>  Если вы хотите вставить условный код в правила, триггеров или хранимых процедур, которые определяет команды следует выполнять при вызове с помощью драйвера, можно использовать **(версии)** функции. **(Версии)** возврата функцией «драйвер ODBC для Visual FoxPro  *\<версии >*"при вызове с помощью драйвера.  
  
## <a name="visual-foxpro-commands-and-functions-supported-in-rules-triggers-default-values-and-stored-procedures"></a>Visual FoxPro команды и функции, поддерживаемые в правила, триггеры, значения по умолчанию и хранимые процедуры  
  
||||  
|-|-|-|  
|Оператор $|%-Оператор|& Команды|  
|& & Команда|* Команда|= Команда|  
  
## <a name="a"></a>Объект  
  
||||  
|-|-|-|  
|Функция ABS)|Функция ACOPY)|Команда Добавления таблицы|  
|Функция ADATABASES)|Функция ADBOBJECTS)|Функция AERROR)|  
|Функция ADEL)|Функция AELEMENT)|Функция ALEN)|  
|Функция AFIELDS)|Функция AINS)|ALTER TABLE - команда SQL|  
|Функция ПСЕВДОНИМ)|Функция ALLTRIM)|ДОБАВЛЕНИЕ КОМАНДЫ МАССИВА|  
|AND -оператор|ДОБАВЬТЕ команду|ДОБАВЬТЕ команду MEMO|  
|ДОБАВЛЕНИЕ КОМАНДЫ|ДОБАВЬТЕ команду Общие|Функция ASCAN)|  
|ДОБАВЬТЕ команду ПРОЦЕДУРЫ|Функция ASC)|Функция ASUBSCRIPT)|  
|Функция ASIN)|Функция ASORT)|Функция ATAN)|  
|В функции)|Функция AT_C)|Функция ATCLINE)|  
|Функция усовершенствованной Транспортной)|Функция ATCC)|Функция AUSED)|  
|Функция ATLINE)|Функция ATN2)||  
|Команда среднее|Функция ACOS)||  
  
## <a name="b"></a>B  
  
||||  
|-|-|-|  
|Команда BEGIN TRANSACTION|МЕЖДУ функция)|Функция BITNOT)|  
|Функция BITCLEAR)|Функция BITLSHIFT)|Функция BITSET)|  
|Функция BITOR)|Функция BITRSHIFT)|ПУСТОЙ команды|  
|Функция BITTEST)|Функция BITXOR)||  
|Функция BOF)|Функция BITAND)||  
  
## <a name="c"></a>C  
  
||||  
|-|-|-|  
|ВЫЧИСЛИТЬ команду|Функция КАНДИДАТА)|Функция CHR)|  
|Функция CDX)|Функция CEILING)|ЗАКРЫТЬ команд|  
|Функция CHRTRAN)|Функция CHRTRANC)|СКОПИРУЙТЕ команду ИНДЕКСОВ|  
|Функция CMONTH)|ПРОДОЛЖИТЬ команды|КОПИРОВАНИЕ СТРУКТУРЫ РАСШИРЕННЫЕ команды|  
|СКОПИРУЙТЕ команду ПРОЦЕДУРЫ|КОПИРОВАНИЕ СТРУКТУРЫ команды|КОПИРОВАНИЕ на команду|  
|Команды КОПИРОВАНИЯ ТЕГА|КОПИРОВАНИЕ на команду МАССИВА|Функция CPCONVERT)|  
|COS функции)|Команды COUNT|Функция CTOD)|  
|Функция CPCURRENT)|Функция CPDBF)|Функция CURSORSETPROP)|  
|Функция CTOT)|Функция CURSORGETPROP)||  
|Функция CURVAL)|Функция CDOW)||  
  
## <a name="d"></a>D  
  
||||  
|-|-|-|  
|Функция DATE)|Функции даты и времени)|Функция DAY)|  
|Функция DBC)|Функция DBF)|Функция DBGETPROP)|  
|Функция DBUSED)|Удаление - команды SQL|УДАЛИТЬ команду|  
|Удаление ТЕГА команды|Функция (УДАЛЕННЫЙ)|Функции по УБЫВАНИЮ)|  
|Функция DIFFERENCE)|Команда ИЗМЕРЕНИЯ|Функция места на диске)|  
|Функция ДМГ)|СДЕЛАЙТЕ СЛУЧАЙ... Команда ENDCASE|Команда|  
|WHILE... Команда ENDDO|Функция ОКА)|Функция DTOC)|  
|Функция DTOR)|Спроектируйте функции)|Функция DTOT)|  
  
## <a name="e"></a>E  
  
||||  
|-|-|-|  
|Функция (пустой)|ВЫЧИСЛИТЬ значение функции)|EXIT, команда|  
|Функция ОШИБОК)|Функция EXP)||  
|Команда ЗАВЕРШЕНИЯ ТРАНЗАКЦИИ|Функция EOF)||  
  
## <a name="f"></a>Ж  
  
||||  
|-|-|-|  
|Функция FCOUNT)|Функция FDATE)|Функция поля)|  
|Функция файла)|Функция FILTER)|Функция FLDLIST)|  
|Функция FLOCK)|Функция FLOOR)|Команда ОЧИСТКИ|  
|FOR... Команда ENDFOR|ДЛЯ функции)|НАЙТИ функции)|  
|Команда свободного таблицы|Функция FSIZE)|Функция FTIME)|  
|Функция FULLPATH)|ФУНКЦИЯ команды|Аргумент функции)|  
  
## <a name="g"></a>Ж  
  
||||  
|-|-|-|  
|СОБЕРИТЕ команду|Функция GETNEXTMODIFIED)|Команда GO/GOTO|  
|Функция GETFLDSTATE)|Функция GOMONTH)||  
|Функция GETCP)|GETENV-функция)||  
  
## <a name="h"></a>З  
  
|||  
|-|-|  
|Заголовок функции)|Функция HOUR)|  
  
## <a name="i"></a>I  
  
||||  
|-|-|-|  
|Функция IDXCOLLATE)|IF... ENDIF-команда|Функция IIF)|  
|Функция INDBC)|ИНДЕКС команды|Функция ОБЪЕМОВ)|  
|Команда INSERT SQL|Функция INT)|ISALPHA ()-функция|  
|Функция ISBLANK)|ISDIGIT ()-функция|Функция ISEXCLUSIVE)|  
|ISLEADBYTE ()-функция|ISLOWER ()-функция|Функция ISNULL)|  
|Функция ISREADONLY)|ISUPPER ()-функция||  
  
## <a name="k"></a>Л  
  
||||  
|-|-|-|  
|Функция (ключа)|Функция KEYMATCH)||  
  
## <a name="l"></a>L  
  
||||  
|-|-|-|  
|Функция (СЛЕВА)|Функция LEFTC)|Функция LIKEC)|  
|Функция LENC)|КАК и функция)|Функция БЛОКИРОВКУ)|  
|ЛОКАЛЬНАЯ командная|НАЙДИТЕ команду|Функция ПОДСТАНОВКИ)|  
|Функция LOG)|Функция LOG10)|Функция LTRIM)|  
|Функция LOWER)|Команда LPARAMETERS||  
|Функция LUPDATE)|Функция LEN)||  
  
## <a name="m"></a>M  
  
||||  
|-|-|-|  
|_MLINE системной памяти переменной|Функция MAX)|Функция многомерных Выражений)|  
|Функция МДГ)|Функция MEMLINES)|Функция сообщения)|  
|Функция MIN)|Функция (минуты)|Функция MLINE)|  
|Функция MOD)|Функция MONTH)|Функция MTON)|  
  
## <a name="n"></a>Нет  
  
||||  
|-|-|-|  
|Функция NDX)|НОРМАЛИЗОВАТЬ функции)|Оператор NOT|  
|Команда Примечание|Функция NTOM)|Функция NVL)|  
  
## <a name="o"></a>O  
  
||||  
|-|-|-|  
|ПРОИСХОДИТ, функция)|Функция OLDVAL)|Ошибка КОМАНДЫ|  
|НА команда клавиши|В функции)|Команда ОТКРЫТЬ базу данных|  
|Оператор или|Функция ПОРЯДКА)|Функция операционной системы)|  
  
## <a name="p"></a>P  
  
||||  
|-|-|-|  
|Команда ПАКЕТА|ПАРАМЕТРЫ функции)|Функция ОПЛАТЫ)|  
|ПАРАМЕТРЫ команды|Функция (ОСНОВНОЙ)|Команда PRIVATE|  
|Функция PI)|Функция программы)|Функция (ПРАВИЛЬНОЕ)|  
|Команда ПРОЦЕДУРЫ|Функция PV)||  
|ОТКРЫТЫЕ команды|PADL () &#124; PADR () &#124; Функции PADC)||  
  
## <a name="r"></a>Чтение  
  
||||  
|-|-|-|  
|Функция RAND)|Функция RAT)|Функция RATC)|  
|Функция RATLINE)|ПОМНИТЕ, команда|Функция RECCOUNT)|  
|Функция RECNO)|Функция: RECSIZE)|Команда язык|  
|Функция СВЯЗИ)|УДАЛИТЬ команду таблицы|Заменить-команда|  
|ЗАМЕНИТЕ КОМАНДЫ МАССИВА|REPLICATE-функция)|ПОВТОРИТЕ команду|  
|ВОЗВРАЩАЕТ команды|Функция (СПРАВА)|Функция RIGHTC)|  
|Функция RLOCK)|Команды ОТКАТА|Функция ROUND)|  
|Функция RTOD)|Функция RTRIM)||  
  
## <a name="s"></a>S  
  
||||  
|-|-|-|  
|СКАНИРОВАТЬ... Команда ENDSCAN|Точечная диаграмма, команда|Функция сек)|  
|Функция СЕКУНД)|Поиск|SEEK-функция)|  
|ВЫБЕРИТЕ команду|Функция (SELECT)|Команда SELECT SQL|  
|BLOCKSIZE команды SET|ВЫПОЛНЕНИЯ команды SET|Команда SET ВЕКА|  
|COLLATE команды SET|Команда SET базы данных|Дата команды SET|  
|По умолчанию команды SET|УДАЛЕННЫЕ команды SET|ТОЧНОЕ команды SET|  
|ЭКСКЛЮЗИВНОЕ команды SET|Команда SET FDOW|ПОЛЯ команды SET|  
|Команда SET-ФИЛЬТРА|Основные команды SET|FULLPATH команды SET|  
|Команда SET FWEEK|ЗАДАЙТЕ часы команды|ИНДЕКС команды SET|  
|БЛОКИРОВКА команды SET|MULTILOCKS команды SET|ЗАДАЙТЕ при выполнении команды|  
|Команда SET NOCPTRANS|Команда SET-уведомление|Значение NULL команды SET|  
|ОПТИМИЗИРОВАТЬ команды SET|ПОРЯДОК команды SET|ПУТЬ команды SET|  
|Команда SET-ПРОЦЕДУРЫ|Команда SET отношения|НАБОР отношения OFF команда|  
|Повторная ОБРАБОТКА команды SET|ЗАДАЙТЕ команду "Пропустить"|Команда SET UDFPARMS|  
|УНИКАЛЬНЫЙ команды SET|Команда SET тома|Функция SET)|  
|Функция SETFLDSTATE)|Функция SIGN)|Функция SIN)|  
|Команду "Пропустить"|Команда SORT|Функция SPACE)|  
|Функция SQRT)|Команда ХРАНИЛИЩА|Функция STR)|  
|Функция STRCONV)|Функция STRTRAN)|Функция STUFF)|  
|Функция STUFFC)|Функция SUBSTR)|Функция SUBSTRC)|  
|Команда СУММИРОВАТЬ по|Функция sys(2011)||  
  
## <a name="t"></a>T  
  
||||  
|-|-|-|  
|_TALLY системной памяти переменной|_TRIGGERLEVEL системной памяти переменной|Функция TAGCOUNT)|  
|Функция TABLEUPDATE)|Функция ТЕГ)|ЦЕЛЕВОЙ функции)|  
|Функция TAGNO)|Функция TAN)|TRIM, функция)|  
|Функция времени)|Команда итог|Функция TXNLEVEL)|  
|Функция TTOC)|Функция TTOD)||  
|ТИП функции)|Функция TABLEREVERT)||  
  
## <a name="u"></a>U  
  
||||  
|-|-|-|  
|Функция (УНИКАЛЬНЫЙ)|UNLOCK, команда|Используйте команду|  
|Команда обновления|Функция (верхний)||  
|ИСПОЛЬЗУЕТСЯ функция)|Обновление - команд SQL||  
  
## <a name="v"></a>V  
  
||||  
|-|-|-|  
|Функция VAL)|ВЕРСИЯ функции)||  
  
## <a name="w"></a>W  
  
||||  
|-|-|-|  
|Функция НЕДЕЛИ)|||  
  
## <a name="y"></a>Да  
  
||||  
|-|-|-|  
|Функция YEAR)|||  
  
## <a name="z"></a>Z  
  
||||  
|-|-|-|  
|Команда ZAP|||
