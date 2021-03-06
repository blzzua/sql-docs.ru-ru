---
title: "Определение числа затронутых строк | Документы Microsoft"
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
- updating data [ODBC], number of rows affected
- number of rows affected by update [ODBC]
- data updates [ODBC], number of rows affected
ms.assetid: 1e56297d-a786-415e-b66d-b42d1b2a8d45
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ac4b30fc9bbbb2e289ca53094d5050f0808b3ec1
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="determining-the-number-of-affected-rows"></a>Определение числа затронутых строк
После приложение обновляет, удаляет или вставляет строки, он может вызвать **SQLRowCount** можно определить затронутые количества строк. **SQLRowCount** возвращает это значение, независимо от наличия строки были обновлены, удалены или вставлены, выполнив **обновление**, **удаление**, или **вставить** инструкции по выполнении позиционированного обновления или инструкции delete или путем вызова **SQLSetPos**.  
  
 Если выполняется пакет инструкций SQL, количество затронутых строк может быть полный счетчик для всех инструкций в пакете или отдельных счетчиков для каждой инструкции в пакете. Дополнительные сведения см. в разделе [пакеты инструкций SQL](../../../odbc/reference/develop-app/batches-of-sql-statements.md) и [несколько результатов](../../../odbc/reference/develop-app/multiple-results.md).  
  
 Также возвращается число затронутых строк SQL_DIAG_ROW_COUNT диагностические поля в заголовке в области диагностики, связанные с дескриптором инструкции. Тем не менее, данные в этом поле сбрасывается после вызова каждой функции, в том же дескрипторе инструкции, в то время как значение, возвращаемое **SQLRowCount** остается неизменным до вызова **SQLBulkOperations**, **SQLExecute**, **SQLExecDirect**, **SQLPrepare**, или **SQLSetPos**.
