---
title: "Фильтры для моделей интеллектуального анализа данных (службы Analysis Services — Интеллектуальный анализ данных) | Документы Microsoft"
ms.custom: 
ms.date: 03/20/2017
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
- attributes [data mining]
- filter syntax [data mining]
- models [Analysis Services], filtering
- filters [data mining]
- filtering data [Analysis Services]
ms.assetid: 0f29c19c-4be3-4bc7-ab60-f4130a10d59c
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 83c491408707f1a7107a3bb6d485418189d9eb1c
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2018
---
# <a name="filters-for-mining-models-analysis-services---data-mining"></a>Фильтры для моделей интеллектуального анализа данных (службы Analysis Services — интеллектуальный анализ данных)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
Фильтрация моделей на основе данных помогает создавать модели интеллектуального анализа, использующие подмножества данных в структуре интеллектуального анализа данных. Фильтрация обеспечивает гибкость при проектировании структур интеллектуального анализа и источников данных, поскольку это позволяет создать одну структуру интеллектуального анализа на основе всеобъемлющего представления источников данных. Затем можно создать фильтры для использования части данных для обучения и проверки различных моделей, а не строить отдельную структуру и связанную с ней модель для каждого подмножества данных.  
  
 Например, определяется представление источника данных для таблицы Customers и связанных с ней таблиц. Далее определяется единая структура интеллектуального анализа данных, в состав которой входят все необходимые поля. Наконец, создается модель, которая фильтруется по определенному атрибуту покупателя, например по региону. Это позволяет легко копировать данную модель либо создавать новые модели на основе различных регионов путем изменения только условий фильтра.  
  
 Ниже приведены некоторые реальные сценарии, когда данная функция может оказаться весьма полезной.  
  
-   Создание отдельных моделей для таких дискретных значений, как пол, регионы и т. д. Например, магазин одежды может строить раздельные модели по признаку пола на основе демографических данных покупателей, даже если данные о продажах поступают из единого источника данных для всех покупателей.  
  
-   Эксперименты с моделями путем создания и тестирования различного группирования одинаковых данных, например возраста 20-30 лет по сравнению с возрастом 20-40 лет и 20-25 лет.  
  
-   Настройка сложных фильтров для содержимого вложенных таблиц, например требования, чтобы вариант включался в модель, только если покупатель приобрел не менее двух оопределенных наименований товара.  
  
 В этом разделе описаны способы создания и использования фильтров для моделей интеллектуального анализа данных, а также управление этими фильтрами.  
  
## <a name="creating-model-filters"></a>Создание фильтров моделей  
 Создавать и применять фильтры можно следующими способами.  
  
-   Создание условий с помощью диалоговых окон редактора фильтров на вкладке **Модели интеллектуального анализа данных** в конструкторе интеллектуального анализа данных.  
  
-   Ввод критериев фильтра непосредственно в свойстве **Фильтр** модели интеллектуального анализа данных.  
  
-   Программная настройка условий фильтра в модели с помощью объектов AMO.  
  
