---
title: "Выполнение запросов (ODBC) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-queries
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- ODBC applications, executing queries
- SQL Server Native Client ODBC driver, statements
- ODBC applications, statements
- SQL Server Native Client ODBC driver, queries
- queries [ODBC]
ms.assetid: d935bcba-8ce6-4159-8395-6c86431602ad
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c94ad284fbdf13dff9169a07a4ae2b45562f41e8
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="executing-queries-odbc"></a>Выполнение запросов (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  После того, как приложение ODBC инициализирует дескриптор соединения и подключается к источнику данных, оно выделяет один или несколько дескрипторов инструкций на дескриптор соединения. Приложение может затем выполнить [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] инструкций с дескриптором инструкции. Общая последовательность событий при выполнении инструкции SQL.  
  
1.  Установите необходимые атрибуты инструкции.  
  
2.  Сформируйте инструкцию.  
  
3.  Выполните инструкцию.  
  
4.  Получите результирующие наборы.  
  
 После того, как приложение получит все строки во всех результирующих наборах, возвращенных инструкцией SQL, оно может выполнить другой запрос на том же дескрипторе инструкции. Если приложение определяет, что он не требуется для получения всех строк в некотором результирующем наборе, его можно отменить остаток результирующего набора с помощью вызова [SQLMoreResults](../../relational-databases/native-client-odbc-api/sqlmoreresults.md) или [SQLCloseCursor](../../relational-databases/native-client-odbc-api/sqlclosecursor.md).  
  
 Если в приложении ODBC необходимо несколько раз выполнить одну инструкцию SQL с различными данными, используйте маркер параметра, обозначенный вопросительным знаком (?) при построении инструкции SQL:  
  
```  
INSERT INTO MyTable VALUES (?, ?, ?)  
```  
  
 Каждый маркер параметра затем подключаются к программной переменной путем вызова [SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md).  
  
 После того, как будут вызваны все инструкции SQL и обработаны их результирующие наборы, приложение освобождает дескриптор инструкции.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Драйвер ODBC для собственного клиента поддерживает несколько дескрипторов инструкций на один дескриптор соединения. Управление транзакциями осуществляется на уровне соединения, поэтому вся работа, выполняемая со всеми дескрипторами инструкций на одном дескрипторе соединения, управляется как часть одной транзакции.  
  
## <a name="in-this-section"></a>В этом разделе  
  
-   [Выделение дескриптора инструкции](../../relational-databases/native-client-odbc-queries/allocating-a-statement-handle.md)  
  
-   [Построение инструкции SQL &#40; ODBC &#41;](../../relational-databases/native-client-odbc-queries/constructing-an-sql-statement-odbc.md)  
  
-   [Конструирование инструкций SQL для курсоров](../../relational-databases/native-client-odbc-queries/constructing-sql-statements-for-cursors.md)  
  
-   [Использование параметров инструкции](../../relational-databases/native-client-odbc-queries/using-statement-parameters.md)  
  
-   [Выполнение инструкции &#40; ODBC &#41;](../../relational-databases/native-client-odbc-queries/executing-statements/executing-statements-odbc.md)  
  
-   [Освобождение дескриптора инструкции](../../relational-databases/native-client-odbc-queries/freeing-a-statement-handle.md)  
  
## <a name="see-also"></a>См. также  
 [Собственный клиент SQL Server &#40; ODBC &#41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
