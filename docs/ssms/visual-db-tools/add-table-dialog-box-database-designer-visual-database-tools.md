---
title: "Диалоговое окно \"Добавление таблицы\" в конструкторе базы данных (визуальные инструменты для баз данных) | Документация Майкрософт"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-visual-db
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vdtsql.chm:65555
- vdt.dlgbox.schema.addtable
ms.assetid: 3c0b1b30-795c-4240-91d6-890b8348014a
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a13a8f643a66c8357f17af11a00f47bd7ec3b5a1
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/17/2018
---
# <a name="add-table-dialog-box-database-designer-visual-database-tools"></a>Диалоговое окно «Добавление таблицы» (конструктор базы данных) (визуальные инструменты для баз данных)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] позволяет добавлять таблицы в конструкторе базы данных.  
  
> [!NOTE]  
> Если таблица опубликована для репликации, то изменения схемы следует проводить при помощи инструкции языка Transact-SQL [ALTER TABLE](http://msdn.microsoft.com/en-us/f1745145-182d-4301-a334-18f799d361d1) или объектов SMO. При изменении схемы с помощью конструктора таблиц или конструктора диаграмм баз данных конструктор пытается удалить и затем вновь создать таблицу. Но поскольку удалять опубликованные объекты нельзя, изменения схемы не будут применены.  
  
## <a name="uielement-list"></a>Список элементов пользовательского интерфейса  
**Обновить**  
Обновляет список таблиц для соответствия текущему состоянию базы данных.  
  
**Добавить**  
Добавляет выбранную таблицу или таблицы.  
  
> [!NOTE]  
> Если нужно добавить несколько таблиц к диаграмме, можно выбрать их все, а затем нажать кнопку **Добавить**. Или можно дважды щелкнуть каждую таблицу, которую нужно добавить, а затем, по окончании, нажать кнопку **Закрыть** .  
  
**Закрыть**  
Закрывает диалоговое окно без дальнейшего добавления таблиц.  
  
## <a name="see-also"></a>См. также:  
[Добавление таблиц в диаграммы (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/add-tables-to-diagrams-visual-database-tools.md)  
  
