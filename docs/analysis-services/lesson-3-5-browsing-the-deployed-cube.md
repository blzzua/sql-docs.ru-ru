---
title: "Просмотр развернутого куба | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 849c6109-1453-4fe4-a892-c49a982cfadb
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 8ddbefdcbc54c076c801e5f4d83e107e48ac5ba9
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2018
---
# <a name="lesson-3-5---browsing-the-deployed-cube"></a>Занятие 3-5-Просмотр развернутого куба
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

В этой задаче будет проводиться просмотр куба [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial. Так как при проведении анализа сравниваются несколько измерений, для просмотра данных воспользуемся сводной таблицей Excel. Разместим в сводной таблице информацию о клиенте, дате и продукте на разных осях, чтобы было видно, как изменяются продажи через Интернет в различные периоды времени, для различных групп клиентов и продуктовых линий.  
  
### <a name="to-browse-the-deployed-cube"></a>Просмотр развернутого куба  
  
1.  Чтобы перейти в конструктор кубов в среде [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], дважды щелкните куб «Учебник по **[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] »** в папке **Кубы** в обозревателе решений.  
  
2.  Перейдите на вкладку **Браузер** и на панели инструментов конструктора нажмите кнопку **Повторное соединение** .  
  
3.  Щелкните значок Excel, чтобы запустить программу Excel, используя в качестве источника базу данных рабочей области. Нажмите кнопку **Включить**при появлении запроса на подключение к данным.  
  
4.  В списке полей сводной таблицы разверните группу **Продажи через Интернет**, а затем перетащите показатель **Объем продаж** в область **Значения** .  
  
5.  В списке полей сводной таблицы разверните узел **Продукт**.  
  
6.  Перетащите пользовательскую иерархию **Product Model Lines** в область **Столбцы** .  
  
7.  В списке полей сводной таблицы разверните узел **Клиент**, затем узел **Местоположение**и перетащите иерархию **Customer Geography** из папки отображения расположения в область **Строки** .  
  
8.  В списке полей сводной таблицы разверните узел **Дата заказа**и перетащите иерархию **Order Date.Calendar Date** в область **Фильтр отчета** .  
  
9. Нажмите стрелку справа от фильтра **Order Date.Calendar Date** на панели данных, снимите флажок для уровня **(Все)** , последовательно разверните узлы **2006**, **H1 CY 2006**и **Q1 CY 2006**, установите флажок **Февраль 2006**и нажмите кнопку **ОК**.  
  
    На экран будут выведены продажи через Интернет по регионам и линейкам продуктов в феврале 2006 г., как показано на следующем рисунке.  
  
    ![Продажи через Интернет по регионам и сериям продуктов](../analysis-services/media/l3-cube-browser-finish.gif "продажи через Интернет по регионам и сериям продуктов")  
  
## <a name="next-lesson"></a>Следующее занятие  
[Урок 4: Определение расширенных атрибутов и свойств измерений](../analysis-services/lesson-4-defining-advanced-attribute-and-dimension-properties.md)  
  
  
  
