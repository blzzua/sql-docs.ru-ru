---
title: "Длина данных столбца | Документы Microsoft"
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
- column data [ODBC]
- length of column data [ODBC]
- ODBC cursor library [ODBC], cache
- cursor library [ODBC], cache
- cache [ODBC]
ms.assetid: c762c881-ebe0-4eac-84d5-f30281fc3eca
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b8a291ef2698c8616481dee30f5bdce41814b7d3
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="length-of-column-data"></a>Длина данных столбца
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этой возможности в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Корпорация Майкрософт рекомендует использовать функциональность курсора драйвера.  
  
 Библиотека курсоров создает буфер, в кэше для каждого буфера длины и индикатора, привязанное к результирующий набор с **SQLBindCol**. Он использует значения в этих буферах для создания **ГДЕ** предложения, если он эмулирует позиционированного обновления или delete. Обновляет эти буферы из буферов набора строк при выборке данных из источника данных и при выполнении инструкции позиционированного обновления.  
  
 Если тип C буфера данных — SQL_C_CHAR и SQL_C_BINARY, а значение длины/индикатора равно SQL_NTS, длина строки данных помещается в буфер длины/индикатора.  
  
> [!NOTE]  
>  Библиотека курсоров не обновляет свой кэш для столбца, если **StrLen_or_IndPtr* в соответствующих строк буфера является значение SQL_DATA_AT_EXEC, ни результатом SQL_LEN_DATA_AT_EXEC макроса.
