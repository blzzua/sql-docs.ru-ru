---
title: "Jet: Даты, времени и отметок времени литералы | Документы Microsoft"
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
- literals [ODBC], SQL grammar
- SQL grammar [ODBC], literals
- date literals [ODBC]
- timestamp literals [ODBC]
- time literals [ODBC]
ms.assetid: 37db1ae1-ca4e-4cd8-9b47-7f1a38e7fcad
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 819b40dd4cc3e8481ed5e0795debca13c0779fd6
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="jet-date-time-and-timestamp-literals"></a>Jet: Даты, времени и отметок времени литералы
Для максимальной совместимости приложений следует передавать литералы даты в каноническом формате ODBC, с помощью предложения escape-синтаксис:  
  
-   Для date литералов {d '*значение*"}, где *значений*e указывается в формате «гггг мм дд»  
  
-   Литералы времени {t '*значение*"}, где *значений*e находится в форме «чч»  
  
 Для отметки времени литералов {ts*значение*"}, где *значений*e — в виде «гггг мм дд чч [. f...]».
