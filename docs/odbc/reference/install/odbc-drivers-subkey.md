---
title: "Подраздел драйверы ODBC | Документы Microsoft"
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
- subkeys [ODBC], drivers subkey
- registry entries for components [ODBC], drivers subkey
- drivers subkey [ODBC]
ms.assetid: 8edbf68f-d05d-4d77-92f6-e9500008f520
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 171692642f04cbab5b1e289efdae89ab79f15831
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="odbc-drivers-subkey"></a>Подраздел драйверы ODBC
Значения в подразделе драйверы ODBC списка установленных драйверов. В следующей таблице показан формат этих значений.  
  
|Имя|Тип данных|data|  
|----------|---------------|----------|  
|*Описание драйвера*|REG_SZ|**Установлен**|  
  
 *Описание драйвера* имя определяется разработчиком драйвера. Обычно это имя СУБД, связанные с драйвером.  
  
 Например предположим, что были установлены драйверы для файлов форматированный текст и SQL Server. Значения в подразделе драйверы ODBC могут быть:  
  
```  
Text : REG_SZ : Installed  
SQL Server : REG_SZ : Installed  
```
