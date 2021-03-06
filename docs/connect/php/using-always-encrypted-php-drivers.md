---
title: Использование постоянного шифрования с помощью драйверов PHP для SQL Server | Документы Microsoft
ms.date: 01/08/2018
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: php
ms.suite: sql
ms.custom: ''
ms.technology:
- drivers
ms.topic: article
author: v-kaywon
ms.author: v-kaywon
manager: mbarwin
ms.workload: Inactive
ms.openlocfilehash: 588a0471866b1b33a3e485b321193edfd0c9187d
ms.sourcegitcommit: 2e130e9f3ce8a7ffe373d7fba8b09e937c216386
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2018
---
# <a name="using-always-encrypted-with-the-php-drivers-for-sql-server"></a>Использование постоянного шифрования с помощью драйверов PHP для SQL Server
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

## <a name="applicable-to"></a>Применимо к
 -   5.2 драйверы Майкрософт для PHP для SQL Server
 
## <a name="introduction"></a>Введение

Этой статье содержатся сведения о разработке приложений PHP с помощью [Always Encrypted (ядро СУБД)](../../relational-databases/security/encryption/always-encrypted-database-engine.md) и [драйверы PHP для SQL Server](../../connect/php/Microsoft-php-driver-for-sql-server.md).

Функция Always Encrypted позволяет шифровать конфиденциальные данные в клиентских приложениях, не раскрывая данные или ключи шифрования для SQL Server или Базы данных SQL Azure. Always Encrypted драйвер с поддержкой, такие как драйвер ODBC для SQL Server прозрачно шифрует и расшифровывает конфиденциальные данные в клиентском приложении. Драйвер автоматически определяет, какие параметры запроса соответствуют важным столбцам базы данных (защищенным с помощью Always Encrypted), и шифрует значения этих параметров перед передачей данных в SQL Server или Базу данных SQL Azure. Аналогичным образом драйвер прозрачно расшифровывает данные, полученные из зашифрованных столбцов базы в результатах запроса. Дополнительные сведения см. в разделе [Always Encrypted (ядро СУБД)](../../relational-databases/security/encryption/always-encrypted-database-engine.md). Драйверы PHP для SQL Server используют драйвер ODBC для SQL Server для шифрования конфиденциальных данных.

