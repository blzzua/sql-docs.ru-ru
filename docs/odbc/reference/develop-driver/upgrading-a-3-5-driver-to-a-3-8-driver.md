---
title: "Обновление 3.5 драйвер 3.8 драйверу | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ffba36ac-d22e-40b9-911a-973fa9e10bd3
caps.latest.revision: 27
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 98b9c8e3e2179801a4cb7cd2947939d6f2927a02
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="upgrading-a-35-driver-to-a-38-driver"></a>Обновление драйвера 3.5 3.8 драйверу
Данный раздел содержит рекомендации и замечания по обновлению с драйвером ODBC 3.5 с драйвером ODBC 3.8.  
  
##### <a name="version-numbers"></a>Номера версий  
 Следующие правила относятся к версии:  
  
-   Драйвер SQL_OV_ODBC3_80 поддержка SQL_ATTR_ODBC_VERSION, возвращая значение SQL_ERROR для значения, отличные от SQL_OV_ODBC2, SQL_OV_ODBC3 и SQL_OV_ODBC3_80. Будущие версии диспетчера драйверов будет предполагать, что драйвер поддерживает уровень соответствия ODBC, если драйвер возвращает SQL_SUCCESS из [SQLSetEnvAttr, функция](../../../odbc/reference/syntax/sqlsetenvattr-function.md).  
  
-   Драйвер версии 3.8 должен возвращать 03.80 из **SQLGetInfo** при передаче SQL_DRIVER_ODBC_VER *свойство*. Однако старые диспетчеров драйверов, которой были включены в предыдущих версиях Microsoft Windows, будет считать драйвер драйвер версии 3.5 и выдает предупреждение.  
  
     В Windows 7 версия диспетчера драйверов, 03.80. В Windows 8, версия диспетчера драйверов, 03.81 через SQLGetInfo SQL_DM_VER (*свойство* параметр). SQL_ODBC_VER отчеты версии в виде 03.80 в Windows 7 и Windows 8.  
  
##### <a name="driver-specific-c-data-types"></a>Типы данных C драйвера  
 Драйвер может настроили типы данных C когда оно работает с приложением ODBC версии 3.8. (Дополнительные сведения см. в разделе [типы данных C в ODBC](../../../odbc/reference/develop-app/c-data-types-in-odbc.md).) Тем не менее не требуется для реализации любых типов C драйвера 3.8 драйвера. Но драйвер должен по-прежнему выполнять проверки диапазона типов C; Диспетчер драйверов не будет, 3.8 драйверов. Чтобы упростить разработку драйверов, можно определить значение типа данных в конкретное C драйвер в следующем формате:  
  
```  
SQL_DRIVER_C_TYPE_BASE+0, SQL_DRIVER_C_TYPE_BASE+1  
```  
  
##### <a name="driver-specific-data-types-descriptor-types-information-types-diagnostic-types-and-attributes"></a>Типов данных драйвера, дескрипторов типов, типов данных, типы диагностики и атрибуты  
 При разработке нового драйвера, следует использовать диапазон драйвера для типов данных, дескрипторов типов, типов данных, типы диагностики и атрибуты. Специфические для драйвера диапазоны и их значения базового типа рассматриваются в [типов данных драйвера, дескрипторов типов, типов данных, типы диагностики и атрибуты](../../../odbc/reference/develop-app/driver-specific-data-types-descriptor-information-diagnostic.md).  
  
##### <a name="connection-pooling"></a>Организация пулов соединений  
 Для более эффективного управления пулов соединений ODBC 3.8 вводит атрибут соединения SQL_ATTR_RESET_CONNECTION в **SQLSetConnectAttr**. SQL_RESET_CONNECTION_YES является единственным допустимым значением для этого атрибута. SQL_ATTR_RESET_CONNECTION задается непосредственно перед диспетчера драйверов помещает соединения в пул подключений, что позволяет драйверу для сброса других атрибутах соединения значениями по умолчанию.  
  
 Чтобы избежать ненужных связь с сервером, драйвер могут быть отложены атрибута соединения сбросить до следующего связи с удаленным сервером после соединение повторно из пула.  
  
 Обратите внимание, что SQL_ATTR_RESET_CONNECTION используется только в связи между диспетчером драйверов и драйверов. Приложение не может установить этот атрибут непосредственно. Все драйверы версии 3.8 должны реализовывать этот атрибут подключения.  
  
