---
title: "Добавление таблиц в запросы (визуальные инструменты для баз данных) | Документация Майкрософт"
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
helpviewer_keywords:
- inserting tables
- adding tables
- queries [SQL Server], tables
ms.assetid: 6551aa7e-31a1-4636-852a-819bc53d658b
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f19aca315ef01bc4a329d6b03ca9c07b6f2a52f6
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/17/2018
---
# <a name="add-tables-to-queries-visual-database-tools"></a>Добавление таблиц в запросы (визуальные инструменты для баз данных)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] При создании запроса извлекаются данные из таблицы или других объектов, структурированных подобно таблицам, таких как представления и некоторые пользовательские функции. Чтобы любые из этих объектов можно было использовать в запросе, их следует добавить на **панель диаграммы**.  
  
### <a name="to-add-a-table-or-table-valued-object-to-a-query"></a>Добавление таблицы или возвращающего табличное значение объекта в запрос  
  
1.  Щелкните правой кнопкой мыши **панель диаграммы** конструктора запросов и представлений и выберите в контекстом меню пункт **Добавить таблицу** .  
  
2.  В диалоговом окне **Добавление таблицы** выберите вкладку, соответствующую типу объекта, который нужно добавить в запрос.  
  
3.  В списке элементов дважды щелкните каждый элемент, который нужно добавить.  
  
4.  Завершив добавление элементов, нажмите кнопку **Закрыть**.  
  
    После этого конструктор запросов и представлений обновит соответствующим образом **панель диаграммы**, **панель критериев**и **панель SQL** .  
  
Таблицы и представления автоматически добавляются в запрос при ссылке на них в инструкции, вводимой на панели SQL  
  
Конструктор запросов и представлений не отображает столбцы таблицы или табличного объекта, если недостаточно прав для этого или если поставщик не может возвратить информацию о них. В таких случаях для таблицы или возвращающего табличное значение объекта отображаются только заголовок окна и флажок * (Все столбцы).  
  
### <a name="to-add-an-existing-query-to-a-new-query"></a>Добавление существующего запроса в новый запрос  
  
1.  Убедитесь в том, что для создаваемого запроса отображается **панель SQL** .  
  
2.  Введите на **панели SQL**после слова FROM левую и правую скобки ().  
  
3.  Откройте для существующего запроса конструктор запросов (теперь должны быть открыты два конструктора запросов).  
  
4.  Отобразите **панель SQL** для внутреннего запроса, то есть существующего запроса, который включается в новый, внешний запрос.  
  
5.  Выделите весь текст на **панели SQL**и скопируйте его в буфер обмена.  
  
6.  Щелкните **панель SQL** нового запроса, установите курсор между добавленными скобками и вставьте в них содержимое буфера обмена.  
  
7.  Продолжая работать на **панели SQL**, укажите псевдоним после правой скобки.  
  
## <a name="see-also"></a>См. также:  
[Создание псевдонимов таблицы (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/create-table-aliases-visual-database-tools.md)  
[Удаление таблиц из запросов (визуальные инструменты для базы данных)](../../ssms/visual-db-tools/remove-tables-from-queries-visual-database-tools.md)  
[Определение критериев поиска (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/specify-search-criteria-visual-database-tools.md)  
[Резюмирование результатов запросов (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/summarize-query-results-visual-database-tools.md)  
[Выполнение основных операций с запросами (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
  
