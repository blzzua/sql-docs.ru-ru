---
title: "Маркеры параметров | Документы Microsoft"
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
- minimum SQL syntax supported [ODBC]
- ODBC drivers [ODBC], minimum SQL syntax supported
- parameter markers [ODBC]
ms.assetid: 07213d04-cd31-45fd-a8c8-2e16e09eeaf4
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f94e8315d5cd38d49b681dfb7c8141bdbf028052
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="parameter-markers"></a>Маркеры параметров
В соответствии со спецификацией SQL-92 приложению не удается разместить маркеры параметров в следующих местах. Более полный список см. в спецификации SQL-92.  
  
-   В **ВЫБЕРИТЕ** списка  
  
-   Как *выражений* в *предикат сравнения*  
  
-   Как оба операнда бинарного оператора  
  
-   В качестве первого и второго операнда из **BETWEEN** операции  
  
-   Как первый и третий операнды **BETWEEN** операции  
  
-   Как выражение и первое значение **в** операции  
  
-   В качестве операнда унарный + или – операции  
  
-   В качестве аргумента *ссылка на функцию для набора*  
  
 Дополнительные сведения о маркерах см. в спецификации SQL-92. Дополнительные сведения о параметрах см. в разделе [параметров инструкции](../../../odbc/reference/develop-app/statement-parameters.md).