## <a name="prerequisites"></a>предварительные требования

 -   Настройте функцию постоянного шифрования в базе данных. В этой конфигурации участвует подготовки ключей постоянного шифрования и настройке шифрования для выбранных столбцов базы данных. Если в базе данных постоянное шифрование еще не настроено, следуйте инструкциям в разделе [Приступая к работе с постоянным шифрованием](../../relational-databases/security/encryption/always-encrypted-database-engine.md#getting-started-with-always-encrypted). В частности база данных должна содержать определения метаданных для главного ключа столбца (CMK), ключ шифрования столбца (CEK) и таблицу, содержащую один или несколько столбцов, зашифрованных с помощью этого CEK.
 -   Убедитесь, что на компьютере разработки установлен драйвер ODBC для SQL Server версии 17 и выше. Дополнительные сведения см. в разделе [драйвер ODBC для SQL Server](../../connect/odbc/microsoft-odbc-driver-for-sql-server.md).

## <a name="enabling-always-encrypted-in-a-php-application"></a>Включение постоянного шифрования в приложения PHP

Является самым простым способом включения шифрования параметров, предназначенных для зашифрованных столбцов и расшифровки результатов запроса, задав значение `ColumnEncryption` ключевое слово строки подключения для `Enabled`. Ниже приведены примеры включения постоянного шифрования в драйвере SQLSRV и PDO_SQLSRV:

SQLSRV:
```
$connectionInfo = array("Database"=>$databaseName, "UID"=>$uid, "PWD"=>$pwd, "ColumnEncryption"=>"Enabled");
$conn = sqlsrv_connect($server, $connectionInfo);
```

PDO_SQLSRV:
```
$connectionInfo = "Database = $databaseName; ColumnEncryption = Enabled;";
$conn = new PDO("sqlsrv:server = $server; $connectionInfo", $uid, $pwd);
```

Включение постоянного шифрования недостаточно для шифрования или расшифровки для успешного выполнения; также необходимо убедиться, что:
 -   Приложение имеет VIEW ANY COLUMN MASTER KEY DEFINITION и VIEW ANY COLUMN ENCRYPTION KEY DEFINITION базы данных разрешения, необходимые для доступа к метаданным о ключах постоянного шифрования в базе данных. Дополнительные сведения см. в разделе [базы данных разрешения](../../relational-databases/security/encryption/always-encrypted-database-engine.md#database-permissions).
 -   Приложения могут обращаться к CMK, который защищает столбца для запрашиваемых зашифрованных столбцов. Это требование не зависит от поставщика хранилища ключей, в котором хранится CMK. Дополнительные сведения см. в разделе [работа с хранилищами главных ключей столбцов](#working-with-column-master-key-stores).

## <a name="retrieving-and-modifying-data-in-encrypted-columns"></a>Получение и изменение данных в зашифрованных столбцах

После включения постоянного шифрования для подключения, можно использовать стандартные API-интерфейсы SQLSRV (см. [Справочник по API для драйвера SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)) или PDO_SQLSRV API (в разделе [Справочник по API для драйвера PDO_SQLSRV](../../connect/php/pdo-sqlsrv-driver-reference.md)) для извлечения или изменения данных в столбцах зашифрованной базы данных. При условии, что приложение имеет разрешения, необходимые базы данных можно получить доступ к главному ключу столбца, драйвер шифрует все параметры запроса, предназначенные для зашифрованных столбцов и расшифровать данные, полученные из зашифрованных столбцов прозрачно в поведение приложения, как если бы столбцы не были зашифрованы.

Если постоянное шифрование не включено, сбой запросы с параметрами, предназначенными для зашифрованных столбцов. Можно по-прежнему получить данные из зашифрованных столбцов, при условии, что запрос не имеет параметров предназначенные для зашифрованных столбцов. Тем не менее драйвер не пытаться любой расшифровки и приложение получает двоичные зашифрованные данные (в виде массивов байтов).

В следующей таблице перечислены поведение запросов в зависимости от того, является ли постоянное шифрование включено или нет:

| Характеристика запроса | Постоянное шифрование включено, и приложение может получить доступ к ключам и метаданным ключей | Постоянное шифрование включено, и приложение не может получить доступ к ключам и метаданным ключей | Постоянное шифрование отключено | | Параметры, предназначенные для зашифрованных столбцов. | Значения параметров прозрачно шифруются. | Ошибка | Ошибка | | Получение данных из зашифрованных столбцов без параметров, предназначенных для зашифрованных столбцов. | Результаты из зашифрованных столбцов прозрачно расшифровываются. Приложение получает значения столбца в открытом тексте. | Ошибка | Результаты из зашифрованных столбцов не расшифровываются. Приложение получает зашифрованные значения в виде байтовых массивов. |
 
В следующих примерах показано получение и изменение данных в зашифрованных столбцах. В этих примерах таблицу со следующей схемой. Столбцы SSN и BirthDate зашифрованы.
```
CREATE TABLE [dbo].[Patients](
 [PatientId] [int] IDENTITY(1,1),
 [SSN] [char](11) COLLATE Latin1_General_BIN2
 ENCRYPTED WITH (ENCRYPTION_TYPE = DETERMINISTIC,
 ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256',
 COLUMN_ENCRYPTION_KEY = CEK1) NOT NULL,
 [FirstName] [nvarchar](50) NULL,
 [LastName] [nvarchar](50) NULL,
 [BirthDate] [date]
 ENCRYPTED WITH (ENCRYPTION_TYPE = RANDOMIZED,
 ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256',
 COLUMN_ENCRYPTION_KEY = CEK1) NOT NULL
 PRIMARY KEY CLUSTERED ([PatientId] ASC) ON [PRIMARY])
 GO
```

### <a name="data-insertion-example"></a>Пример вставки данных

Следующие примеры демонстрируют, как используются драйверы SQLSRV и PDO_SQLSRV вставить строку в таблице пациента. Обратите внимание на следующие моменты:
 -   В образце кода нет ничего, связанного с шифрованием. Драйвер автоматически обнаруживает и шифрует значения параметров SSN и BirthDate, которые предназначенные для зашифрованных столбцов. Этот механизм делает шифрование прозрачным для приложения.
 -   Значениях, вставляемых в столбцы базы данных, включая зашифрованные столбцы передаются как связанные параметры. Хотя с помощью параметров является необязательным при отправке значений в незашифрованные столбцы (хотя настоятельно рекомендуется, так как он помогает предотвратить атаки SQL injection), он необходим для значений, предназначенных для зашифрованных столбцов. При значениях, вставляемых в столбцы SSN или BirthDate были переданы в качестве литералов, внедренных в инструкции запроса, запрос завершится ошибкой, так как драйвер не будет пытаться шифрования, либо иначе обработать литералы в запросах. В результате сервер отклонит их как несовместимые с зашифрованными столбцами.
 -   При вставке значений с помощью параметров привязки, тип SQL, идентичный тип данных целевого столбца или поддерживается, преобразование в тип данных целевого столбца должны передаваться в базу данных. Это требование обусловлено постоянное шифрование поддерживает несколько преобразований типа (Дополнительные сведения см. в разделе [Always Encrypted (ядро СУБД)](../../relational-databases/security/encryption/always-encrypted-database-engine.md)). Два драйверы PHP SQLSRV и PDO_SQLSRV, каждый из них имеет механизм, чтобы помочь пользователю определить тип SQL значения. Таким образом пользователь не нужно явно указать тип SQL.
  -   Драйвер SQLSRV пользователь имеет два параметра:
   -   Используют драйвер PHP, чтобы определить и установить правильный тип SQL. В этом случае пользователь должен использовать `sqlsrv_prepare` и `sqlsrv_execute` для выполнения параметризованного запроса.
   -   Явно задайте тип SQL.
  -   Для драйвера PDO_SQLSRV пользователь не имеет параметр, чтобы явно задать тип SQL для параметра. Драйвер PDO_SQLSRV автоматически помогают пользователю определить тип SQL, при привязке параметра.
 -   Для драйверов определить тип SQL существуют некоторые ограничения:
  -   Драйвер SQLSRV:
   -   Если пользователю драйвера, чтобы определить типы SQL для зашифрованных столбцов, пользователь должен использовать `sqlsrv_prepare` и `sqlsrv_execute`.
   -   Если `sqlsrv_query` является основной, пользователь отвечает за задание типов SQL для всех параметров. Указанный тип SQL должен включать длину строки для строковых типов и масштаба и точности для десятичного типа.
  -   PDO_SQLSRV Driver:
   -   Атрибут инструкции `PDO::SQLSRV_ATTR_DIRECT_QUERY` не поддерживается в параметризованном запросе.
   -   Атрибут инструкции `PDO::ATTR_EMULATE_PREPARES` не поддерживается в параметризованном запросе.
   
Драйвер SQLSRV и [sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md):
```
// insertion into encrypted columns must use a parameterized query
$query = "INSERT INTO [dbo].[Patients] ([SSN], [FirstName], [LastName], [BirthDate]) VALUES (?, ?, ?, ?)";
$ssn = "795-73-9838";
$firstName = "Catherine";
$lastName = "Abel;
$birthDate = "1996-10-19";
$params = array($ssn, $firstName, $lastName, $birthDate);
// during sqlsrv_prepare, the driver determines the SQL types for each parameter and pass them to SQL server
$stmt = sqlsrv_prepare($conn, $query, $params);
sqlsrv_execute($stmt);
```

Драйвер SQLSRV и [sqlsrv_query](../../connect/php/sqlsrv-query.md):
```
// insertion into encrypted columns must use a parameterized query
$query = "INSERT INTO [dbo].[Patients] ([SSN], [FirstName], [LastName], [BirthDate]) VALUES (?, ?, ?, ?)";
$ssn = "795-73-9838";
$firstName = "Catherine";
$lastName = "Abel";
$birthDate = "1996-10-19";
// need to provide the SQL types for ALL parameters  
// note the SQL types (including the string length) have to be the same at the column definition
$params = array(array(&$ssn, null, null, SQLSRV_SQLTYPE_CHAR(11)),
                array(&$firstName, null, null, SQLSRV_SQLTYPE_NVARCHAR(50)),
                array(&$lastName, null, null, SQLSRV_SQLTYPE_NVARCHAR(50)),
                array(&$birthDate, null, null, SQLSRV_SQLTYPE_DATE));
sqlsrv_query($conn, $query, $params);
```

Драйвер PDO_SQLSRV и [PDO::prepare](../../connect/php/pdo-prepare.md):
```
// insertion into encrypted columns must use a parameterized query
$query = "INSERT INTO [dbo].[Patients] ([SSN], [FirstName], [LastName], [BirthDate]) VALUES (?, ?, ?, ?)";
$ssn = "795-73-9838";
$firstName = "Catherine";
$lastName = "Able";
$birthDate = "1996-10-19";
// during PDO::prepare, the driver determines the SQL types for each parameter and pass them to SQL server
$stmt = $conn->prepare($query);
$stmt->bindParam(1, $ssn);
$stmt->bindParam(2, $firstName);
$stmt->bindParam(3, $lastName);
$stmt->bindParam(4, $birthDate);
$stmt->execute();
```

### <a name="plaintext-data-retrieval-example"></a>Пример извлечения данных открытым текстом

В следующих примерах демонстрируется фильтрация данных на основе зашифрованных значений и получение данных открытого текста из зашифрованных столбцов с использованием драйверов SQLSRV и PDO_SQLSRV. Обратите внимание на следующие моменты:
 -   Значение, используемое в предложении WHERE для фильтрации по столбцу SSN должен передать с помощью параметра привязки, чтобы драйвер мог его прозрачно зашифровать перед отправкой на сервер.
 -   При выполнении запроса со связанными параметрами, драйверы PHP автоматически определяет тип SQL для пользователя, если пользователь явно не указывает тип SQL при использовании драйвера SQLSRV.
 -   Все значения, выводимые программой, в виде обычного текста, так как драйвер прозрачно расшифровывает данные, полученные из столбцов SSN и BirthDate.
 
Примечание: Запросы могут выполнять сравнение на равенство по зашифрованным столбцам только в том случае, если шифрование является детерминированным. Дополнительные сведения см. в разделе [Выбор детерминированного или случайного шифрования](../../relational-databases/security/encryption/always-encrypted-database-engine.md#selecting--deterministic-or-randomized-encryption).

SQLSRV:
```
// since SSN is an encrypted column, need to pass the value in the WHERE clause through bind parameter
$query = "SELECT [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE [SSN] = ?";
$ssn = "795-73-9838";
$stmt = sqlsrv_prepare($conn, $query, array(&$ssn));
// during sqlsrv_execute, the driver encrypts the ssn value and passes it to the database
sqlsrv_execute($stmt);
// fetch like usual
$row = sqlsrv_fetch_array($stmt);
```

PDO_SQLSRV:
```
// since SSN is an encrypted column, need to pass the value in the WHERE clause through bind parameter
$query = "SELET [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE [SSN] = ?";
$ssn = "795-73-9838";
$stmt = $conn->prepare($query);
$stmt->bindParam(1, $ssn);
// during PDOStatement::execute, the driver encrypts the ssn value and passes it to the database
$stmt->execute();
// fetch like usual
$row = $stmt->fetch();
```

### <a name="ciphertext-data-retrieval-example"></a>Пример извлечения данных зашифрованного текста

Если постоянное шифрование не включено, запрос может получать данные из зашифрованных столбцов, пока для него не будут указаны параметры, предназначенные для зашифрованных столбцов.

В следующих примерах выполняется извлечение двоичных зашифрованных данных из зашифрованных столбцов с использованием драйверов SQLSRV и PDO_SQLSRV. Обратите внимание на следующие моменты:
 -   Как постоянное шифрование не включено в строке подключения, запрос возвращает зашифрованные значения SSN и BirthDate в виде байтовых массивов (программа преобразует значения в строки).
 -   Запрос, получающий данные из зашифрованных столбцов с отключенным постоянным шифрованием, может иметь параметры при условии, что ни один из параметров не предназначен для зашифрованного столбца. Следующий запрос выполняет фильтрацию по LastName, который не зашифрован в базе данных. Если запрос фильтрует по SSN или BirthDate, выполнение запроса завершится ошибкой.
 
SQLSRV:
```
$query = "SELET [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE [LastName] = ?";
$lastName = "Abel";
$stmt = sqlsrv_prepare($conn, $query, array(&$lastName));
sqlsrv_execute($stmt);
$row = sqlsrv_fetch_array($stmt);
```

PDO_SQLSRV:
```
$query = "SELET [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE [LastName] = ?";
$lastName = "Abel";
$stmt = $conn->prepare($query);
$stmt->bindParam(1, $lastName);
$stmt->execute();
$row = $stmt->fetch();
```

### <a name="avoiding-common-problems-when-querying-encrypted-columns"></a>Как избежать распространенных проблем при запросе зашифрованных столбцов

В этом разделе описываются общие категории ошибок, при запросе зашифрованных столбцов из приложений PHP и приводятся рекомендации о том, как их избежать.

#### <a name="unsupported-data-type-conversion-errors"></a>Ошибки преобразования неподдерживаемых типов данных

Постоянное шифрование поддерживает несколько преобразований для зашифрованных типов данных. В разделе [Always Encrypted (ядро СУБД)](../../relational-databases/security/encryption/always-encrypted-database-engine.md) подробный список поддерживаемых преобразований типов. Чтобы избежать ошибок при преобразовании типов данных, сделайте следующее:
 -   При использовании драйвера SQLSRV с `sqlsrv_prepare` и `sqlsrv_execute` тип SQL, а также размер столбца и количество цифр дробной части параметра определяется автоматически.
 -   При использовании драйвера PDO_SQLSRV для выполнения запроса, также автоматически определяется тип SQL с размер столбца и количество цифр дробной части параметра
 -   При использовании драйвера SQLSRV с `sqlsrv_query` для выполнения запроса:
  -   SQL тип параметра — либо точно совпадает с типом целевого столбца или поддерживается преобразование из типа SQL для типа столбца.
  -   Точность и масштаб параметров, предназначенных для столбцов `decimal` и `numeric` типов данных SQL Server совпадает с точностью и масштабом настройки для целевого столбца.
  -   Точность параметров, предназначенных для столбцов `datetime2`, `datetimeoffset`, или `time` типов данных SQL Server не превышает точность для целевого столбца, в запросах, которые изменяют целевого столбца.
 -   Не используйте атрибуты инструкции PDO_SQLSRV `PDO::SQLSRV_ATTR_DIRECT_QUERY` или `PDO::ATTR_EMULATE_PREPARES` в параметризованном запросе
 
#### <a name="errors-due-to-passing-plaintext-instead-of-encrypted-values"></a>Ошибки, возникающие из-за передачи значений в виде открытого текста, а не в зашифрованном виде

Любое значение, предназначенное для зашифрованного столбца должен быть зашифрованы перед отправкой на сервер. Предпринята попытка вставки, изменения или фильтрации по значение открытого текста в зашифрованном столбце приведет к ошибке. Чтобы избежать таких ошибок, проверьте следующее.
 -   Постоянное шифрование включено (в строке подключения значение `ColumnEncryption` ключевое слово `Enabled`).
 -   Параметр привязки используется для отправки данных, предназначенных для зашифрованных столбцов. В следующем примере запрос, который неправильно фильтрует по литералу или константе в зашифрованном столбце (SSN):
```
$query = "SELET [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE SSN='795-73-9838'";
```

## <a name="controlling-performance-impact-of-always-encrypted"></a>Управление влиянием постоянного шифрования на производительность

Так как постоянное шифрование — это технология шифрования на стороне клиента, большую нагрузку на производительность отражается на стороне клиента, а не в базе данных. Помимо затрат на операции шифрования и дешифрования являются другие источники нагрузки на стороне клиента:
 -   Дополнительных циклов приема-передачи в базу данных для извлечения метаданных для параметров запроса.
 -   Вызовы хранилища главных ключей столбцов для доступа к главному ключу столбца.
 
### <a name="round-trips-to-retrieve-metadata-for-query-parameters"></a>Циклов приема-передачи для извлечения метаданных для параметров запроса

Если для соединения включено постоянное шифрование, драйвер ODBC по умолчанию вызывает [sys.sp_describe_parameter_encryption](../../relational-databases/system-stored-procedures/sp-describe-parameter-encryption-transact-sql.md) для каждого параметризованного запроса, передавая инструкцию запроса (без значений параметров) для SQL Server . Эта хранимая процедура анализирует инструкцию запроса, чтобы узнать, если любой из параметров должен быть зашифрован и если да, возвращает связанные с шифрованием сведения для каждого параметра, чтобы драйвер мог зашифровывать их.

Так как драйверы PHP позволяет привязать параметр в подготовленной инструкции без предоставления SQL введите, при привязке параметра в соединении с поддержкой постоянного шифрования, вызовите драйверы PHP [SQLDescribeParam](../../odbc/reference/syntax/sqldescribeparam-function.md) на параметр для получения типа SQL, размер столбца и десятичных цифр. Метаданные затем используется для вызова [SQLBindParameter]( ../../odbc/reference/syntax/sqlbindparameter-function.md). Эти дополнительные `SQLDescribeParam` вызовы не требуют лишних обращений к базе данных, как драйвер ODBC уже хранится сведения на стороне клиента при `sys.sp_describe_parameter_encryption` был вызван.

Предыдущего поведения обеспечить высокий уровень прозрачности для клиентского приложения (и разработчику приложений) требуется знать, какие запросы получают доступ к зашифрованным столбцам, при условии, что значения, предназначенные для зашифрованных столбцов передаются драйверу в параметры.

В отличие от драйвера ODBC для SQL Server Включение постоянного шифрования на уровне инструкции или запроса пока не поддерживается в драйверах PHP. 

### <a name="column-encryption-key-caching"></a>Кэширование ключа шифрования столбца

Чтобы уменьшить количество вызовов к хранилищу главных ключей столбцов для расшифровки ключей шифрования столбца (CEK), драйвер кэширует столбца открытым текстом в памяти. После получения зашифрованного ключа CEK (ECEK) из метаданных базы данных, драйвер ODBC сначала пытается найти соответствующий ключ CEK открытого текста зашифрованного значения ключа в кэше. Драйвер вызывает хранилищу ключей, содержащему CMK только в том случае, если не удается найти соответствующий ключ CEK открытого текста в кэше.

Примечание: В драйвере ODBC для SQL Server, записей в кэше вытесняются после истечения времени ожидания два часа. Это означает, что для данного ECEK, драйвер обращается к хранилищу ключей только один раз в течение времени существования приложения или каждые два часа, какое значение меньше.

## <a name="working-with-column-master-key-stores"></a>Работа с хранилищами главных ключей столбцов

Для шифрования или расшифровки данных, драйвер должен получить CEK, настроенной для целевого столбца. Столбца хранятся в зашифрованном виде в метаданных базы данных (ECEKs). Каждый ключ CEK имеет соответствующий CMK, который был использован для его шифрования. [Метаданных базы данных](../../t-sql/statements/create-column-master-key-transact-sql.md) не хранит CMK; содержит только имя хранилища ключей и информацию о хранилище ключей можно использовать для поиска CMK.

Чтобы получить значение открытого текста ECEK, драйвер сначала получает метаданные о CEK и его соответствующие CMK и затем использует эти сведения для связи содержащий CMK хранилища ключей и запрашивает его для расшифровки ECEK. Драйвер взаимодействует с хранилищем ключа с помощью поставщика хранилища ключей.

Для драйвера Microsoft 5.2.0 для PHP для SQL Server поддерживается только поставщик хранилища сертификатов Windows. Два других ключей поставщиков поддерживаются драйвером ODBC (хранилище ключей Azure и настраиваемого поставщика хранилища ключей) еще не поддерживается.

### <a name="using-the-windows-certificate-store-provider"></a>С помощью поставщика хранилища сертификатов Windows

Драйвер ODBC для SQL Server в Windows включает встроенный столбец поставщик хранилища главных ключей для хранилища сертификатов Windows, с именем `MSSQL_CERTIFICATE_STORE`. (Этот поставщик доступен не на macOS или Linux.) С этим поставщиком CMK хранится локально на клиентском компьютере и без дополнительной настройки в приложении не требуется для использования с драйвером. Тем не менее приложение должно иметь доступ к сертификат и его закрытый ключ в хранилище. Дополнительные сведения см. в разделе [Create and Store Column Master Keys (Always Encrypted)](../../relational-databases/security/encryption/create-and-store-column-master-keys-always-encrypted.md)(Создание и хранение главных ключей столбцов (постоянное шифрование)).

## <a name="limitations-of-the-php-drivers-when-using-always-encrypted"></a>Ограничения при использовании постоянного шифрования драйверов PHP

SQLSRV и PDO_SQLSRV:
 -   Поддержка Linux/MacOS
  -   Linux/MacOS не поддерживают поставщика хранилища сертификатов Windows и это только поставщик хранилища ключей, в настоящее время поддерживается с помощью драйверов PHP
 -   Принудительное шифрование параметра
 -   Включение постоянного шифрования на уровне инструкций 
 
SQLSRV:
 -   С помощью `sqlsrv_query` для привязки параметра без указания типа SQL
 -   С помощью `sqlsrv_prepare` для привязки параметров в пакет инструкций SQL  
 
PDO_SQLSRV:
 -   `PDO::SQLSRV_ATTR_DIRECT_QUERY` атрибут инструкции, указанный в параметризованном запросе
 -   `PDO::ATTR_EMULATE_PREPARE` атрибут инструкции, указанный в параметризованном запросе
 -   привязка параметров в пакет инструкций SQL
 
Драйверы PHP также наследуют ограничений, налагаемых драйвером ODBC для SQL Server и базы данных. В разделе [ограничения драйвера ODBC при использовании постоянного шифрования](../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md) и [всегда зашифрованные сведения о возможностях](../../relational-databases/security/encryption/always-encrypted-database-engine.md#feature-details).  
  
## <a name="see-also"></a>См. также  
[Руководство по программированию для драйвера SQL PHP](../../connect/php/programming-guide-for-php-sql-driver.md)
[Справочник по API для драйвера SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  
[Справочник по API для драйвера PDO_SQLSRV](../../connect/php/pdo-sqlsrv-driver-reference.md)  
  
