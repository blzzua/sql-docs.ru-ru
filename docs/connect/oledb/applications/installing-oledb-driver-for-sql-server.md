---
title: Установка драйвера OLE DB для SQL Server | Документы Microsoft
description: Установка и удаление драйвера OLE DB для SQL Server
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
- OLE DB Driver for SQL Server, uninstalling
- MSOLEDBSQL, installing
- MSOLEDBSQL, uninstalling
- Setup [OLE DB Driver for SQL Server]
- uninstalling OLE DB Driver for SQL Server
- data access [OLE DB Driver for SQL Server], uninstalling OLE DB Driver for SQL Server
- installing OLE DB Driver for SQL Server
- OLE DB Driver for SQL Server, installing
- data access [OLE DB Driver for SQL Server], installing OLE DB Driver for SQL Server
- removing OLE DB Driver for SQL Server
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: e31904372a2850d27a3fad9158dad6bbd763dc6d
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2018
---
# <a name="installing-ole-db-driver-for-sql-server"></a>Установка драйвера OLE DB для SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

Чтобы установить драйвер OLE DB для SQL Server необходимо msoledbsql.msi установщика.
Запустите программу установки и выберите нужные предпочтительным. Драйвер OLE DB для SQL Server может быть установленных side-by-side с более ранними версиями поставщиков Microsoft OLE DB.

Чтобы загрузить последнюю версию драйвера OLE DB для SQL Server перейдите на [центра загрузки Майкрософт](http://www.microsoft.com/download/details.aspx?id=56730).

Драйвер OLE DB для SQL Server файлов (msoledbsql.dll, msoledbsqlr.rll) устанавливаются в следующем расположении:  

`%SYSTEMROOT%\system32\`  

> [!NOTE]  
> Все необходимые настройки реестра для драйвера OLE DB для SQL Server, выполненных в процессе установки.  

Драйвер OLE DB для SQL Server файлов заголовков и библиотек (msoledbsql.h и msoledbsql.lib) устанавливаются в следующие расположения:  

`%PROGRAMFILES%\Microsoft SQL Server\Client SDK\OLEDB\180\SDK`  

Драйвер OLE DB для SQL Server можно распространять через msoledbsql.msi. Может потребоваться установить драйвер OLE DB для SQL Server при развертывании приложения. Один из способов установки нескольких пакетов в одном (с точки зрения пользователя) сеансе установки состоит в применении технологии построителей цепочек и загрузчиков. Дополнительные сведения см. в разделе [разработки пользовательского пакета загрузчика для Visual Studio 2005](http://go.microsoft.com/fwlink/?LinkId=115667) и [Добавление настраиваемых необходимых компонентов](http://go.microsoft.com/fwlink/?LinkId=115668).  
  
X64 msoledbsql.msi также устанавливает 32-разрядная версия драйвера OLE DB для SQL Server. Если приложение предназначено для платформы, отличной от той, которую оно было разработано, вы можете загрузить версии msoledbsql.msi x64 и x86.

При вызове msoledbsql.msi только клиентские компоненты устанавливаются по умолчанию. Клиентские компоненты — это файлы, поддерживающие работу приложения, разработанного с помощью драйвера OLE DB для SQL Server. Чтобы установить также компоненты пакета SDK, укажите в командной строке `ADDLOCAL=All`. Например:  

`msiexec /i msoledbsql.msi ADDLOCAL=ALL APPGUID={0CC618CE-F36A-415E-84B4-FB1BFF6967E1}`  

## <a name="silent-install"></a>Автоматическая установка  
 При использовании параметров/passive, / qn, /qb или /qr параметр с msiexec необходимо также указать IACCEPTMSOLEDBSQLLICENSETERMS = Да, чтобы явно указать, что вы принимаете условия лицензии конечного пользователя. Этот параметр указывается только прописными буквами.  

## <a name="uninstalling-ole-db-driver-for-sql-server"></a>При удалении драйвера OLE DB для SQL Server  
Поскольку приложения, такие как [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] сервера и [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] средства в зависимости от драйвера OLE DB для SQL Server, очень важно не удаление драйвер OLE DB для SQL Server, пока не будут удалены все зависимые приложения. Чтобы предоставить пользователям с предупреждением, что ваше приложение зависит от драйвера OLE DB для SQL Server, используйте параметра установки APPGUID в MSI-ФАЙЛЕ, как показано ниже:  

 `msiexec /i msoledbsql.msi APPGUID={0CC618CE-F36A-415E-84B4-FB1BFF6967E1}`  

Значением, передаваемым в APPGUID, служит код продукта. Код продукта необходимо создать при использовании установщика (Майкрософт) для формирования пакета установки приложения.  

## <a name="see-also"></a>См. также  
 [Создание приложений с помощью драйвера OLE DB для SQL Server](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)   
