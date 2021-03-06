---
title: "DLL-файлов установки драйвера | Документы Microsoft"
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
- installing ODBC components [ODBC], driver setup DLL
- ODBC drivers [ODBC], driver setup DLL
- driver setup DLL [ODBC]
ms.assetid: 49bab021-81fa-402e-b7a4-a5214f1fadc4
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: fd507929bcb54079f62f81829f5e721834efe21e
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="driver-setup-dll"></a>DLL-файлов установки драйвера
> [!NOTE]  
>  Начиная с Windows XP и Windows Server 2003, ODBC включается в операционной системе Windows. ODBC следует устанавливать только явно на более ранних версиях Windows.  
  
 Настройка драйвера, DLL-Библиотека содержит **ConfigDriver** и **ConfigDSN** функции. **ConfigDriver** задач установки драйвера, например ввода специфические для драйвера информации в реестр. **ConfigDSN** поддерживает специфические для драйвера информацию об источниках данных в реестре. Полное описание этих функций см. в разделе [Справочник по API библиотеки DLL установки](../../../odbc/reference/syntax/setup-dll-api-reference.md).  
  
 **ConfigDSN** вызывает следующие функции в DLL-ФАЙЛ источника данных в реестре Ведение установщик:  
  
-   **SQLWriteDSNToIni**. Добавление источника данных.  
  
-   **SQLRemoveDSNFromIni**. Удаление источника данных.  
  
-   **SQLWritePrivateProfileString**. Запись значения драйвера подраздела спецификации источника данных.  
  
-   **SQLGetPrivateProfileString**. Чтение значения драйвера из подраздела спецификации источника данных.  
  
-   **SQLGetTranslator**. Запрашивать у пользователя имя переводчик и параметр. Эта функция вызывает **ConfigTranslator** в трансляторе установки библиотеки DLL.  
  
 Настройка драйвера DLL записывается разработчиком драйвера. Он может быть частью драйвера DLL или отдельную библиотеку DLL.
