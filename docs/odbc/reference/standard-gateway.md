---
title: "Стандартный шлюз | Документы Microsoft"
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
- ODBC [ODBC], database access
- SQL [ODBC], database access
- database access [ODBC]
- standardizing database access [ODBC], gateways
- standard gateways [ODBC]
- gateways [ODBC]
ms.assetid: b8341492-2141-4bab-80bd-f2752223079e
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e70ef86e0fce41e73cee16074cdfcd6a97177ba7
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="standard-gateway"></a>Стандартный шлюз
Объект *шлюза* — это программное обеспечение, которое вызывает один СУБД должен выглядеть как другой. Т. е шлюз принимает интерфейс программирования, грамматику SQL и данных протокола один СУБД и переводит его в программный интерфейс грамматику SQL, и протокол скрытые СУБД потока данных. Например приложения, написанные для использования Microsoft® SQL Server™ можно также доступ к данным DB2 через шлюз DB2 Micro Decisionware; Этот продукт в результате DB2, как SQL Server. При использовании шлюзов, другой шлюз должен быть написан для каждой целевой базы данных.  
  
 Несмотря на то, что шлюзы ограничиваются архитектурных различий между СУБД, они являются хорошим кандидатом для стандартизации. Тем не менее если все СУБД стандартизировать интерфейс программирования, грамматику SQL и данные потока протокола один СУБД, которого СУБД — выбирается в качестве стандартной? Наверняка не коммерческих поставщиков СУБД наверняка согласятся стандартизировать продукт конкурента. Если разрабатываются стандартный интерфейс программирования, грамматику SQL и протокол потока данных, шлюз не требуется.
