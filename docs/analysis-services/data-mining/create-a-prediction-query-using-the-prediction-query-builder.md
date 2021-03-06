---
title: "Создание прогнозирующего запроса с помощью построителя прогнозирующих запросов | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- prediction queries [Analysis Services]
- Mining Model Prediction [Analysis Services], prediction queries
ms.assetid: e02836e5-dd8c-4c97-a078-840ae79d3660
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: af9277de8848136f2123b7acf476dbee80a92ce1
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2018
---
# <a name="create-a-prediction-query-using-the-prediction-query-builder"></a>Создание прогнозирующего запроса с помощью построителя прогнозирующих запросов
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
Создать прогнозирующий запрос можно при создании решения интеллектуального анализа данных в среде BI Development Studio. Можно также щелкнуть правой кнопкой мыши существующую модель интеллектуального анализа данных в среде SQL Server Management Studio и выбрать параметр **Построить прогнозирующий запрос**.  
  
 **Построитель прогнозирующих запросов** имеет три режима конструктора. Для перехода из одного режима в другой используются значки в верхнем левом углу.  
  
-   **Конструирование**  
  
-   **Запрос**  
  
-   **Результат**  
  
 Режим**конструктора** позволяет создать прогнозирующий запрос, для чего необходимо выбрать входные данные, связать данные с моделью, а затем добавить прогнозирующие функции в инструкции, создаваемые с помощью сетки. Сетка конструктора содержит следующие строительные блоки.  
  
 **Source**  
 Выберите источник нового столбца. Можно использовать столбцы из модели интеллектуального анализа данных, входных таблиц, включенных в представление источника данных, прогнозирующей функции или пользовательского выражения.  
  
 **Поле**  
 Определяет конкретный столбец или функцию, связанные с элементом, выбранным в столбце **Источник** .  
  
 **Псевдоним**  
 Определяет, как столбец будет называться в результирующем наборе.  
  
 **Показать**  
 Определяет, отображается ли элемент, выбранный в столбце **Источник** , в результатах.  
  
 **Группирование**  
 Работает со столбцом **и/или** для группирования выражений с использованием скобок. Например, (expr1 или expr2) и expr3.  
  
 **и/или**  
 Создает логику в запросе. Например, (expr1 или expr2) и expr3.  
  
 **Критерий/Аргумент**  
 Указывает условие или пользовательское выражение, которое применяется к столбцу. Можно перетаскивать столбцы из таблиц в ячейку.  
  
 Режим**запросов** предоставляет текстовый редактор, обеспечивающий прямой доступ к языку DMX, а также к представлению входных данных и столбцов модели. Если выбран режим **запросов** , сетка, которая использовалась для определения запроса, заменяется базовым текстовым редактором. Этот редактор можно использовать для копирования и сохранения созданных запросов или для вставки существующих DMX-запросов через буфер обмена и выполнения этих запросов.  
  
 Представление**результатов** выполняет текущий запрос и показывает результаты в сетке. Если базовые данные изменились и необходимо выполнить запрос еще раз, нажмите кнопку «Выполнить» в строке состояния.  
  
 При создании запроса интеллектуального анализа данных можно одновременно использовать и визуальные средства и текстовый редактор. Если внести изменения в запрос в текстовом редакторе и вернуться в представление **конструктора** , все изменения будут потеряны и запрос вернется к исходному виду, в котором он был создан построителем прогнозирующих запросов.  
  
### <a name="to-create-a-prediction-query"></a>Создание прогнозирующего запроса  
  
1.  Перейдите на вкладку **Прогноз моделей интеллектуального анализа данных** в конструкторе интеллектуального анализа данных.  
  
2.  Нажмите кнопку **Выбрать модель** в таблице **Модель интеллектуального анализа данных** .  
  
     Откроется диалоговое окно **Выбор модели интеллектуального анализа данных** со списком всех структур интеллектуального анализа данных, существующих в текущем проекте.  
  
3.  Выберите модель, по которой нужно сделать прогноз, и нажмите кнопку **ОК**.  
  
4.  В окне **Выбор входных таблиц** нажмите кнопку **Выбрать таблицу вариантов**.  
  
     Откроется диалоговое окно **Выбор таблицы** .  
  
5.  Из списка **Источник данных** выберите источник данных, содержащий данные, на основе которых необходимо создать прогноз.  
  
6.  В поле **Имя таблицы или представления** выберите таблицу, содержащую данные, на основе которых необходимо создать прогноз, а затем нажмите кнопку **ОК**.  
  
     После выбора входной таблицы в построителе прогнозирующих запросов будет создано сопоставление по умолчанию между моделью интеллектуального анализа данных и таблицей входных данных на основе имен столбцов. Для удаления сопоставления щелкните кнопкой мыши, чтобы выбрать строку, связывающую столбец в таблице **Модель интеллектуального анализа данных** с сопоставляемым столбцом в таблице **Выбор входных таблиц** , а затем нажмите клавишу DELETE. Можно также вручную создать сопоставления, щелкнув столбец в таблице **Выбор входных таблиц** и перетащив его в соответствующий столбец в таблице **Модель интеллектуального анализа данных** .  
  
7.  Добавьте любое сочетание следующих типов данных в сетку построителя прогнозирующих запросов.  
  
    -   Прогнозируемые столбцы из поля **Модель интеллектуального анализа данных** .  
  
    -   Любое сочетание входных столбцов из поля **Выбор входных таблиц** .  
  
    -   Прогнозирующие функции  
  
8.  Запустите запрос, нажав первую кнопку на панели инструментов вкладки **Прогноз моделей интеллектуального анализа данных** , а затем выбрав пункт **Результат**.  
  
## <a name="see-also"></a>См. также  
 [Создание одноэлементного запроса в конструкторе интеллектуального анализа данных](../../analysis-services/data-mining/create-a-singleton-query-in-the-data-mining-designer.md)   
 [Запросы интеллектуального анализа данных](../../analysis-services/data-mining/data-mining-queries.md)  
  
  
