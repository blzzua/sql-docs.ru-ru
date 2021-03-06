---
title: Выполнение инструкции | Документы Microsoft
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
helpviewer_keywords:
- SQL statements [ODBC], executing
ms.assetid: e5f0d2ee-0453-4faf-b007-12978dd300a1
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ddb265060dc0714ce4eafaa09ce336d289697309
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="executing-a-statement"></a>Выполнение инструкции
Для выполнения инструкции, в зависимости от при компиляции (подготовленный), компонент database engine и кто их определяет четырьмя способами:  
  
-   **Прямое выполнение** приложение определяет инструкцию SQL. Готова и во время выполнения за один шаг.  
  
-   **На выполнение подготовленной** приложение определяет инструкцию SQL. Готова и во время выполнения в отдельности. Инструкция может быть подготовлена один раз и выполняться несколько раз.  
  
-   **Процедуры** приложения можно определить и скомпилировать один или несколько инструкций SQL на этапе разработки времени и сохранить эти инструкции в источнике данных, что и процедура. Процедура выполняется один или несколько раз во время выполнения. Приложение может перечислять существующие хранимые процедуры, с помощью функции работы с каталогами.  
  
-   **Функции каталога** записи драйвер создает функцию, возвращающую предопределенных результирующий набор. Как правило эта функция выполняет стандартные инструкции SQL или вызывает процедуру, созданную для этой цели. Функция выполняется один или несколько раз во время выполнения.  
  
 Определенной инструкции (как определено в его дескриптора инструкции) может быть выполняться любое количество раз. Инструкция может быть выполнена с множеством разных инструкций SQL, или он может выполняться несколько раз с той же инструкции SQL. Например, следующий код использует тот же дескриптор инструкции (*hstmt1*) для извлечения и отображения таблиц в базе данных Sales. Затем он использует этот дескриптор для получения столбцов таблицы, выбранные пользователем.  
  
```  
SQLHSTMT    hstmt1;  
SQLCHAR *   Table;  
  
// Create a result set of all tables in the Sales database.  
SQLTables(hstmt1, "Sales", SQL_NTS, "sysadmin", SQL_NTS, NULL, 0, NULL, 0);  
  
// Fetch and display the table names; then close the cursor.  
// Code not shown.  
  
// Have the user select a particular table.  
SelectTable(Table);  
  
// Reuse hstmt1 to create a result set of all columns in Table.  
SQLColumns(hstmt1, "Sales", SQL_NTS, "sysadmin", SQL_NTS, Table, SQL_NTS, NULL, 0);  
  
// Fetch and display the column names in Table; then close the cursor.  
// Code not shown.  
```  
  
 И в следующем коде показано, как используется один дескриптор для многократного выполнения одной инструкции для удаления строк из таблицы.  
  
```  
SQLHSTMT      hstmt1;  
SQLUINTEGER   OrderID;  
SQLINTEGER    OrderIDInd = 0;  
  
// Prepare a statement to delete orders from the Orders table.  
SQLPrepare(hstmt1, "DELETE FROM Orders WHERE OrderID = ?", SQL_NTS);  
  
// Bind OrderID to the parameter for the OrderID column.  
SQLBindParameter(hstmt1, 1, SQL_PARAM_INPUT, SQL_C_ULONG, SQL_INTEGER, 5, 0,  
                  &OrderID, 0, &OrderIDInd);  
  
// Repeatedly execute hstmt1 with different values of OrderID.  
while ((OrderID = GetOrderID()) != 0) {  
   SQLExecute(hstmt1);  
}  
```  
  
 Для большое число драйверов выделение инструкций является ресурсоемких задач, поэтому повторное использование одной и той же инструкции таким способом обычно более эффективен, чем освобождение существующих инструкций и выделение новые. Приложений, создающих результирующие наборы в операторе должна быть указана закрыть курсор над результирующий набор, прежде чем выполнить повторно инструкции. Дополнительные сведения см. в разделе [закрытие курсора](../../../odbc/reference/develop-app/closing-the-cursor.md).  
  
 Повторное использование инструкции также вызывает приложение, чтобы избежать ограничений в некоторые драйверы количество инструкций, которые могут быть активны одновременно. Точное определение «активный», относящиеся к драйверу, но часто называется любая инструкция, подготовки или выполнения и по-прежнему содержит доступных результатов. Например, после **вставить** инструкция была подготовлена, обычно он считается активным; после **ВЫБЕРИТЕ** оператора выполняется и по-прежнему открыт курсор, обычно считается быть активно; После **CREATE TABLE** инструкция была выполнена, обычно не считается активным.  
  
 Приложение определяет, сколько инструкций может быть активна одновременно в одном соединении, вызвав **SQLGetInfo** с параметром SQL_MAX_CONCURRENT_ACTIVITIES. Приложение может использовать несколько активных инструкций, чем это ограничение путем открытия нескольких подключений к источнику данных; Поскольку соединения могут потреблять много ресурсов, однако следует рассматривать влияние на производительность.  
  
 Приложения можно ограничить количество времени, достаточного для инструкцию для выполнения с помощью атрибута SQL_ATTR_QUERY_TIMEOUT инструкции. Если время ожидания истекает до источник данных возвращает результирующий набор, функция, выполнение инструкции SQL возвращает SQLSTATE HYT00 (превышено время ожидания). По умолчанию нет отсутствие времени ожидания.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Прямое выполнение](../../../odbc/reference/develop-app/direct-execution-odbc.md)  
  
-   [Подготовленное выполнение](../../../odbc/reference/develop-app/prepared-execution-odbc.md)  
  
-   [Процедуры](../../../odbc/reference/develop-app/procedures-odbc.md)  
  
-   [Пакеты инструкций SQL](../../../odbc/reference/develop-app/batches-of-sql-statements.md)  
  
-   [Выполнение функций каталога](../../../odbc/reference/develop-app/executing-catalog-functions.md)
