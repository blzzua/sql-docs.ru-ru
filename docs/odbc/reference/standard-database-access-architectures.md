---
title: "Архитектуры доступа к стандартной базы данных | Документы Microsoft"
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
ms.assetid: a9d41800-9068-4b76-895a-32b2853692dd
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 749492ebd893234dea574c0fd87e20b45ddd8628
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="standard-database-access-architectures"></a>Архитектуры доступа к стандартной базы данных
Анализ компонентов доступа базы данных, описанные в предыдущем разделе, оказывается, два из них — программный интерфейс и данные потока протоколы — хорошо подходят для стандартизации. Эти два компонента — IPC механизм и сетевые протоколы, не только находятся на слишком низкого уровня, но оба сильно зависит от сети и операционной системы. Имеется также третий подход — шлюзы —, предоставляющий возможности для стандартизации.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Стандартный интерфейс программирования](../../odbc/reference/standard-programming-interface.md)  
  
-   [Стандартный протокол потока данных](../../odbc/reference/standard-data-stream-protocol.md)  
  
-   [Стандартный шлюз](../../odbc/reference/standard-gateway.md)
