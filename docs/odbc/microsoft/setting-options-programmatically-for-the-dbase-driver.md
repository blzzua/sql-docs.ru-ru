---
title: "Параметры Программная установка для драйвера dBASE | Документы Microsoft"
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
- Jet-based ODBC drivers [ODBC], DBasedriver
- desktop database drivers [ODBC], DBasedriver
- DBase driver [ODBC], setting options programmatically
- ODBC desktop database drivers [ODBC], DBasedriver
ms.assetid: 336d0fd4-5448-4d8c-b7d9-49e857228e36
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 79bf64c2f577935b26dcb64b93e7f3567924291b
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="setting-options-programmatically-for-the-dbase-driver"></a>Параметры Программная установка для драйвера dBASE
|Параметр|Description|Метод|  
|------------|-----------------|------------|  
|Приблизительное число строк|Определяет, округляются ли статистика размер таблицы. Этот параметр применяется ко всем источникам данных, использующие драйвер ODBC.|Чтобы задать этот параметр динамически, используйте **СТАТИСТИКИ** ключевое слово в вызове [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|  
|Порядок сортировки|Последовательность, в которой отсортированы поля.<br /><br /> Последовательность может быть: ASCII (по умолчанию) или International.|Чтобы задать этот параметр динамически, используйте **COLLATINGSEQUENCE** ключевое слово в вызове [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|  
|Имя источника данных|Имя, идентифицирующее источник данных, например Payroll или службу.|Чтобы задать этот параметр динамически, используйте **DSN** ключевое слово в вызове [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|  
|база данных|Можно настроить источник данных Microsoft Access, без выбора или создания базы данных. Если база данных не предоставляется при установке, пользователям будет предложено выбрать файл базы данных при подключении к источнику данных.|Чтобы задать этот параметр динамически, используйте **DBQ** ключевое слово в вызове [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|  
|Description|Необязательное описание данных в источнике данных; Например «привлекает даты, журнал зарплат и текущий Обзор всех сотрудников.»|Чтобы задать этот параметр динамически, используйте **описание** ключевое слово в вызове [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|  
|Монопольно|Если **монопольного** установлен, базы данных будут открыты в монопольном режиме и может осуществляться одновременно только одним пользователем. Повышение производительности достигается, когда оно работает в режиме монопольного доступа.|Чтобы задать этот параметр динамически, используйте **МОНОПОЛЬНОГО** ключевое слово в вызове [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|  
|Время ожидания страницы|Указывает период времени, в десятые доли секунды, страницы (если не используется), остаются в буфере перед удалением. Значение по умолчанию — 600 десятые доли секунды (60 секунд). Этот параметр применяется ко всем источникам данных, использующие драйвер ODBC.<br /><br /> Время ожидания страницы не может быть 0, из-за задержки, обусловленные. Время ожидания страницы не может быть меньше специфические задержку, даже если параметр времени ожидания страницы имеет значение ниже этого значения.|Чтобы задать этот параметр динамически, используйте **PAGETIMEOUT** ключевое слово в вызове [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|  
|Только для чтения|Определяет базу данных только для чтения.|Чтобы задать этот параметр динамически, используйте **READONLY** ключевое слово в вызове [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|  
|Выберите каталог|Отображает диалоговое окно, где можно выбрать каталог, содержащий файлы, которым требуется доступ.<br /><br /> При определении каталога источника данных, укажите каталог, где находятся наиболее часто используемых файлов. Драйвер ODBC использует этот каталог в качестве каталога по умолчанию. Скопируйте в эту папку, другие файлы, если часто используются. Кроме того можно указывать имена файлов в инструкции SELECT с именем каталога:<br /><br /> ВЫБЕРИТЕ \* ИЗ C:\MYDIR\EMP<br /><br /> Или можно указать новый каталог по умолчанию с помощью **SQLSetConnectOption** функцию с параметром SQL_CURRENT_QUALIFIER.|Чтобы задать этот параметр динамически, используйте **его значения** ключевое слово в вызове [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|  
|Отображение удаленных строк|Определяет, извлечь или находится на строки, которые были помечены как удаленные. Если этот флажок снят, удаленные строки не отображаются. Если флажок установлен, удаленные строки рассматриваются таким же, как не удаленных строк. Значение по умолчанию снят.|Чтобы задать этот параметр динамически, используйте **DELETED** ключевое слово в вызове [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|
