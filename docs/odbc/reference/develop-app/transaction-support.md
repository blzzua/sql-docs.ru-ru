---
title: Поддержка транзакций | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- transactions [ODBC], degree of support
ms.assetid: d56e1458-8da2-4d73-a777-09e045c30a33
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4964565ce7de30b30fa3dc4c7705c5656ebcb88b
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="transaction-support"></a>Поддержка транзакций
Степень поддержки транзакций, определяемым драйвером. ODBC предназначен для реализации для одного пользователя или рабочего стола, базы данных, не требуется управлять несколько обновлений к его данным. Кроме того некоторые базы данных, поддерживающие транзакции будет поддерживаться только инструкции языка обработки данных (DML) SQL; Существуют ограничения или семантика специальные транзакций по использованию языка определения данных (DDL), когда транзакция активна. То есть может быть поддержку транзакций для нескольких одновременных обновления таблиц, но не для изменения числа и определения таблиц во время транзакции.  
  
 Приложение определяет, поддерживаются ли операции DDL могут быть включены в транзакции и любые специальные эффекты, в том числе DDL в рамках транзакции, вызвав **SQLGetInfo** с параметром SQL_TXN_CAPABLE. Дополнительные сведения см. в разделе [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) описание функции.  
  
 Если драйвер не поддерживает транзакции, но приложение имеет возможность (с помощью API-Интерфейс, отличный от ODBC) для блокирования и разблокирования данных, приложения могут обеспечить поддержку транзакций блокировка и снятие блокировки записей и таблицами, при необходимости. Реализация примера передачи учетной записи, приложение будет блокировать записи для обеих учетных записей, копирует текущие значения, Дебет первой учетной записи, кредита второй учетной записи и разблокировать записей. Если не удалось выполнить все этапы, приложение будет сбросить учетные записи, с помощью копии.  
  
 Источники даже данные, которые поддерживают транзакции может оказаться неспособными поддерживать несколько транзакций одновременно в конкретной среде. Приложения вызывают **SQLGetInfo** с параметром SQL_MULTIPLE_ACTIVE_TXN, чтобы определить, поддерживает ли источник данных одновременных активных транзакций в той же среде более одного соединения. Так как одна транзакция на соединение, только представляет интерес для приложений, имеющих несколько подключений к одному источнику данных.
