---
title: "Выполнение файлов скрипта Transact-SQL с использованием программы sqlcmd | Документация Майкрософт"
ms.custom: 
ms.date: 07/15/2016
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transact sql scripts
ms.assetid: 90067eb8-ca3e-44e8-bb1a-bf7d1a359423
caps.latest.revision: 
author: mightypen
ms.author: genemi
manager: craigg
ms.workload: Active
ms.openlocfilehash: 815b9a2deb8dd4c3f81e46257ae3756eeefe9512
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2018
---
# <a name="sqlcmd---run-transact-sql-script-files"></a>sqlcmd — выполнение файлов скрипта Transact-SQL
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] Для запуска файла скрипта Transact-SQL используйте **sqlcmd**. Файл скрипта Transact-SQL является текстовым файлом, содержащим сочетание инструкций Transact-SQL, команд **sqlcmd** и переменных скрипта.  

## <a name="create-a-script-file"></a>Создание файла скрипта  
 Чтобы создать простой файл скрипта Transact-SQL, используя приложение "Блокнот", следуйте перечисленным ниже шагам.  
  
1.  Нажмите кнопку **Пуск**, последовательно укажите пункты **Все программы**, **Стандартные**и выберите пункт **Блокнот**.  
  
2.  Скопируйте и вставьте следующий код языка Transact-SQL в приложение "Блокнот":  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT p.FirstName + ' ' + p.LastName AS 'Employee Name',  
    a.AddressLine1, a.AddressLine2 , a.City, a.PostalCode   
    FROM Person.Person AS p   
       INNER JOIN HumanResources.Employee AS e   
            ON p.BusinessEntityID = e.BusinessEntityID  
        INNER JOIN Person.BusinessEntityAddress bea   
            ON bea.BusinessEntityID = e.BusinessEntityID  
        INNER JOIN Person.Address AS a   
            ON a.AddressID = bea.AddressID;  
    GO  
    ```  
  
3.  Сохраните файл под именем **myScript.sql** на диске C.  
  
## <a name="run-the-script-file"></a>Выполнение файла скрипта  
  
1.  Откройте окно командной строки.  
  
2.  В окне командной строки введите **sqlcmd -S myServer\instanceName -i C:\myScript.sql**  
  
3.  Нажмите клавишу ВВОД.  
  
 В окне командной строки будет выведен список имен и адресов сотрудников [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] .  

## <a name="save-the-output-to-a-text-file"></a>Сохранение результата в текстовом файле
  
1.  Откройте окно командной строки.  
  
2.  В окне командной строки введите **sqlcmd -S myServer\instanceName -i C:\myScript.sql -o C:\EmpAdds.txt**  
  
3.  Нажмите клавишу ВВОД.  
  
 Результат не будет выведен в окне командной строки. Он будет записан в файл EmpAdds.txt. Можно проверить полученные результаты, открыв файл EmpAdds.txt.  
  
## <a name="see-also"></a>См. также:  
 [Запуск программу sqlcmd](../../relational-databases/scripting/sqlcmd-start-the-utility.md)   
 [Служебная программа sqlcmd](../../tools/sqlcmd-utility.md)  
  
  
