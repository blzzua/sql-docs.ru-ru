---
title: "Сопоставление типов курсоров Attributes1 сведения | Документы Microsoft"
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
- compatibility [ODBC], mapping cursor attributes1 information types
- application upgrades [ODBC], mapping cursor attributes1 information types
- mapping cursor attributes1 information types [ODBC]
- backward compatibility [ODBC], mapping cursor attributes1 information types
- upgrading applications [ODBC], mapping cursor attributes1 information types
ms.assetid: 9f112449-ca86-45ac-a865-e6174d67f91b
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 23d451096509030552f0af18961d1febe5bfb391
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="mapping-the-cursor-attributes1-information-types"></a>Сопоставление типов курсоров Attributes1 сведения
Когда ODBC 3. *x* приложение вызывает **SQLGetInfo** в ODBC 2*.x* драйвер с типом SQL_XXXX_CURSOR_ATTRIBUTES1 сведения (для динамических, однонаправленные, управляемые набором ключей, или статические курсоры) определяется параметр битов, возвращаемых диспетчером драйверов ODBC 2. *x* драйвер возвращает для соответствующего ODBC 2. *x* типы информации. Биты установлены, как показано в следующей таблице.  
  
|Бит в<br /><br /> SQL_XXXX_CURSOR_ATTRIBUTES1|Тип курсора|ODBC 2. *x* сведения<br /><br /> Тип|  
|-----------------------------------------------|-----------------|-------------------------------------|  
|SQL_CA1_NEXT|All|SQL_FETCH_DIRECTION|  
|SQL_CA1_ABSOLUTE SQL_CA1_RELATIVE SQL_CA1_BOOKMARK|Динамические, управляемые набором ключей, статические|SQL_FETCH_DIRECTION|  
|SQL_CA1_LOCK_NO_CHANGE SQL_CA1_LOCK_UNLOCK SQL_CA1_LOCK_EXCLUSIVE|Динамические, управляемые набором ключей, статические|SQL_LOCK_TYPES|  
|SQL_CA1_POSITIONED_UPDATE SQL_CA1_POSITIONED_DELETE SQL_CA1_SELECT_FOR_UPDATE|All|SQL_POSITIONED_STATEMENTS|  
|SQL_CA1_POS_POSITION SQL_CA1_POS_DELETE SQL_CA1_POS_REFRESH SQL_CA1_POS_BULK_ADD|Динамические, управляемые набором ключей, статические|SQL_POS_OPERATIONS|
