---
title: "Создание базы данных (учебник) | Документы Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: t-sql
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- tutorial creating a database
ms.assetid: e1e2c83f-dfad-4bb8-aa7a-09d3f69517ae
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 55a63275dc9e7d130614b5dece07b7f74edd53ca
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="lesson-1-1---creating-a-database"></a>Урок 1–1. Создание базы данных
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)] Как и у многих инструкций языка [!INCLUDE[tsql](../includes/tsql-md.md)], у инструкции CREATE DATABASE имеется обязательный параметр: имя базы данных. Кроме этого, у инструкции CREATE DATABASE имеется ряд необязательных параметров, таких как расположение на диске, где требуется хранить файлы базы данных. При выполнении инструкции CREATE DATABASE без дополнительных параметров, для многих из них [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] использует значения по умолчанию. В этом учебнике используются лишь некоторые дополнительные синтаксические параметры.  
  
### <a name="to-create-a-database"></a>Создание базы данных  
  
1.  В окне редактора запросов введите, но не выполняйте, следующий код:  
  
    ```  
    CREATE DATABASE TestData  
    GO  
    ```  
  
2.  С помощью указателя выделите слова `CREATE DATABASE`и нажмите клавишу **F1**. Должен открыться раздел CREATE DATABASE электронной документации по SQL Server. Таким же способом можно найти полный синтаксис инструкции CREATE DATABASE и других инструкций, используемых в данном учебнике.  
  
3.  В редакторе запросов нажмите клавишу **F5** , чтобы выполнить инструкцию и создать базу данных с именем `TestData`.  
  
При создании базы данных сервер [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] создает копию базы данных **model** и присваивает ей указанное имя базы данных. Эта операция обычно занимает несколько секунд, если только с помощью дополнительного параметра не указан большой исходный размер базы данных.  
  
> [!NOTE]  
> Когда в одном пакете представлено несколько инструкций, они разделяются с помощью ключевого слова GO. Ключевое слово GO является необязательным, если в пакете содержится только одна инструкция.  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
[Создание таблицы (учебник)](../t-sql/lesson-1-2-creating-a-table.md)  
  
## <a name="see-also"></a>См. также:  
[CREATE DATABASE (SQL Server Transact-SQL)](../t-sql/statements/create-database-sql-server-transact-sql.md)  
  
  
  
