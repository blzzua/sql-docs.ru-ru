---
title: "Записи реестра для компонентов ODBC | Документы Microsoft"
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
- subkeys [ODBC]
- installing ODBC components [ODBC], registry entries
- registry entries for components [ODBC]
- subkeys [ODBC], for components
- registry entries for components [ODBC], about registry entries
ms.assetid: c90aa8a4-6ece-48de-901c-17d23739a9ff
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 2eba696dec938321f270acf7cfd3c38141ec3f2f
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="registry-entries-for-odbc-components"></a>Записи реестра для компонентов ODBC
> [!NOTE]  
>  Начиная с Windows XP и Windows Server 2003, ODBC включается в операционной системе Windows. ODBC следует устанавливать только явно на более ранних версиях Windows.  
  
 Установщик DLL сохраняет сведения каждого установленного компонента ODBC в реестре. На компьютерах под управлением Microsoft Windows NT и Microsoft Windows 95/98 эти сведения хранятся в подразделах в следующем разделе реестра:  
  
 HKEY_LOCAL_MACHINE  
  
 ПРОГРАММНОЕ ОБЕСПЕЧЕНИЕ  
  
 интерфейс ODBC  
  
 Файл Odbcinst.ini  
  
 Поскольку Odbcinst.ini раздел HKEY_LOCAL_MACHINE дерева, сведения о компонентах ODBC доступен для всех пользователей компьютера.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Подраздел Core ODBC](../../../odbc/reference/install/odbc-core-subkey.md)  
  
-   [Подраздел драйвера ODBC](../../../odbc/reference/install/odbc-drivers-subkey.md)  
  
-   [Подразделы спецификаций драйверов](../../../odbc/reference/install/driver-specification-subkeys.md)  
  
-   [Подраздел драйвера по умолчанию](../../../odbc/reference/install/default-driver-subkey.md)  
  
-   [Подраздел ODBC-преобразователей](../../../odbc/reference/install/odbc-translators-subkey.md)  
  
-   [Подразделы спецификаций преобразователей](../../../odbc/reference/install/translator-specification-subkeys.md)
