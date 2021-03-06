---
title: "Массивы значений параметров | Документы Microsoft"
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
- arrays of parameter values [ODBC]
- parameter arrays [ODBC]
ms.assetid: 9b572c5b-1dfe-40af-bebd-051548ab6d90
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c5f81e6b84f53da297f806ff2d63ea0b6e29b708
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="arrays-of-parameter-values"></a>Массивы значений параметров
Часто бывает полезна для приложений, для передачи массивов параметров. Например, при использовании массивов параметров и параметризованную **вставить** инструкции, приложение можно вставить несколько строк за один раз. Существует несколько преимуществ использования массивов. Во-первых сокращает сетевой трафик, поскольку данные для многих инструкций отправляются в одном пакете (если источник данных поддерживает массивы параметров в собственном коде). Во-вторых некоторые источники данных можно выполнять инструкции SQL, использование массивов быстрее, чем выполнение одинаковое число отдельных инструкций SQL. Наконец, когда данные хранятся в виде массива, как это часто бывает в случае данные экрана, приложение можно привязать все строки в определенном столбце с помощью одного вызова **SQLBindParameter** и обновлять их, выполнив одну инструкцию.  
  
 К сожалению не так много источников данных поддерживают массивы параметров. Тем не менее драйвер можно эмулировать массивы параметров, выполнение инструкции SQL один раз для каждого набора значений параметров. Это может привести к увеличению скорости, так как драйвер затем можно подготовить инструкцию, которую он планирует выполнить один раз для каждого набора параметров. Он также может привести к более простой код приложения.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Привязка массивов параметров](../../../odbc/reference/develop-app/binding-arrays-of-parameters.md)  
  
-   [Использование массивов параметров](../../../odbc/reference/develop-app/using-arrays-of-parameters.md)
