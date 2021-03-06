---
title: Перенос баз данных MySQL в SQL Server — база данных Azure SQL | Документы Microsoft
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-mysql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 8006f9a0-394d-4238-8dc5-44255134628b
caps.latest.revision: 12
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: afd5e6aee5fb59c6e3eebb11c47d04b09e37bd40
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2018
---
# <a name="migrating-mysql-databases-to-sql-server---azure-sql-db-mysqltosql"></a>Миграция баз данных MySQL в SQL Server — базы данных Azure SQL (MySQLToSql)
SQL Server Migration Assistant (SSMA) для MySQL — это комплексный среда, которая поможет вам быстро перенести базы данных MySQL в SQL Server или SQL Azure. С помощью SSMA для MySQL, можно просмотреть объекты базы данных и данных, оценки баз данных для миграции, миграция объектов базы данных в SQL Server или SQL Azure и затем выполните перенос данных в SQL Server или SQL Azure.  
  
## <a name="recommended-migration-process"></a>Рекомендуется использовать процесс миграции  
Для успешного переноса объектов и данных из базы данных MySQL в SQL Server или SQL Azure, воспользуйтесь следующей процедурой:  
  
1.  [Работа с проектами SSMA &#40;MySQLToSQL&#41;](../../ssma/mysql/working-with-ssma-projects-mysqltosql.md).  
  
    После создания проекта можно задать преобразование проекта, миграции и параметры сопоставления типов. Дополнительные сведения о параметрах проекта см. в разделе [задание параметров проекта &#40;MySQLToSQL&#41;](../../ssma/mysql/setting-project-options-mysqltosql.md). Сведения о том, как настроить сопоставления типов данных см. в разделе [сопоставление MySQL и типов данных SQL Server &#40;MySQLToSQL&#41;](../../ssma/mysql/mapping-mysql-and-sql-server-data-types-mysqltosql.md)  
  
2.  [Подключение к MySQL &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-mysql-mysqltosql.md)  
  
3.  [Подключение к SQL Server &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-sql-server-mysqltosql.md)  
  
4.  [Сопоставление баз данных MySQL в схемы SQL Server &#40;MySQLToSQL&#41;](../../ssma/mysql/mapping-mysql-databases-to-sql-server-schemas-mysqltosql.md)  
  
5.  [Подключение к базе данных Azure SQL &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-azure-sql-db-mysqltosql.md)  
  
6.  При необходимости [оценки баз данных MySQL для преобразования &#40;MySQLToSQL&#41; ](../../ssma/mysql/assessing-mysql-databases-for-conversion-mysqltosql.md) для оценки для преобразования объектов базы данных и оценить время преобразования.  
  
7.  [Преобразование базы данных MySQL &#40;MySQLToSQL&#41;](../../ssma/mysql/converting-mysql-databases-mysqltosql.md)  
  
8.  [Синхронизация](http://msdn.microsoft.com/en-us/ac993a6d-0283-4823-8793-6b217677dfa3)  
  
9. Это можно сделать одним из следующих способов:  
  
    -   Сохранить сценарий и запустите его на SQL Server или SQL Azure.  
  
    -   Синхронизируйте объекты базы данных.  
  
10. [Перенос данных MySQL в SQL Server — Azure SQL DB &#40;MySQLToSQL&#41;](../../ssma/mysql/migrating-mysql-data-into-sql-server-azure-sql-db-mysqltosql.md)  
  
11. При необходимости обновить базу данных приложения.  
  
> [!NOTE]  
> Невозможно выполнить миграцию схем Information_schema и MySQL.  
  
## <a name="see-also"></a>См. также  
[Установка SSMA для MySQL &#40;MySqlToSql&#41;](../../ssma/mysql/installing-ssma-for-mysql-mysqltosql.md)  
[Начало работы с SSMA для MySQL &#40;MySQLToSQL&#41;](../../ssma/mysql/getting-started-with-ssma-for-mysql-mysqltosql.md)  
  
