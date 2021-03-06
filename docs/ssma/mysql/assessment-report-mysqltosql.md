---
title: Оценка отчетов (MySQLToSQL) | Документы Microsoft
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
ms.assetid: 5525d989-024c-402d-9e84-faa4721cc5b9
caps.latest.revision: 4
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 37ea0744861296d4a3ec4a97f3736835bfd23b0b
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2018
---
# <a name="assessment-report-mysqltosql"></a>Оценка отчетов (MySQLToSQL)
Окно отчета оценки показывает результаты преобразования объектов базы данных для [!INCLUDE[tsql](../../includes/tsql_md.md)] синтаксис, и поможет оценить сложность и стоимость проектов миграции.  
  
Доступ к отчету оценки, выбирать объекты для преобразования в обозревателе метаданных источника, щелкните правой кнопкой мыши **схемы**, а затем выберите **создать отчет**.  
  
## <a name="options"></a>Параметры  
  
|||  
|-|-|  
|**Термин**|**Определение**|  
|**Преобразование статистики**|Показывает статистику типом оператора преобразования. В этой области отображается при создании объекта группы, например схеме или на панели слева выбран объект без кода.|  
|**Объекты по категориям**|Указывает число объектов по категориям. В этой области отображается только тогда, когда объект группы, например схемы, или на панели слева выбран объект без кода.|  
|**Статистика**|Показывает статистику преобразования для выбранного объекта. В этой области отображается только при выборе отдельного объекта с кодом на панели слева. Может потребоваться развернуть **статистики**, который находится сразу над **источника** панели для просмотра этой панели.|  
|**Source**|Показывает код MySQL для выбранного объекта, а также код, который не был преобразован в [!INCLUDE[tsql](../../includes/tsql_md.md)]. В этой области отображается только при выборе отдельного объекта с кодом на панели слева.<br /><br />Щелкните номера строк, чтобы установить или снять закладки. Используйте кнопки в верхней части области перемещаться по коду.|  
|**Цель**|Показывает что преобразование [!INCLUDE[tsql](../../includes/tsql_md.md)] код для выбранного объекта и сообщения об ошибках для кода, который не был преобразован. В этой области отображается только при выборе отдельного объекта с кодом на панели слева.<br /><br />Щелкните номера строк, чтобы установить или снять закладки. Используйте кнопки в верхней части области перемещаться по коду.|  
|**Панель сообщений**|Показывает ошибки, предупреждения и информационные сообщения, которые были созданы при создании отчета оценки. Сообщения группируются по номеру. Чтобы просмотреть код, который вызвал ошибку, нажмите кнопку **ошибки**, **предупреждения**, или **сведения**, разверните категорию сообщений и нажмите кнопку сообщения.|  
  
