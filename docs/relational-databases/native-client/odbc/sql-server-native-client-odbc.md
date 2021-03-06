---
title: "Собственный клиент SQL Server (ODBC) | Документы Microsoft"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client|ODBC
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- SQLNCLI, ODBC
- SQL Server Native Client ODBC driver, about SQL Server Native Client ODBC driver
- data access [SQL Server Native Client], ODBC
- SQL Server Native Client ODBC driver
- ODBC
- SQL Server Native Client, ODBC
- ODBC, about SQL Server Native Client ODBC driver
ms.assetid: 811d5ba3-a2b8-48c0-adbc-8c91f041f458
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 0b17b4b7255a63b3c3d1b5f17f89df8d3cfcf009
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="sql-server-native-client-odbc"></a>Собственный клиент SQL Server (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  ODBC — это стандартное определение прикладного программного интерфейса (API), который используется для доступа к данным в реляционных базах данных и базах данных с индексно-последовательным методом доступа (ISAM). [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поддерживает ODBC через драйвер ODBC клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client как один из собственных API для написания приложений на языках C и C++, взаимодействующих с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Программы [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], написанные с помощью драйвера ODBC собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], взаимодействуют с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с помощью вызовов функций на языке C. Специфичные для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] версии функций ODBC реализованы в драйвере ODBC собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Драйвер передает инструкции SQL в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и возвращает приложению результаты их выполнения.  
  
 Драйвер ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] соответствует требованиям спецификации Microsoft Win32 ODBC 3.51. Драйвер поддерживает приложения, написанные с применением более ранних версий ODBC согласно спецификации ODBC 3.51.  
  
## <a name="in-this-section"></a>В этом разделе  
  
-   [Имена источников данных и 64-разрядные операционные системы](../../../relational-databases/native-client/odbc/data-source-names-and-64-bit-operating-systems.md)  
  
-   [Создание драйвера приложение ODBC собственного клиента SQL Server](../../../relational-databases/native-client/odbc/creating-a-driver-application.md)  
  
-   [Взаимодействие с SQL Server &#40; ODBC &#41;](../../../relational-databases/native-client-odbc-communication/communicating-with-sql-server-odbc.md)  
  
-   [Выполнение запросов &#40; ODBC &#41;](../../../relational-databases/native-client-odbc-queries/executing-queries-odbc.md)  
  
-   [Результаты обработки &#40; ODBC &#41;](../../../relational-databases/native-client-odbc-results/processing-results-odbc.md)  
  
-   [С помощью курсоров &#40; ODBC &#41;](../../../relational-databases/native-client-odbc-cursors/using-cursors-odbc.md)  
  
-   [Выполнение транзакций &#40; ODBC &#41;](http://msdn.microsoft.com/library/f431191a-5762-4f0b-85bb-ac99aff29724)  
  
-   [Обработка ошибок и сообщений](../../../relational-databases/native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
-   [Выполнение хранимых процедур](../../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)  
  
-   [Использование функций каталога](../../../relational-databases/native-client/odbc/using-catalog-functions.md)  
  
-   [Выполнение операций массового копирования &#40; ODBC &#41;](../../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)  
  
-   [Управление столбцами text и image](../../../relational-databases/native-client-odbc-text-image-columns/managing-text-and-image-columns.md)  
  
-   [Создание профилей производительности драйвера ODBC](../../../relational-databases/native-client/odbc/profiling-odbc-driver-performance.md)  
  
-   [Возвращающие табличные значения параметры &#40; ODBC &#41;](../../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
-   [Дата и время усовершенствования &#40; ODBC &#41;](../../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)  
  
-   [Определяемые пользователем типы больших значений CLR &#40; ODBC &#41;](../../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md)  
  
-   [Поддержка FILESTREAM &#40; ODBC &#41;](../../../relational-databases/native-client/odbc/filestream-support-odbc.md)  
  
-   [Имена участника-службы &#40; Имена участников-служб &#41; в клиентских подключений &#40; ODBC &#41;](../../../relational-databases/native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md)  
  
-   [Поддержка разреженных столбцов &#40; ODBC &#41;](../../../relational-databases/native-client/odbc/sparse-columns-support-odbc.md)  
  
-   [Собственный клиент SQL Server &#40; ODBC &#41; Ссылка](http://msdn.microsoft.com/library/06b7edee-8636-49d9-9b5c-2c710bf4fa2d)  
  
-   [Инструкции по ODBC](../../../relational-databases/native-client-odbc-how-to/odbc-how-to-topics.md)  
  
## <a name="see-also"></a>См. также  
 [Программирование собственного клиента SQL Server](../../../relational-databases/native-client/sql-server-native-client-programming.md)   
 [Установка собственного клиента SQL Server](../../../relational-databases/native-client/applications/installing-sql-server-native-client.md)  
  
  
