---
title: "Создание запросов с неименованными параметрами (визуальные инструменты для баз данных) | Документация Майкрософт"
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
- unnamed parameters
- parameters [SQL Server], unnamed
ms.assetid: 5f4b664b-3d3d-4d07-a0e7-791d78743504
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 33e5ffe37109fa5d1f5f85ed7c6ef9689aa01ec3
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/17/2018
---
# <a name="create-queries-with-unnamed-parameters-visual-database-tools"></a>Создание запросов с неименованными параметрами (визуальные инструменты для баз данных)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] Запросы с неименованными параметрами создаются с указанием вопросительного знака (?) в качестве заполнителя литерала. Конструктор запросов и представлений присваивает такому параметру временное имя. В запросе можно указать любое число неименованных параметров.  
  
При запуске запроса в конструкторе запросов и представлений в диалоговом окне параметров запроса отображается временное имя.  
  
### <a name="to-specify-an-unnamed-parameter"></a>Указание неименованного параметра  
  
1.  Добавьте столбцы или выражения, для которых нужно произвести поиск, на [панель критериев](../../ssms/visual-db-tools/criteria-pane-visual-database-tools.md). Если столбцы или выражения поиска не нужно включать в результат запроса, их необходимо удалить из списка выходных столбцов.  
  
2.  Укажите строку, в которой содержится столбец данных или выражение для поиска, и в столбце сетки **Фильтр** введите вопросительный знак (?).  
  
    По умолчанию конструктор запросов и представлений добавляет оператор «=». Однако можно отредактировать ячейку и заменить его на оператор «>», «<» или любой другой оператор сравнения языка SQL.  
  
## <a name="see-also"></a>См. также:  
[Запрос с параметрами (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/query-with-parameters-visual-database-tools.md)  
  
