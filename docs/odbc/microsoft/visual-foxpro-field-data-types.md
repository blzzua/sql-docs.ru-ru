---
title: "Типы данных полей Visual FoxPro | Документы Microsoft"
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
- field data types [ODBC]
- Visual FoxPro ODBC driver [ODBC], data types
ms.assetid: 50b733dc-679a-4b10-bc5d-98bb474dead2
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8c99a094c690882c6f2877964ae19b335cff1509
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="visual-foxpro-field-data-types"></a>Типы данных полей Visual FoxPro
В следующей таблице перечислены значения для *FieldType* аргумент в инструкции ALTER TABLE и CREATE TABLE и указывает, является ли *nFieldWidth* и *nPrecision* аргументы Обязательно.  
  
|*FieldType*|*NFieldWidth*|*nPrecision*|Description|  
|-----------------|-------------------|------------------|-----------------|  
|B|-|d|Double|  
|C|Нет|-|Символ поле шириной*n*|  
|D|-|-|Дата|  
|Ж|Нет|d|С плавающей запятой числовое поле шириной  *n*  с *d* десятичных разрядов|  
|Ж|-|-|Общие|  
|I|-|-|Целочисленный|  
|L|-|-|Логические|  
|M|-|-|MEMO|  
|Нет|Нет|d|Числовое поле шириной  *n*  с *d* десятичных разрядов|  
|T|-|-|DateTime|  
|Да|-|-|CURRENCY|
