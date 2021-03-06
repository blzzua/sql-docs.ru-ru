---
title: "Типы драйверов | Документы Microsoft"
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
- driver compatibility issues [ODBC]
- ODBC drivers [ODBC], backward compatibility
- backward compatibility [ODBC], application and driver compatibility
- compatibility [ODBC], application and driver compatibility
ms.assetid: 864c53c1-b68a-48b6-b6bc-5ecb520bb9dc
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c2068bb92d1aaa00debc46277c117d4134091666
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="types-of-drivers"></a>Типы драйверов
Драйверы ODBC можно классифицировать следующим образом:  
  
-   **32-разрядное ODBC 2.**  
     ***x* драйвер** 32-разрядный драйвер:  
  
    -   Экспортирует только ODBC 2*.x* функции.  
  
    -   Демонстрирует ODBC 2. *x* поведение для изменения поведения.  
  
-   **ISO и откройте соответствующие группы драйверов** 32-разрядный драйвер:  
  
    -   Экспортирует все функции, которые описаны в документах Open Group или ISO CLI. Сюда входят некоторые функции, которые являются устаревшими в ODBC.  
  
    -   Поведение ODBC 3.0 для изменения поведения.  
  
    -   Не обязательно проходят через диспетчер драйверов ODBC 3.0.  
  
-   **Драйвер ODBC 3.0** 32-разрядный драйвер:  
  
    -   Экспортирует только функции, которые находятся в ODBC 3.0 минус устаревания функций.  
  
    -   Способен обнаружены ODBC 2. *x* поведение или поведение ODBC 3.0 по отношению к изменениям, в зависимости от атрибута SQL_ATTR_APP_ODBC_VERSION среды.  
  
-   **Драйвер ODBC 3.5 (или более поздней версии) ANSI** 32-разрядный драйвер:  
  
    -   Экспортирует только функции, которые находятся в ODBC 3.5 минус устаревания функций.  
  
    -   Способен обнаружены ODBC 2. *x* поведение или поведение ODBC 3.0 или ODBC 3.5 поведение по отношению к изменения поведения на основе SQL_ATTR_APP_ODBC_VERSION среды атрибута.  
  
-   **Драйвер ODBC 3.5 (или более поздней версии) Юникода** 32-разрядный драйвер:  
  
    -   Поддерживает все возможности драйвера ODBC 3.5 ANSI.  
  
    -   Экспортирует все строки ODBC API-интерфейсы версии Юникода.  
  
    -   Можно хранить и обрабатывать данные в Юникоде в источнике данных.  
  
> [!NOTE]  
>  16-разрядные драйверы ODBC, не будут работать непосредственно с ODBC 3. *x* диспетчера драйверов. Тем не менее возможно, что 16-разрядные драйверы для работы с 2.0 диспетчера драйвера ODBC, который впоследствии преобразователи до 3. *x* диспетчера драйверов.
