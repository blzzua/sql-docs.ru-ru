---
title: "Шаг 6: Отключение от источника данных | Документы Microsoft"
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
- application process [ODBC], disconnecting from data source
- data sources [ODBC], disconnecting
- disconnecting from data source [ODBC]
ms.assetid: 6ad759ba-4721-4d8f-9b26-de976d4fc1a0
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d76d3b3061dded62c7230e4a8d02a4312c8152f9
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="step-6-disconnect-from-the-data-source"></a>Шаг 6: Отключение от источника данных
Последним шагом является отключение от источника данных, как показано на следующем рисунке. Во-первых, приложение освободит все дескрипторы инструкций путем вызова **SQLFreeHandle**. Дополнительные сведения см. в разделе [освободить дескриптор инструкции](../../../odbc/reference/develop-app/freeing-a-statement-handle-odbc.md).  
  
 ![Показывает отключение от источника данных](../../../odbc/reference/develop-app/media/pr17.gif "pr17")  
  
 После этого приложение отключает из источника данных с **SQLDisconnect** и освобождает дескриптор соединения с **SQLFreeHandle**. Дополнительные сведения см. в разделе [отключение от источника данных или драйвер](../../../odbc/reference/develop-app/disconnecting-from-a-data-source-or-driver.md).  
  
 Наконец, приложение освобождает дескриптор среды с **SQLFreeHandle** и выгружает диспетчера драйверов. Дополнительные сведения см. в разделе [выделения памяти для обработки среды](../../../odbc/reference/develop-app/allocating-the-environment-handle.md).
