---
title: "Окно \"Пространственные результаты\" | Документация Майкрософт"
ms.custom: 
ms.date: 03/01/2017
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
ms.assetid: c2d5a477-6496-4d01-adee-7322ebdfadf3
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7374f5ba8c17d85d86d414bd42095e1aa44f9c96
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2018
---
# <a name="spatial-results-window"></a>Окно «Пространственные результаты»
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] Окно **Пространственные результаты** содержит визуальные средства сопоставления для просмотра пространственных данных. Чтобы использовать окно «Пространственные результаты», результаты запроса должны содержать по крайней мере один пространственный столбец с данными геометрического или географического типа.  
  
> [!NOTE]  
>  Окно **Пространственные результаты** доступно только в случае, если результаты возвращаются в сетку в окне **Результаты** . Если для результатов задано возвращение в виде текста, это окно будет недоступно.  
  
## <a name="options"></a>Параметры  
 **Выберите пространственный столбец**  
 Укажите пространственный столбец для просмотра из числа пространственных столбцов в результатах запроса. В один момент времени можно выбрать только один столбец.  
  
 **Выберите столбец меток**  
 Укажите непространственный столбец из числа столбцов, возвращаемых в результатах запроса, чтобы задать метки для пространственных данных. В один момент времени можно выбрать только один столбец.  
  
 Этот параметр недоступен, если в запросе возвращаются только объекты Point.  
  
 **Выберите проекцию**  
 Географические данные отображаются в одной из четырех проекций: равноугольная проекция, проекция Меркатора, проекция Робинзона или проекция Бонна.  
  
 Этот параметр недоступен для геометрических данных.  
  
 **Масштаб**  
 Регулирует отображение карты по экспоненциальной шкале.  
  
 **Отобразить линии сетки**  
 Включает или выключает линии координатной сетки.  
  
 Для фигур-многоугольников метка будет отображаться только в случае, если фигура достаточно велика, чтобы вместить текст метки. Чтобы показать метки для маленьких фигур, увеличьте масштаб.  
  
> [!NOTE]  
>  Для экземпляров Point нельзя задавать метки.  
  
## <a name="see-also"></a>См. также:  
 [Просмотр пространственных данных в обозревателе объектов](../../relational-databases/scripting/view-spatial-data-in-object-explorer.md)   
 [Пространственные данные (SQL Server)](../../relational-databases/spatial/spatial-data-sql-server.md)   
 [Редактор запросов компонента Database Engine (среда SQL Server Management Studio)](../../relational-databases/scripting/database-engine-query-editor-sql-server-management-studio.md)   
 [Редакторы запросов и текста (SQL Server Management Studio)](../../relational-databases/scripting/query-and-text-editors-sql-server-management-studio.md)  
  
  
