---
title: Команда УНИКАЛЬНЫЙ НАБОР | Документы Microsoft
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
- SET UNIQUE command [ODBC]
ms.assetid: 1f69e31e-4599-47cc-ac89-b86fba8703c5
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0ba0921d2bfab8911d129ac4d1430e6d8d9bd6fe
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="set-unique-command"></a>УНИКАЛЬНЫЙ команды SET
Указывает, хранятся ли записи с повторяющимися значениями ключей в файле индекса.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SET UNIQUE ON | OFF  
```  
  
## <a name="arguments"></a>Аргументы  
 ON  
 Указывает, не включены все записи со значением ключа индекса повторяющиеся в файле индекса. В файле индекса включается первой записи с исходное значение ключа индекса.  
  
 OFF  
 (По умолчанию). Указывает, что записи с повторяющимися значениями ключей будут включены в файл индекса.  
  
## <a name="remarks"></a>Remarks  
 Индексный файл сохраняет его ЗАДАТЬ УНИКАЛЬНЫЙ параметр выполните повторную ИНДЕКСАЦИЮ. Дополнительные сведения см. в разделе [ИНДЕКСА](../../odbc/microsoft/index-command.md).
