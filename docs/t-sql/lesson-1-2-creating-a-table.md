---
title: "Создание таблицы (учебник) | Документы Майкрософт"
ms.custom: 
ms.date: 04/18/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating tables
ms.assetid: 653f2dd3-36a2-4bd5-8703-71a57d244661
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 452150637ddf034ed1b69c2d0a32c9ad4c4e5977
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="lesson-1-2---creating-a-table"></a>Урок 1–2. Создание таблицы
[!INCLUDE[tsql-appliesto-ss2008-all-md](../includes/tsql-appliesto-ss2008-all-md.md)]

Чтобы создать таблицу, нужно указать имя таблицы, имена и типы данных для каждого столбца таблицы. Также рекомендуется указывать, допускаются ли значения NULL для каждого из столбцов. Для создания таблицы необходимо иметь разрешение `CREATE TABLE` и разрешение `ALTER SCHEMA` для схемы, которая будет содержать таблицу. Предопределенная роль базы данных `db_ddladmin` имеет эти разрешения.  
  
Большинство таблиц имеют первичный ключ, состоящий из одной или нескольких столбцов таблицы. Первичный ключ всегда уникален. Компонент [!INCLUDE[ssDE](../includes/ssde-md.md)] потребует выполнения условия неповторения значения первичного ключа в таблице.  
  
Список типов данных и ссылки на их описание см. в разделе [Типы данных (Transact-SQL)](../t-sql/data-types/data-types-transact-sql.md).  
  
> [!NOTE]  
> Компонент [!INCLUDE[ssDE](../includes/ssde-md.md)] может быть установлен с учетом регистра и без учета регистра. Если компонент [!INCLUDE[ssDE](../includes/ssde-md.md)] установлен с учетом регистра, имена объектов должны иметь одно и тоже имя. Например, таблица с именем OrderData будет отличаться от таблицы ORDERDATA. Если компонент [!INCLUDE[ssDE](../includes/ssde-md.md)] установлен без учета регистра, эти два имени таблицы будут рассматриваться как одна таблица, то есть имя может быть использовано только один раз.  
  
### <a name="to-create-a-database-to-contain-the-new-table"></a>Создание базы данных, в которой будет размещаться новая таблица  
  
-   Введите следующий код в окно редактора запросов.  
  
    ```  
    USE master;  
    GO  
  
    --Delete the TestData database if it exists.  
    IF EXISTS(SELECT * from sys.databases WHERE name='TestData')  
    BEGIN  
        DROP DATABASE TestData;  
    END  
  
    --Create a new database called TestData.  
    CREATE DATABASE TestData;  
    Press the F5 key to execute the code and create the database.  
    ```  
  
### <a name="switch-the-query-editor-connection-to-the-testdata-database"></a>Переключение соединения редактора запросов на базу данных TestData  
  
-   В окне редактора запросов введите и выполните следующий код, чтобы изменить соединение на базу данных `TestData` .  
  
    ```  
    USE TestData  
    GO  
    ```  
  
### <a name="to-create-a-table"></a>Создание таблицы  
  
-   В окне редактора запросов введите и выполните следующий код, чтобы создать простую таблицу `Products`. Столбцы таблицы имеют имена `ProductID`, `ProductName`, `Price`и `ProductDescription`. Столбец `ProductID` является первичным ключом таблицы. `int`, `varchar(25)`, `money`и `text` . Только столбцы `Price` и `ProductionDescription` могут быть пустыми при вставке или изменении строки. Данная инструкция содержит необязательный элемент (`dbo.`), называемый схемой. Схема — это объект базы данных, к которому принадлежит таблица. Если вы являетесь администратором, схемой по умолчанию будет схема `dbo` . `dbo` означает владельца базы данных.  
  
    ```  
    CREATE TABLE dbo.Products  
       (ProductID int PRIMARY KEY NOT NULL,  
        ProductName varchar(25) NOT NULL,  
        Price money NULL,  
        ProductDescription text NULL)  
    GO  
    ```  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
[Вставка данных в таблицу и их обновление (учебник)](../t-sql/lesson-1-3-inserting-and-updating-data-in-a-table.md)  
  
## <a name="see-also"></a>См. также:  
[CREATE TABLE (Transact-SQL)](../t-sql/statements/create-table-transact-sql.md)  
  
  
  

