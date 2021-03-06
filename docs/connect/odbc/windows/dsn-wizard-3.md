---
title: "Экран мастера 3 (драйвер ODBC для SQL Server) источника данных | Документы Microsoft"
ms.custom: 
ms.date: 09/27/2017
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
ms.assetid: 76326eeb-1144-4b9f-85db-50524c655d30
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a0a97971dcd8a16a2ac15b1013dbbe96a43f21c0
ms.sourcegitcommit: 99102cdc867a7bdc0ff45e8b9ee72d0daade1fd3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/11/2018
---
# <a name="data-source-wizard-screen-3"></a>Мастер источника данных 3

Укажите базу данных по умолчанию, различные параметры ANSI, которые будут использоваться драйвером, и имя зеркального сервера.

## <a name="options"></a>Параметры

### <a name="change-the-default-database-to"></a>Изменение базы данных по умолчанию

Указывает имя базы данных по умолчанию для любого соединения, установленного с помощью этого источника данных. Если данное поле пустое, соединения будут использовать базу данных по умолчанию для идентификатора входа на сервере. Если это поле выбрано, то база данных, указанная в этом поле, заменяет базу данных по умолчанию для идентификатора входа. Если **присоединить файл базы данных** указано имя первичного файла, база данных, описанная в первичном файле подключен как базы данных, используя имя базы данных, указанной в **изменить базу данных по умолчанию для**поле.

Более эффективно указывать базу данных по умолчанию для идентификатора входа, чем указывать ее в источнике данных ODBC.

### <a name="mirror-server"></a>Зеркальный сервер

Указывает имя партнера по обеспечению отработки отказа базы данных, для которой будет включено зеркальное отображение. Если имя базы данных не содержится в **изменить базу данных по умолчанию для** базы данных по умолчанию будет прямоугольник или именем, отображаемым **зеркальный сервер** неактивна.

Дополнительно можно указать имя участника-службы сервера для зеркального сервера. Имя участника-службы зеркального сервера используется для взаимной проверки подлинности клиента и сервера.

### <a name="attach-database-filename"></a>Присоединить файл базы данных

Указывает имя первичного файла для присоединяемой базы данных. Эта база данных присоединяется и используется в качестве базы данных по умолчанию для источника данных. Укажите полный путь и имя первичного файла. Имя базы данных, указанной в **изменить базу данных по умолчанию для** используется в качестве имени для присоединяемой базы данных.

### <a name="use-ansi-quoted-identifiers"></a>Заключенные в кавычки идентификаторы в формате ANSI

Указывает, что будет включен параметр QUOTED_IDENTIFIER при подключении драйвера ODBC для SQL Server. Если этот флажок установлен, SQL Server использует правила ANSI, касающиеся кавычек. Двойные кавычки можно использовать только для идентификаторов, например имен столбцов или таблиц. Строки символов должны быть заключены в одиночные кавычки:

```
SELECT "LastName"
FROM "Person.Contact"
WHERE "LastName" = 'O''Brien'
```

Если данный флажок не установлен, то в приложениях, использующих заключенные в кавычки идентификаторы (например, в программе Microsoft Query, поставляющейся с Microsoft Excel), возникнут ошибки при попытке сформировать инструкции SQL, содержащие заключенные в кавычки идентификаторы.

### <a name="use-ansi-nulls-paddings-and-warnings"></a>Использование значения NULL, шаблоны и предупреждения ANSI

Указывает, что установить параметры ANSI_NULLS, ANSI_WARNINGS и ANSI_PADDINGS на при подключении драйвера ODBC для SQL Server.

Если включен параметр ANSI_NULLS, сервер принудительно применяет правила ANSI при сравнении столбцов со значениями NULL. Для всех сравнений со значениями NULL необходимо использовать синтаксис ANSI: «IS NULL» или «IS NOT NULL». Синтаксис Transact-SQL «= NULL» не поддерживается.

Параметр ANSI_WARNINGS включен SQL Server выдает предупреждающие сообщения для условий, нарушающих правила ANSI, но не нарушающих правила Transact-SQL. Примерами таких ошибок является усечение данных при выполнении инструкций INSERT или UPDATE либо обнаружение значения NULL при выполнении агрегатной функции. 

Параметр ANSI_PADDING включен, завершающие пробелы в **varchar** значений и завершающие нули **varbinary** значения не удаляются автоматически.

### <a name="application-intent"></a>Намерение приложения

Объявляет тип рабочей нагрузки приложения при соединении с сервером. Возможными значениями являются **ReadOnly** и **ReadWrite**.

### <a name="multi-subnet-failover"></a>Отработка отказа в нескольких подсетях.

Если приложение пытается подключиться к высокого уровня доступности, аварийного восстановления (группы доступности AlwaysOn) группе доступности (AG) в разных подсетях, включение **отказоустойчивых кластеров с несколькими подсетями.** Настраивает драйвер ODBC для SQL Server для обеспечения более быстрое обнаружение и подключение к серверу (активного).

### <a name="transparent-network-ip-resolution"></a>Разрешение IP-адресов для прозрачной сети.

Изменяет поведение **отказоустойчивых кластеров с несколькими подсетями** позволяет ускорить восстановление соединения во время отработки отказа. В разделе [с помощью прозрачного разрешение IP-адресов сети](../../../connect/odbc/using-transparent-network-ip-resolution.md) для получения дополнительной информации.

### <a name="column-encryption"></a>Шифрование столбца.

Включает автоматическую расшифровку и передаче данных в и из столбцов, зашифрованных с помощью шифрования [постоянного шифрования](../../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md) функция доступна в SQL Server 2016 и более поздней версии.

### <a name="use-fmtonly-metadata-discovery"></a>Используйте FMTONLY обнаружение метаданных:

Используйте метод обнаружения метаданных устаревших SET FMTONLY, при подключении к SQL Server 2012 или более поздней версии. Включить эту возможность только при использовании запросов, не поддерживаемых [sp_describe_first_result_set](../../../relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql.md), например, содержащие временных таблиц. 

### <a name="next"></a>Дальше

Переход к следующей странице мастера.

### <a name="back"></a>Назад

Возврат к предыдущему экрану мастера.

## <a name="next-steps"></a>Следующие шаги

[Экран 2 мастера источников данных](../../../connect/odbc/windows/dsn-wizard-2.md)

[Мастер источника данных 4](../../../connect/odbc/windows/dsn-wizard-4.md)
