---
title: "Трассировка и воспроизведение событий | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: smo
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- replaying events
- traces [SMO]
- events [SMO], replaying
- events [SMO], tracing
ms.assetid: f41b3f85-2f6c-4c3e-9776-8c73d2cc7a53
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6a5501861717bf21e6004730b38f93b309c40e0e
ms.sourcegitcommit: cb2f9d4db45bef37c04064a9493ac2c1d60f2c22
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/12/2018
---
# <a name="tracing-and-replaying-events"></a>Трассировка и воспроизведение событий
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  В SMO **трассировки** и **воспроизведения** объекты в <xref:Microsoft.SqlServer.Management.Trace> пространства имен предоставляют программный доступ к [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] функциональные возможности, которые используются для наблюдения за экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]или [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Приложение позволяет собирать и сохранять данные о каждом событии в файле или в таблице для последующего анализа. Например, с помощью приложения можно наблюдать за рабочей средой, чтобы определить, какие процедуры сказываются на производительности из-за того, что выполняются слишком медленно.  
  
 **Трассировки** и **воспроизведения** объекты предоставляют набор объектов, которые могут использоваться для создания трассировок на экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Эти объекты можно использовать из пользовательских приложений для создания вручную трассировок для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] или служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Кроме того, SMO **трассировки** объекты могут использоваться для чтения файлов трассировок SQL и таблицы, которые были созданы при наблюдении за [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], или ведения журнала DTS.  
  
 Объекты **Trace** SMO позволяют выполнять следующие функции:  
  
-   создать трассировку;  
  
-   назначить фильтры для трассировки;  
  
-   назначить отслеживаемые события;  
  
-   остановить и запустить трассировку;  
  
-   прочитать файлы трассировки и таблицы трассировки;  
  
-   получить сведения о событиях трассировки;  
  
-   получить сведения о фильтрах трассировки;  
  
-   программно управлять данными трассировки;  
  
-   записать файлы и таблицы трассировки;  
  
-   воспроизвести файлы и таблицы трассировки.  
  
 Данные трассировки из **трассировки** и **воспроизведения** можно использовать объекты SMO-приложении или исследовать их вручную с помощью [SQL Server Profiler](../../../tools/sql-server-profiler/sql-server-profiler.md). Данные трассировки также совместимы с [трассировки SQL](../../../relational-databases/sql-trace/sql-trace.md) хранимые процедуры, которые также обеспечивают возможности трассировки.  
  
 Объекты трассировки SMO находятся в пространстве имен <xref:Microsoft.SqlServer.Management.Trace>, для использования которого необходима ссылка на файл Microsoft.SQLServer.ConnectionInfo.dll.  
  
 **Трассировки** и **воспроизведения** объектов требуется [ServerConnection](https://msdn.microsoft.com/en-us/library/microsoft.sqlserver.management.common.serverconnection.aspx) <xref:Microsoft.SqlServer.Management.Smo.Server.%23ctor%2A> объектов для установления соединения с экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. [ServerConnection](https://msdn.microsoft.com/en-us/library/microsoft.sqlserver.management.common.serverconnection.aspx) объект хранится в [Microsoft.SqlServer.Management.Common](https://msdn.microsoft.com/en-us/library/microsoft.sqlserver.management.common) пространства имен, которое требуется ссылка на файл Microsoft.SQLServer.ConnectionInfo.dll.  
  
> [!NOTE]  
>  Объекты **Trace** и **Replay** не поддерживаются в 64-разрядной версии платформы.  
  
  