##### <a name="streamed-output-parameters"></a>Потоковых выходных параметров  
 ODBC версии 3.8 вводит потоковых выходных параметров, более масштабируемым способом для получения выходных параметров. (Дополнительные сведения см. в разделе [получение выходных параметров с помощью метода SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md).) Для поддержки этой возможности, драйвер должен задать SQL_GD_OUTPUT_PARAMS в возвращаемом значении при SQL_GETDATA_EXTENSIONS *свойство* в **SQLGetInfo** вызова. Поддержка тип SQL с помощью потоковых выходных параметров должен быть реализован в драйвере. Диспетчер драйверов не будет формировать ошибку для недопустимого типа SQL. В драйвере определяется SQL типы, поддерживающие потоковых выходных параметров.  
  
 Драйвер должен возвращать значение SQL_ERROR, если приложение использует **SQLGetData** для получения параметр, который не совпадает с параметром, возвращенным **SQLParamData**.  
  
##### <a name="asynchronous-execution-for-connection-operations-polling-method"></a>Асинхронное выполнение операций соединения (метода опроса.)  
 Драйвер можно включить поддержку асинхронных операций для различных операций соединения.  
  
 Начиная с Windows 7, ODBC поддерживает метод опроса (Дополнительные сведения см. в разделе [асинхронное выполнение (метод опроса)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md). Нет необходимости для драйвера ODBC версии 3.8 для реализации асинхронных операций на дескрипторов соединений. Даже если драйвер не реализует операции асинхронного дескрипторов соединения, драйвер должен реализовывать SQL_ASYNC_DBC_FUNCTIONS *свойство* и возвращают **SQL_ASYNC_DBC_NOT_CAPABLE**.  
  
 Если включены операции асинхронного соединения, время выполнения операции соединения является общее время все повторные вызовы. Если последний повторить вызов происходит после общее время превышает значение, заданное в атрибуте соединения sql_attr_connection_timeout не учитывается, и операция не завершена, драйвер возвращает значение SQL_ERROR и заносит в журнал запись диагностики с кодом SQLState HYT01 и сообщение «истекло время ожидания подключения». Нет отсутствие времени ожидания, если операция завершена.  
  
##### <a name="sqlcancelhandle-function"></a>Функция SQLCancelHandle  
 Поддерживает ODBC 3.8 [SQLCancelHandle функция](../../../odbc/reference/syntax/sqlcancelhandle-function.md), который используется для отмены операции инструкции и соединения. Драйвер, который поддерживает **SQLCancelHandle** необходимо экспортировать функцию. Драйвер не прерывать любая функция синхронное или асинхронное подключение, выполняется, если приложение вызывает **SQLCancel** или **SQLCancelHandle** дескриптором инструкции. Аналогичным образом, драйвер не прерывать любая функция синхронным или асинхронным инструкции, выполняется, если приложение вызывает **SQLCancelHandle** на дескриптор соединения. Кроме того, драйвер не следует отменить операцию просмотра (**SQLBrowseConnect** возвращает SQL_NEED_DATA) Если приложение вызывает **SQLCancelHandle** на дескриптор соединения. Таким образом драйвер должен возвращать HY010 «ошибочная последовательность функций».  
  
 Нет необходимости поддерживать протоколы **SQLCancelHandle** и асинхронное подключение операций одновременно. Драйвер может поддерживать операции асинхронное подключение, но не **SQLCancelHandle**, или наоборот.  
  
##### <a name="suspended-connections"></a>Приостановленные подключений  
 Диспетчер драйверов ODBC 3.8 можно поместить соединение в приостановленном состоянии. Приложение будет вызывать **SQLDisconnect** для освобождения ресурсов, связанных с этим подключением. В этом случае драйвер следует попытаться освободить столько же ресурсов можно без проверки состояния подключения. Дополнительные сведения о приостановлена. в разделе [функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).  
  
##### <a name="driver-aware-connection-pooling"></a>Организация пулов соединений с учетом драйвера  
 ODBC в Windows 8 позволяет драйверов для настройки поведения пула соединений. Дополнительные сведения см. в разделе [Driver-Aware Connection Pooling](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md).  
  
##### <a name="asynchronous-execution-notification-method"></a>Асинхронное выполнение (метод уведомления)  
 ODBC 3.8 поддерживает метод уведомления для асинхронных операций, которые доступны, начиная с Windows 8. Дополнительные сведения см. в разделе [асинхронное выполнение (метод уведомления)](../../../odbc/reference/develop-app/asynchronous-execution-notification-method.md).  
  
## <a name="see-also"></a>См. также:  
 [Разработка драйвера ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Драйверы ODBC, предоставляемые корпорацией Майкрософт](../../../odbc/microsoft/microsoft-supplied-odbc-drivers.md)   
 [Новые возможности ODBC 3.8](../../../odbc/reference/what-s-new-in-odbc-3-8.md)