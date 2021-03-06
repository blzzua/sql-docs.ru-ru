---
title: "Создание некластеризованных индексов | Документация Майкрософт"
ms.custom: 
ms.date: 02/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: indexes
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-indexes
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- index creation [SQL Server], nonclustered indexes
- nonclustered indexes [SQL Server], creating
- nonclustered indexes [SQL Server], UNIQUE constraint
- indexes [SQL Server], nonclustered
- nonclustered indexes [SQL Server], PRIMARY KEY constraint
ms.assetid: 9402029a-1227-46c4-93aa-c2122eb1b943
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Active
ms.openlocfilehash: fa2f52d326ae38533c2c493db91e4b6a1597f491
ms.sourcegitcommit: d8ab09ad99e9ec30875076acee2ed303d61049b7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/23/2018
---
# <a name="create-nonclustered-indexes"></a>Создание некластеризованных индексов
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  Некластеризованные индексы в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] можно создать с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Некластеризованный индекс — это структура индекса, отделенная от данных, хранящихся в таблице, и переупорядочивающая один или несколько выделенных столбцов. Некластеризованные индексы часто ускоряют поиск данных по сравнению с поиском в базовой таблице. Иногда на запросы можно ответить, используя только данные из некластеризованного индекса, либо некластеризованный индекс может указать компоненту [!INCLUDE[ssDE](../../includes/ssde-md.md)] на нужные строки из базовой таблицы. Обычно некластеризованные индексы создаются с целью повышения производительности часто используемых запросов, не входящих в кластеризованный индекс, либо для поиска строк таблицы, не имеющей кластеризованного индекса (которая называется кучей). Можно создать несколько некластеризованных индексов для таблицы или индексированного представления.  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Implementations"></a> Стандартные реализации  
 Некластеризованные индексы реализуются следующим образом.  
  
-   **Ограничения UNIQUE**  
  
     При создании ограничения UNIQUE создается уникальный некластеризованный индекс. Он нужен, чтобы принудительно применять ограничение UNIQUE по умолчанию. Если кластеризованный индекс в таблице еще не создан, то можно указать уникальный кластеризованный индекс. Дополнительные сведения см. в статье [Unique Constraints and Check Constraints](../../relational-databases/tables/unique-constraints-and-check-constraints.md).  
  
-   **Индекс, не зависящий от ограничения**  
  
     По умолчанию некластеризованный индекс создается в том случае, если ранее не был задан кластеризованный индекс. Для таблицы может быть создано не более 999 некластеризованных индексов. В это число входят любые индексы, созданные ограничениями PRIMARY KEY или UNIQUE, но не входят XML-индексы.  
  
-   **Некластеризованный индекс в индексированном представлении**  
  
     Некластеризованные индексы в представлении могут создаваться только после создания в нем уникального кластеризованного индекса. Дополнительные сведения см. в разделе [Создание индексированных представлений](../../relational-databases/views/create-indexed-views.md).  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Необходимо разрешение ALTER для таблицы или представления. Пользователь должен быть членом предопределенной роли сервера **sysadmin** или предопределенных ролей базы данных **db_ddladmin** и **db_owner**.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-create-a-nonclustered-index-by-using-the-table-designer"></a>Создание некластеризованного индекса с помощью конструктора таблиц  
  
1.  В обозревателе объектов разверните базу данных, содержащую таблицу, в которой необходимо создать некластеризованный индекс.  
  
2.  Разверните папку **Таблицы** .  
  
3.  Щелкните правой кнопкой мыши таблицу, в которой нужно создать некластеризованный индекс, и выберите пункт **Конструктор**.  
  
4.  В меню **Конструктор таблиц** выберите пункт **Индексы и ключи**.  
  
5.  В диалоговом окне **Индексы и ключи** нажмите **Добавить**.  
  
6.  Выберите новый индекс в текстовом поле **Выбранный первичный/уникальный ключ или индекс** .  
  
7.  Выберите в сетке элемент **Создать как кластеризованный**и в раскрывающемся списке справа от свойства выберите значение **Нет** .  
  
8.  Щелкните **Закрыть**.  
  
9. В меню **Файл** выберите команду **Сохранить***имя_таблицы*.  
  
#### <a name="to-create-a-nonclustered-index-by-using-object-explorer"></a>Создание некластеризованного индекса в обозревателе объектов  
  
1.  В обозревателе объектов разверните базу данных, содержащую таблицу, в которой необходимо создать некластеризованный индекс.  
  
2.  Разверните папку **Таблицы**.  
  
3.  Разверните таблицу, для которой необходимо создать некластеризованный индекс.  
  
4.  Щелкните правой кнопкой мыши папку **Индексы** , выберите **Создать индекс**и **Некластеризованный индекс…**  
  
5.  В диалоговом окне **Создание индекса** на странице **Общие** введите имя нового индекса в поле **Имя индекса** .  
  
6.  В разделе **Ключевые столбцы индекса**щелкните **Добавить…**  
  
7.  В диалоговом окне **Выбор столбцов из***имя_таблицы* установите флажки для столбцов таблицы, добавляемых к некластеризованному индексу.  
  
8.  Нажмите кнопку **ОК**.  
  
9. В диалоговом окне **Создание индекса** нажмите кнопку **ОК**.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-create-a-nonclustered-index-on-a-table"></a>Создание некластеризованного индекса для таблицы  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```sql  
    USE AdventureWorks2012;  
    GO  
    -- Find an existing index named IX_ProductVendor_VendorID and delete it if found.   
    IF EXISTS (SELECT name FROM sys.indexes  
                WHERE name = N'IX_ProductVendor_VendorID')   
        DROP INDEX IX_ProductVendor_VendorID ON Purchasing.ProductVendor;   
    GO  
    -- Create a nonclustered index called IX_ProductVendor_VendorID   
    -- on the Purchasing.ProductVendor table using the BusinessEntityID column.   
    CREATE NONCLUSTERED INDEX IX_ProductVendor_VendorID   
        ON Purchasing.ProductVendor (BusinessEntityID);   
    GO  
    ```  
  
## <a name="related-content"></a>См. также  
[CREATE INDEX (Transact-SQL)](../../t-sql/statements/create-index-transact-sql.md)   
[Руководство по проектированию индексов SQL Server](../../relational-databases/sql-server-index-design-guide.md) 
