---
title: Подключения к базе данных Azure SQL (SybaseToSQL) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-sybase
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 96538007-1099-40c8-9902-edd07c5620ee
caps.latest.revision: 5
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c1656e76e6452c4394aad5eadb5d5b4073de9aac
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2018
---
# <a name="connect-to-azure-sql-db--sybasetosql"></a>Подключения к базе данных Azure SQL (SybaseToSQL)
Используйте подключение к базе данных SQL Azure-диалоговое окно для подключения к базе данных SQL Azure базы данных, которые требуется перенести.  
  
Чтобы открыть это диалоговое окно на **файл** последовательно выберите пункты **подключение к базе данных SQL Azure**. Если ранее вы подключились, команда является **повторно подключиться к базе данных SQL Azure.**  
  
## <a name="options"></a>Параметры  
**Имя сервера**  
  
Выберите или введите имя сервера для подключения к базе данных SQL Azure.  
  
**База данных**  
  
Выберите, введите или **Обзор** имя базы данных.  
  
> [!IMPORTANT]  
> SSMA для СУБД Sybase в базе данных SQL Azure не поддерживает подключение к базе данных master.  
  
**Имя пользователя**  
  
Введите имя пользователя, который SSMA будет использоваться для подключения к базе данных в базе данных SQL Azure  
  
**Пароль**  
  
Введите пароль для имени пользователя.  
  
**Шифрование**  
  
SSMA рекомендует зашифрованное подключение к базе данных SQL Azure.  
  
## <a name="create-azure-database"></a>Создание базы данных SQL Azure  
Если нет никаких баз данных в учетной записи базы данных SQL Azure, можно создать очень первой базы данных.  
  
Чтобы создать новую базу данных в первый раз, выполните следующие действия  
  
1.  Нажмите кнопку "Обзор", который присутствует в окне подключения к базе данных SQL Azure-диалоговое окно  
  
2.  Если нет никаких баз данных, отображаются следующие два элемента меню.  
  
    1.  **(не найдены базы данных)**  которого отключено и серым все время  
  
    2.  **Создать новую базу данных** включен только в том случае, если нет никаких баз данных в учетной записи базы данных SQL Azure. При выборе этого пункта меню, диалоговое окно создания базы данных Azure отсутствует имя базы данных и размером.  
  
3.  Во время создания базы данных следующие два параметра, назначается в качестве входных данных:  
  
    1.  **Имя базы данных:** введите имя базы данных.  
  
    2.  **Размер базы данных:** выбрать размер базы данных, который необходимо создать в базе данных SQL Azure учетной записи.  
  
