---
title: "Шаг 4б: количество строк выборки | Документы Microsoft"
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
- fetches [ODBC], fetching row count
- row count [ODBC]
- application process [ODBC], fetching row count
ms.assetid: 3af481b1-d694-446e-948d-e3a5edcad050
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b0eda22056173ea6ca90dd4ecc31146de54fbfae
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="step-4b-fetch-the-row-count"></a>Шаг 4б: количество строк выборки
Следующий шаг — выборка количества строк, как показано на следующем рисунке.  
  
 ![Выборка количества строк](../../../odbc/reference/develop-app/media/pr15.gif "pr15")  
  
 Если инструкция выполняется на шаге 3 была **обновление**, **удаление**, или **вставить** инструкция, приложение получает количество затронутых строк с  **SQLRowCount**. Дополнительные сведения см. в разделе [определение число затронутых строк](../../../odbc/reference/develop-app/determining-the-number-of-affected-rows.md).  
  
 Теперь приложение возвращается к шагу 3, для выполнения другой инструкции в той же транзакции или переходит к шагу 5 для фиксации или отката транзакции.
