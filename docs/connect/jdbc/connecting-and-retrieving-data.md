---
title: "Соединение и извлечение данных | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ce43cc20-46a3-42ff-a3fb-75ad1ed10e08
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 856e4ea4fe28bf8884ea498a747d0bb4e9753699
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="connecting-and-retrieving-data"></a>Соединение и извлечение данных
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  При работе с [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], существует два основных способа подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных. Один — задать свойства подключения в URL-АДРЕСЕ соединения и вызова метода getConnection для возвращения класса DriverManager [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) объекта.  
  
> [!NOTE]  
>  Список свойств соединения, поддерживаемых драйвером JDBC см. в разделе [задание свойств соединения](../../connect/jdbc/setting-the-connection-properties.md).  
  
 Второй метод включает в себя задание свойств соединения с помощью методов задания [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md) класса и затем вызвать [getConnection](../../connect/jdbc/reference/getconnection-method-sqlserverdatasource.md) метод для возврата SQLServerConnection объект.  
  
 Подразделы этого раздела описываются различные способы, в которой вы можете подключиться к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных, а также демонстрируются различные методики извлечения данных.  
  
## <a name="in-this-section"></a>В этом разделе  
  
|Раздел|Description|  
|-----------|-----------------|  
|[Пример URL-адреса подключения](../../connect/jdbc/connection-url-sample.md)|Описывает, как использовать URL-адрес подключения для подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] и затем использовать инструкцию SQL для получения данных.|  
|[Пример источника данных](../../connect/jdbc/data-source-sample.md)|Описывается порядок использования источника данных для соединения с SQL Server и последующего использования хранимой процедуры для извлечения данных.|  
  
## <a name="see-also"></a>См. также:  
 [Пример приложений драйвера JDBC](../../connect/jdbc/sample-jdbc-driver-applications.md)  
  
  
