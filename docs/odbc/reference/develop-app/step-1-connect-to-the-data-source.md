---
title: "Шаг 1: Подключение к источнику данных | Документы Microsoft"
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
- application process [ODBC], connecting to data source
- data sources [ODBC], connections
- connecting to data source [ODBC], steps
ms.assetid: 84298664-4523-4149-b821-7b2e42c85281
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e57a58062f352900e5411fcc99a4c5bc9c59393b
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="step-1-connect-to-the-data-source"></a>Шаг 1: Подключение к источнику данных
Для подключения к источнику данных является первым шагом в любом приложении. Этот этап, включая функции, необходимые, показан на следующем рисунке.  
  
 ![Подключение к источнику данных в приложении ODBC](../../../odbc/reference/develop-app/media/pr11.gif "pr11")  
  
 Первым шагом в соединении с источником данных является для загрузки диспетчера драйверов и выделить дескриптор среды с **SQLAllocHandle**. Дополнительные сведения см. в разделе [выделения памяти для обработки среды](../../../odbc/reference/develop-app/allocating-the-environment-handle.md).  
  
 Затем приложение регистрирует используемая версия ODBC, в которой он соответствует путем вызова **SQLSetEnvAttr** с атрибутом SQL_ATTR_APP_ODBC_VER среды. Дополнительные сведения см. в разделе [объявление приложения ODBC версии](../../../odbc/reference/develop-app/declaring-the-application-s-odbc-version.md) и [обратной совместимости и соответствия стандартам](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md).  
  
 После этого приложение выделяет дескриптор соединения с **SQLAllocHandle** и подключается к источнику данных с **SQLConnect**, **SQLDriverConnect**, или **SQLBrowseConnect**. Дополнительные сведения см. в разделе [выделения дескриптор подключения](../../../odbc/reference/develop-app/allocating-a-connection-handle-odbc.md) и [подключения](../../../odbc/reference/develop-app/establishing-a-connection.md).  
  
 Затем приложение задает любых атрибутов соединения, такие как вручную фиксации транзакции. Дополнительные сведения см. в разделе [атрибуты соединения](../../../odbc/reference/develop-app/connection-attributes.md).
