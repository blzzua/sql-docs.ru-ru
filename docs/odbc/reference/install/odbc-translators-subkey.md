---
title: "Подраздел трансляторы ODBC | Документы Microsoft"
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
- translator subkey [ODBC]
- subkeys [ODBC], translator subkey
- registry entries for components [ODBC], translator subkey
ms.assetid: 6b170f1f-e263-4aac-9d49-8d0ca0470ca2
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e94cd3cd2313b98376e32c8775ec38c3c8ddb268
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="odbc-translators-subkey"></a>Подраздел трансляторы ODBC
Значения в подразделе трансляторы ODBC список установленных трансляторы. В следующей таблице показан формат этих значений.  
  
|Имя|Тип данных|data|  
|----------|---------------|----------|  
|*транслятор desc*|REG_SZ|**Установлен**|  
  
 *Переводчик desc* имя определяется разработчиком преобразователя.  
  
 Например предположим, что пользователь установил на переводчик EBCDIC преобразователь Microsoft® кодовых страниц и пользовательских ASCII. Значения в подразделе трансляторы ODBC может выглядеть следующим образом:  
  
```  
MS Code Page Translator: REG_SZ : Installed  
ASCII to EBCDIC: REG_SZ : Installed.  
```
