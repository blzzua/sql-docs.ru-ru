---
title: "Окно контрольных значений | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
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
f1_keywords:
- vs.debug.watch
helpviewer_keywords:
- Watch Window [Transact-SQL]
ms.assetid: 23f3baa4-14c2-4262-92f7-3f43fcfa0436
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 504bd9a02382a92d21e64279c8b55f7f6f45ea9c
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2018
---
# <a name="transact-sql-debugger---watch-window"></a>Отладчик Transact-SQL, окно контрольных значений
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] В окне **Контрольные значения** приводятся сведения о выбранных выражениях. Может быть открыто четыре окна контрольных значений: **Контрольные значения 1**, **Контрольные значения 2, Контрольные значения 3**и **Контрольные значения 4**. Выражения вычисляются в области текущего кадра стека вызова, который выбран в окне **Стек вызовов** . Чтобы иметь возможность контролировать значения переменных и выражений, необходимо находиться в режиме отладки.  
  
## <a name="task-list"></a>Список задач  
 **Доступ к окнам «Контрольные значения»**  
  
-   В меню **Отладка** выберите пункт **Окна**, затем пункт **Контрольные значения**и выберите пункт **Контрольные значения 1**, **Контрольные значения 2, Контрольные значения 3**или **Контрольные значения 4**.  
  
 **Изменение значения выражения**  
  
-   Щелкните правой кнопкой мыши выражение и выберите **Изменить значение**.  
  
## <a name="columns"></a>Столбцы  
 **Название**  
 Выражения, перечисляемые отладчиком [!INCLUDE[tsql](../../includes/tsql-md.md)] . Поддерживаются следующие выражения:  
  
-   Переменные.  
  
-   Параметры.  
  
-   Системные функции, имена которых начинаются с @@.  
  
-   Выражения, построенные путем применения операторов к одной или нескольким переменным, параметрам или системным функциям, например @IntegerCounter+1 или FirstName+LastName.  
  
-   Инструкции Transact-SQL, возвращающие единственное значение, например SELECT CharacterCol FROM MyTable WHERE PrimaryKey = 1.  
  
 **Value**  
 Отображается значение, возвращаемое после оценки отладчиком [!INCLUDE[tsql](../../includes/tsql-md.md)] выражения, указанного в поле **Имя**.  
  
 Если длина выражения больше ширины столбца **Значение** , полное значение отображается в подсказке при перемещении указателя на ячейку **Значение** для этого выражения.  
  
 Значок лупы в ячейке **Значение** указывает, что доступен визуализатор отладчика [!INCLUDE[tsql](../../includes/tsql-md.md)] . В этом списке можно указать **Визуализатор текста**, **Визуализатор XML**или **Визуализатор HTML**. Чтобы выполнить запуск визуализатора отладчика, щелкните значок лупы. В отладчике [!INCLUDE[tsql](../../includes/tsql-md.md)] откроется диалоговое окно, в котором данные будут отображены в формате, соответствующем типу этих данных.  
  
 **Тип**  
 Отображает тип данных выражения.  
  
## <a name="see-also"></a>См. также:  
 [Отладчик Transact-SQL](../../relational-databases/scripting/transact-sql-debugger.md)   
 [Сведения отладчика Transact-SQL](../../relational-databases/scripting/transact-sql-debugger-information.md)   
 [окно локальных переменных](../../relational-databases/scripting/transact-sql-debugger-locals-window.md)   
 [Окно стека вызовов](../../relational-databases/scripting/transact-sql-debugger-call-stack-window.md)   
 [Диалоговое окно «Быстрая проверка»](../../relational-databases/scripting/transact-sql-debugger-quickwatch-dialog-box.md)   
 [Выражения (Transact-SQL)](../../t-sql/language-elements/expressions-transact-sql.md)  
  
  