### <a name="creating-model-filters-using-data-mining-designer"></a>Создание фильтров моделей с помощью конструктора интеллектуального анализа данных  
 Модель в конструкторе интеллектуального анализа данных фильтруется путем изменения свойства **Filter** в этой модели. Можно ввести критерий фильтра непосредственно на панели **Свойства** либо открыть диалоговое окно фильтра для построения условий.  
  
 Есть два диалоговых окна фильтра. В первом создаются условия, применяемые к таблице вариантов. Если источник данных содержит несколько таблиц, то сначала нужно выбрать таблицу, затем столбец, после чего следует указать операторы и условия, которые должны к нему применяться. Несколько условий связываются с помощью операторов **AND**/**OR** . Операторы, доступные в качестве определяемых значений, зависят от значений в столбце: дискретных или непрерывных. Например, в случае непрерывных значений можно использовать операторы **greater than** и **less than** . Однако для дискретных значений можно использовать только операторы **= (равно)**, **! = (не равно)**и **имеет значение null** .  
  
> [!NOTE]  
>  Ключевое слово **LIKE** не поддерживается. Для включения нескольких дискретных атрибутов необходимо создать несколько отдельных условий и связать их с помощью оператора **OR** .  
  
 Если условия сложные, можно работать одновременно только с одной таблицей с помощью второго диалогового окна. При закрытии второго диалогового окна фильтра выражение вычисляется, а затем сочетается с условиями фильтра других столбцов в таблице вариантов.  
  
### <a name="creating-filters-on-nested-tables"></a>Создание фильтров во вложенных таблицах  
 Если представление источника данных содержит вложенные таблицы, то во втором диалоговом окне фильтров можно создавать условия для строк во вложенных таблицах.  
  
 Например, если таблица вариантов связана с покупателями, а во вложенной таблице показаны продукты, приобретенные покупателями, то можно создать фильтр для покупателей, которые приобрели определенные товары. Это можно сделать с помощью приведенного синтаксиса в фильтре вложенной таблицы: `[ProductName]=’Water Bottle’ OR ProductName=’Water Bottle Cage'`.  
  
 Кроме того, можно отфильтровать данные по существованию определенного значения во вложенной таблице с помощью ключевых слов **EXISTS** или **NOT EXISTS** и вложенного запроса. Это позволяет создавать такие условия, как `EXISTS (SELECT * FROM Products WHERE ProductName=’Water Bottle’)`. Условие `EXISTS SELECT(<subquery>)` возвращает значение **true** , если вложенная таблица содержит хотя бы одну строку, включающую значение `Water Bottle`.  
  
 Можно сочетать условия в таблице вариантов с условиями во вложенной таблице. Например, в показанном ниже синтаксисе приведены условие в таблице вариантов (`Age > 30` ), вложенный запрос к вложенной таблице (`EXISTS (SELECT * FROM Products)`), а также несколько условий к вложенной таблице (`WHERE ProductName=’Milk’  AND Quantity>2`).  
  
```  
(Age > 30 AND EXISTS (SELECT * FROM Products WHERE ProductName=’Milk’  AND Quantity>2) )  
```  
  
 Когда построение фильтра завершено, текст фильтра вычисляется службами [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], переводится в DMX-выражение и после этого сохраняется в модели.  
  
 Инструкции по применению диалоговых окон фильтра в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]см. в разделе [Применение фильтра к модели интеллектуального анализа данных](../../analysis-services/data-mining/apply-a-filter-to-a-mining-model.md).  
  
## <a name="managing-mining-model-filters"></a>Управление фильтрами моделей интеллектуального анализа данных  
 Фильтрация моделей на основе данных значительно упрощает задачу управления структурами и моделями интеллектуального анализа данных за счет возможности создавать несколько моделей на основе одной структуры. Кроме того, можно быстро создавать копии существующих моделей интеллектуального анализа данных и затем изменять только условия фильтра. Однако из-за фильтров может возникнуть определенная путаница.  
  
 Далее приведены некоторые часто задаваемые вопросы о том, как управлять фильтрами и интерпретировать фильтры для моделей интеллектуального анализа данных.  
  
### <a name="how-can-i-tell-whether-a-filter-is-being-used"></a>Как узнать, используется ли фильтр?  
 Существует несколько способов определения того, применен ли фильтр к модели.  
  
-   В конструкторе перейдите на вкладку **Модели интеллектуального анализа данных** , откройте **Свойства**и найдите свойство **Filter** модели интеллектуального анализа данных.  
  
-   Динамическое административное представление DMSCHEMA_MINING_MODELS выдает столбец с текстом фильтра. С помощью следующего запроса к динамическому административному представлению можно возвратить имена моделей и примененные к ним фильтры:  
  
    ```  
    SELECT MODEL_NAME, [FILTER]   
    FROM $SYSTEM.DMSCHEMA_MINING_MODELS  
  
    ```  
  
-   Можно получить значение свойства Filter объекта MiningModel в объектах AMO или найти элемент Filter XML для аналитики.  
  
 Также можно установить соглашение об именовании для моделей, чтобы в имени отражалось содержимое фильтра. Это упростит различение связанных моделей.  
  
### <a name="how-can-i-save-a-filter"></a>Как сохранить фильтр?  
 Критерий фильтра сохраняется в виде скрипта, который хранится в связанной модели интеллектуального анализа данных или во вложенной таблице. Если удалить текст фильтра, его можно восстановить только вручную путем повторного создания критерия фильтра. Таким образом, при создании сложных критериев фильтра следует создавать также резервные копии текста фильтра.  
  
### <a name="why-cant-i-see-any-effects-from-the-filter"></a>Почему я не вижу никакого эффекта от применения фильтра?  
 Всякий раз при изменении или добавлении критерия фильтра необходимо выполнять повторную обработку структуры и модели, чтобы изменения вступили в силу.  
  
### <a name="why-do-i-see-filtered-attributes-in-prediction-query-results"></a>Почему в результатах прогнозирующего запроса присутствуют отфильтрованные атрибуты?  
 При применении фильтра к модели он действует только на выборку вариантов, которые использовались для обучения модели. Фильтр не затрагивает атрибуты, которые известны модели, а также не меняет и не подавляет данные, которые имеются в источнике данных. В результате этого запросы к модели могут возвращать прогнозы для вариантов других типов, а в раскрывающихся списках значений, используемых моделью, могут присутствовать значения атрибутов, исключенных фильтром.  
  
 Например, предположим, что производится обучение модели [Покупатель велосипеда] с использованием только вариантов, включающих женщин в возрасте 20–30 лет. При этом можно выполнить прогнозирующий запрос, который предсказывает вероятность покупки велосипеда мужчиной либо вероятность покупки женщиной в возрасте 30–40 лет. Происходит это потому, что атрибуты и значения, имеющиеся в источнике данных, определяют то, что теоретически возможно, тогда как варианты определяют совершенные действия, используемые для обучения. Однако такие запросы возвратят очень незначительные вероятности, поскольку обучающие данные не содержат никаких вариантов с целевыми значениями.  
  
 Если требуется полностью скрыть или сделать анонимными значения атрибутов в модели, то для этого существуют различные варианты.  
  
-   Фильтрация входящих данных в рамках определения представления источника данных или в реляционном источнике данных.  
  
-   Экранирование или кодировка значения атрибута.  
  
-   Сворачивание исключенных значений в категорию в рамках определения структуры интеллектуального анализа данных.  
  
## <a name="related-resources"></a>Связанные ресурсы  
 Дополнительные сведения о синтаксисе фильтров и примеры выражений фильтра см. в разделе [Синтаксис и примеры фильтра модели (службы Analysis Services — интеллектуальный анализ данных)](../../analysis-services/data-mining/model-filter-syntax-and-examples-analysis-services-data-mining.md).  
  
 Сведения об использовании фильтров модели при тестировании модели интеллектуального анализа данных см. в разделе [Выбор типа диаграммы точности и задание параметров диаграммы](../../analysis-services/data-mining/choose-an-accuracy-chart-type-and-set-chart-options.md).  
  
## <a name="see-also"></a>См. также  
 [Синтаксис и примеры фильтра модели (службы Analysis Services — интеллектуальный анализ данных)](../../analysis-services/data-mining/model-filter-syntax-and-examples-analysis-services-data-mining.md)   
 [Тестирование и проверка &#40; интеллектуального анализа данных &#41;](../../analysis-services/data-mining/testing-and-validation-data-mining.md)  
  
  
