---
title: "Действие параметров ISO | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-queries
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- ISO options (ODBC)
- ODBC applications, ISO options
- ODBC applications, statements
- SQL Server Native Client ODBC driver, ISO options
- statements [ODBC], ISO options
ms.assetid: 813f1397-fa0b-45ec-a718-e13fe2fb88ac
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2267290d43ec746fd3f2d11597eeefa498651e62
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="effects-of-iso-options"></a>Действие параметров ISO
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Стандарт ODBC близок к стандарту ISO, а приложения ODBC ожидают стандартного поведения от драйвера ODBC. Чтобы сделать его более точно соответствовать поведения, определенные в стандарт ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента всегда использует все параметры ISO, доступные в версии SQL Server, к которой он подключается.  
  
 Когда [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента подключается к экземпляру компонента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], сервер обнаруживает, что клиент использует [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] драйвер ODBC для собственного клиента и устанавливает некоторые параметры.  
  
 Драйвер сам формирует эти инструкции; ODBC-приложение не посылает для этого никаких запросов. Установка этих параметров позволяет ODBC-приложениям, использующим драйвер, иметь лучшую переносимость, поскольку в этом случае поведение сервера более соответствует стандарту ISO.  
  
 Приложения на основе DB-Library обычно не вызывают включение этих параметров. Расхождения между ODBC или DB-Library клиенты под управлением одной и той же инструкции SQL не следует предполагать, это указывает на проблемы с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента. Их следует повторно выполнить инструкцию в среде DB-Library с тем же НАБОРОМ параметров, как будет использоваться [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента.  
  
 Поскольку пользователи и приложения могут в любое время включать и выключать параметры из набора SET, разработчики хранимых процедур и триггеров должны проводить тестирование своих процедур и триггеров как со включенными, так и с отключенными параметрами из этого набора. Это гарантирует, что триггеры и процедуры будут правильно работать независимо от того, какие параметры конкретное соединение установит при вызове триггера или процедуры. Если для работы триггера или хранимой процедуры требуется конкретное значение одного из этих параметров, инструкцию SET следует выполнить в начале триггера или хранимой процедуры. Она сохраняет силу только до завершения триггера или хранимой процедуры; после этого восстанавливается первоначальное значение параметра.  
  
 При подключении к экземпляру [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] устанавливается также четвертый параметр SET, CONCAT_NULL_YIELDS_NULL. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Драйвер ODBC собственного клиента не устанавливает эти параметры, если значение AnsiNPW = NO задан в источнике данных или любой [SQLDriverConnect](../../../relational-databases/native-client-odbc-api/sqldriverconnect.md) или [SQLBrowseConnect](../../../relational-databases/native-client-odbc-api/sqlbrowseconnect.md).  
  
 Как уже отмечалось ранее, параметры ISO [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента не включает параметр QUOTED_IDENTIFIER, если задано значение QuotedID = NO задан в источнике данных или любой **SQLDriverConnect** или  **SQLBrowseConnect**.  
  
 Чтобы драйвер мог узнавать текущие значения параметров SET, ODBC-приложения не должны задавать эти параметры с помощью инструкции языка [!INCLUDE[tsql](../../../includes/tsql-md.md)] SET. Они могут задавать их только через параметры источника данных или соединения. Если приложение запускает инструкции SET, то инструкции SQL, создаваемые драйвером, могут быть неверными.  
  
## <a name="see-also"></a>См. также  
 [Выполнение инструкции &#40; ODBC &#41;](../../../relational-databases/native-client-odbc-queries/executing-statements/executing-statements-odbc.md)   
 [SQLDriverConnect](../../../relational-databases/native-client-odbc-api/sqldriverconnect.md)   
 [SQLBrowseConnect](../../../relational-databases/native-client-odbc-api/sqlbrowseconnect.md)  
  
  
