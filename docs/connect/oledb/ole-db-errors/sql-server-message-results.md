---
title: Результаты сообщения SQL Server | Документы Microsoft
description: результаты сообщения SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-errors
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, errors
- errors [OLE DB], SQL Server message results
- OLE DB error handling, SQL Server message results
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 08c47b78d764e62d3e13f55b8a9aa1081d234782
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2018
---
# <a name="sql-server-message-results"></a>Результаты сообщения SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Следующие [!INCLUDE[tsql](../../../includes/tsql-md.md)] операторы не приводят к формированию драйвер OLE DB для SQL Server наборы строк или подсчет строк, затронутых при выполнении:  
  
-   PRINT  
  
-   RAISERROR (со степенью серьезности 10 или ниже)  
  
-   DBCC  
  
-   SET SHOWPLAN  
  
-   SET STATISTICS  
  
 Эти инструкции либо возвращают одно или несколько информационных сообщений, либо дают указание [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] вернуть информационные сообщения вместо набора строк или результатов вычислений. При успешном выполнении драйвер OLE DB для SQL Server возвращает значение S_OK, и сообщения доступны для драйвер OLE DB для SQL Server потребителя.  
  
 Драйвер OLE DB для SQL Server возвращает значение S_OK и имеет один или несколько информационных сообщений, появляющихся после выполнения многих [!INCLUDE[tsql](../../../includes/tsql-md.md)] инструкции или выполнении потребителем драйвер OLE DB для SQL Server функция-член.  
  
 Драйвер OLE DB для SQL Server потребителя, разрешающий динамическую спецификацию текста запроса должен проверять интерфейсы ошибок после каждого члена функции выполнения независимо от значения кода возврата, наличия или отсутствия возвращенной **IRowset** или **IMultipleResults** Справочник по интерфейсу или количество затронутых строк.  
  
## <a name="see-also"></a>См. также  
 [ошибки](../../oledb/ole-db-errors/errors.md)  
  
  
