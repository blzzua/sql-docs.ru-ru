---
title: "Ограничения безопасности для SQL Server для Linux | Документы Microsoft"
description: "Данная статья содержит SQL Server в Linux ограничения."
author: rothja
ms.author: jroth
manager: craigg
ms.date: 01/30/2018
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: 
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: 64da74cc-14bf-4636-a55e-8cc1fce2aaff
ms.workload: Inactive
ms.openlocfilehash: 54e7518c24cb75e5f41f8fc6a4c5a159093ca66a
ms.sourcegitcommit: f02598eb8665a9c2dc01991c36f27943701fdd2d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/13/2018
---
# <a name="security-limitations-for-sql-server-on-linux"></a>Ограничения безопасности для SQL Server в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

SQL Server в Linux в настоящее время имеет следующие ограничения:

* Предоставляется стандартная пароля. Параметр MUST_CHANGE имеет единственный параметр, который можно настроить.  
* Расширенное управление ключами не поддерживается. 
* Использование ключей, хранящихся в хранилище ключей Azure не поддерживается.
* SQL Server создает свой собственный самозаверяющий сертификат для шифрования соединения. SQL Server можно настроить для использования пользователя, предоставленный сертификата для TLS. 

Дополнительные сведения о функции безопасности, доступные в SQL Server см. в разделе [центр обеспечения безопасности для ядра СУБД SQL Server и базы данных SQL Azure](../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md).

## <a name="next-steps"></a>Следующие шаги

Для типовых задач безопасности в разделе [приступить к работе со средствами безопасности SQL Server в Linux](sql-server-linux-security-get-started.md). Скрипт для изменения TCP порт номер каталогов SQL Server и настроить флага трассировки или параметров сортировки см. в разделе [Настройка SQL Server в Linux с mssql conf](sql-server-linux-configure-mssql-conf.md).
