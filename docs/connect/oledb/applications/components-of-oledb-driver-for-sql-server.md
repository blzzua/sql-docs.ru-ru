---
title: Драйвер OLE DB для SQL Server компонентов | Документы Microsoft
description: Компоненты драйвера OLE DB для SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb|applications
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- data access [OLE DB Driver for SQL Server], components
- components [OLE DB Driver for SQL Server]
- MSOLEDBSQL, about OLE DB Driver for SQL Server
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 82a3a0999b2d04b699a7b8b9b0299fefc04628de
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2018
---
# <a name="components-of-ole-db-driver-for-sql-server"></a>Компоненты драйвера OLE DB для SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Драйвер OLE DB для SQL Server содержит следующие компоненты:  

|Компонент|Описание|  
|---------------|-----------------|  
|msoledbsql.dll|Файл библиотеки динамической компоновки (DLL), содержащий все драйвер OLE DB для SQL Server функциональные возможности.|  
|msoledbsqlr.rll|Сопутствующий файл ресурса для драйвера OLE DB для SQL Server библиотеки.|   
|msoledbsql.h|Драйвер OLE DB для SQL Server заголовочного файла, содержащего все новые определения, необходимые для использования драйвера OLE DB для SQL Server. Этот файл заголовка заменяет файл заголовка sqloledb.h.<br /><br /> Примечание: Можно ссылаться на msoledbsql.h и sqloledb.h в одной программе при условии, что sqloledb.h указывается первым.|  
|msoledbsql.lib|Файл библиотеки, необходимый для прямого вызова **bcp** служебных функций, которые являются частью драйвер OLE DB для SQL Server.<br /><br /> Примечание: Если есть ссылка на файл msoledbsql.lib в программном коде, необходимо убедиться в файле msoledbsql.dll в вашем системном пути, а также в системных путях пользователей, использующих данное приложение.|  

## <a name="see-also"></a>См. также  
 [Создание приложений с помощью драйвера OLE DB для SQL Server](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)  
