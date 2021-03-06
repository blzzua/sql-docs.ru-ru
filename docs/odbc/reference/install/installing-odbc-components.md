---
title: "Установка компонентов ODBC | Документы Microsoft"
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
- installing ODBC components [ODBC]
- installing ODBC components [ODBC], about installing
- ODBC [ODBC], component installation
ms.assetid: b7e48e9c-8912-4003-b4ef-30aa44de06a7
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 790d398aff2723557f0e944fad87cd03fbc9819c
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="installing-odbc-components"></a>Установка компонентов ODBC
> [!NOTE]  
>  Начиная с Windows XP и Windows Server 2003, ODBC включается в операционной системе Windows. ODBC следует устанавливать только явно на более ранних версиях Windows.  
  
 В этом разделе описывается способ установки и удаления компонентов ODBC. Так как разработчики всегда устанавливать компонент ODBC (их драйвер), они должны прочитать этот раздел. Разработчики приложений должны прочитать этот раздел только в том случае, если они будут отправлены компонентов ODBC вместе со своими приложениями. Компоненты ODBC включают диспетчера драйверов, драйверы, трансляторы, установщик DLL, библиотеку курсоров и все связанные файлы. В целях этого раздела приложения ODBC не считаются компонентов ODBC.  
  
> [!NOTE]  
>  Этот раздел относится только к платформы Microsoft Windows. Установка компонентов ODBC на других платформах зависит от платформы.  
  
 Компоненты ODBC устанавливаются или удаляются по принципу компонент не основы файла. Например если преобразователь состоит из транслятор себя и количество файлов данных, эти файлы являются устанавливаются или удаляются как группой. они должны не быть установлен и на основе файла. Причиной этого является убедитесь в том, что в системе существует только полный набор компонентов.  
  
 Для целей установки и удаления компонентов ниже определяются как компоненты ODBC:  
  
-   **Компоненты ядра.** Диспетчер драйверов, библиотеку курсоров, установщик DLL и любые другие связанные файлы составляют основные компоненты и необходимо установить и удалить, так как группу.  
  
-   **Драйверы.** Каждый драйвер соответствует отдельный компонент.  
  
-   **Трансляторы.** Каждого из них представляет собой отдельный компонент.  
  
 С поддержкой Юникода в ODBC 3.5 и более поздних версий должное внимание следует уделить с компонентами OLE DB и ODBC. Поставщика OLE DB для ODBC версии 1.1 была записана определенные спецификации Юникода в ODBC 3.0. Из-за эти спецификации в ODBC 3.5, его необходимо иметь версию 1.5 или более поздней версии поставщика, при использовании ODBC 3.5 и более поздней версии. Этот раздел содержит следующие подразделы.  
  
-   [Компоненты установки](../../../odbc/reference/install/installation-components.md)  
  
-   [Подсчет использования](../../../odbc/reference/install/usage-counting.md)
