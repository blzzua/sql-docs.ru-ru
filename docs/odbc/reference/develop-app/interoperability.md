---
title: "Взаимодействие | Документы Microsoft"
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
- interoperability [ODBC]
- interoperability [ODBC], about interoperability
ms.assetid: 43b7c849-9d59-4002-9977-9e2c8730b859
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b797bcf1e8e5521ea2b4fd57a68969b3f04e802d
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="interoperability"></a>Совместимость
*Взаимодействие* — это способность одного приложения для работы с многих различных DBMS. Потребность в написании универсальный, с возможностью взаимодействия приложений был одним из основных факторов, ведущих к разработке ODBC. Однако взаимодействия не простой путь из «не поддерживает возможность взаимодействия» для «полностью с возможностью взаимодействия.» Путь есть много ветвей, и каждый требует плюсы и минусы функции, скорости, сложности кода и времени разработки.  
  
 Процесс записи с возможностью взаимодействия приложения состоит из нескольких этапов:  
  
1.  Решить, будет ли приложение использовать ODBC.  
  
2.  Выбор уровня взаимодействия и решить, какие преимущества и недостатки необходимы для достижения этого уровня.  
  
3.  Написание кода с возможностью взаимодействия и как полностью его тестирование.  
  
 Следует отметить, что взаимодействие — в первую очередь это домен, разработчик приложения. Драйверы предназначены для работы с одной СУБД и по определению не являются функционально совместимыми. Они играют роль во взаимодействии с правильной реализации и предоставления ODBC через один СУБД.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Есть ли смысл использовать ODBC?](../../../odbc/reference/develop-app/is-odbc-the-answer.md)  
  
-   [Выбор уровня взаимодействия](../../../odbc/reference/develop-app/choosing-a-level-of-interoperability.md)  
  
-   [Определение целевых СУБД и драйверов](../../../odbc/reference/develop-app/determining-the-target-dbmss-and-drivers.md)  
  
-   [Оценка возможности использования функций базы данных](../../../odbc/reference/develop-app/considering-database-features-to-use.md)  
  
-   [Продолжительность цикла продукта](../../../odbc/reference/develop-app/length-of-the-product-cycle.md)  
  
-   [Создание приложений с поддержкой взаимодействия](../../../odbc/reference/develop-app/writing-an-interoperable-application.md)  
  
-   [Тестирование приложений с поддержкой взаимодействия](../../../odbc/reference/develop-app/testing-interoperable-applications.md)
