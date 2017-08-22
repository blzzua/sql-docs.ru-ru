---
title: "StructureColumn (расширения интеллектуального анализа данных) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- StructureColumn
dev_langs:
- DMX
helpviewer_keywords:
- StructureColumn function
ms.assetid: 57557536-4bfa-4fa7-bf7a-fb8722ca200d
caps.latest.revision: 15
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 3e7f727e1007c6502e6612ccef563f670837cf5c
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="structurecolumn-dmx"></a>StructureColumn (расширения интеллектуального анализа данных)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает значение столбца структуры, соответствующего указанному варианту, либо табличное значение для вложенной таблицы в указанном варианте.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
StructureColumn('structure column name')  
```  
  
## <a name="arguments"></a>Аргументы  
 structure column name  
 Имя варианта или вложенной таблицы в столбце структуры интеллектуального анализа данных.  
  
## <a name="result-type"></a>Тип результата  
 Возвращаемый тип зависит от типа столбца, который ссылается на \<имя столбца структуры > параметра. Например, если указанный столбец структуры интеллектуального анализа данных содержит скалярное значение, то функция возвращает скалярное значение.  
  
 Если же столбец структуры интеллектуального анализа данных содержит вложенную таблицу, то функция возвращает табличное значение. Затем его можно указать в предложении FROM вложенной инструкции SELECT.  
  
## <a name="remarks"></a>Замечания  
 Эта функция полиморфна и может использоваться в любом месте инструкции, где допустимы выражения, в том числе список выражений инструкции SELECT, выражение WHERE или ORDER BY.  
  
 Имя столбца в структуре интеллектуального анализа данных является строковым значением и таким образом, должны заключаться в одинарные кавычки: например, `StructureColumn('` **столбец 1**`')`. Если несколько столбцов имеют одинаковые имена, то имя определяется в контексте содержащей его инструкции SELECT.  
  
 Результаты, возвращаемые из запроса с помощью **StructureColumn** функции зависят от наличия в модели фильтров. Иными словами, фильтр модели определяет, какие из вариантов будут включены в модель интеллектуального анализа данных. Таким образом, запрос для столбца структуры способен возвращать только те варианты, которые использовались в модели интеллектуального анализа данных. Образец кода, показывающего влияние фильтров для модели интеллектуального анализа данных на таблицы вариантов и вложенные таблицы, см. в подразделе «Примеры» данного раздела.  
  
 Дополнительные сведения о том, как использовать эту функцию в инструкции DMX SELECT см. в разделе [SELECT FROM &#60; модели &#62;. ВАРИАНТЫ &#40; расширений интеллектуального анализа данных &#41; ](../dmx/select-from-model-cases-dmx.md) или [SELECT FROM &#60; структура &#62;. СЛУЧАИ](../dmx/select-from-structure-cases.md).  
  
## <a name="error-messages"></a>сообщения об ошибках  
 Следующая ошибка безопасности возникает в том случае, если пользователь не имеет разрешения на детализацию родительской структуры интеллектуального анализа данных.  
  
 Пользователь "%{user/}" не имеет разрешения на детализацию до уровня родительской структуры модели интеллектуального анализа данных "%{model/}".  
  
 Следующее сообщение об ошибке возникает в том случае, если указано недопустимое имя столбца структуры.  
  
 Столбец "%{structure-column-name/}" структуры интеллектуального анализа данных не найден в родительской структуре "%{structure/}" в текущем контексте (строка %{line/}, столбец %{column/}).  
  
## <a name="examples"></a>Примеры  
 В приведенных ниже примерах используется следующая структура интеллектуального анализа данных. Обратите внимание, что она содержит столбцы вложенных таблиц `Products` и `Hobbies`. Вложенная таблица в столбце `Hobbies` содержит единственный столбец, который используется в качестве ключа для вложенной таблицы. Вложенная таблица в столбце `Products` имеет сложную структуру и состоит из ключевого столбца и других столбцов для ввода. Следующие примеры иллюстрируют, каким образом в структуре интеллектуального анализа данных можно создать множество различных столбцов, даже если все они моделью не используются. Некоторые из этих столбцов могут не пригодиться для выявления закономерностей на уровне модели, но могут оказаться весьма удобными для детализации.  
  
```  
CREATE MINING STRUCTURE [MyStructure]   
(  
CustomerName TEXT KEY,  
Occupation TEXT DISCRETE,  
Age LONG CONTINUOUS,  
MaritalStatus TEXT DISCRETE,  
Income LONG CONTINUOUS,  
Products  TABLE  
 (  
    ProductNameTEXT KEY,  
    Quantity LONG CONTINUOUS,  
    OnSale BOOLEAN  DISCRETE  
)  
 Hobbies  TABLE  
 (  
    Hobby KEY  
 ))  
```  
  
 Затем на основе созданной структуры создадим модель интеллектуального анализа данных с использованием следующего примера кода.  
  
```  
ALTER MINING STRUCTURE [MyStructure] ADD MINING MODEL [MyModel] (  
CustomerName,  
Age,  
MaritalStatus,  
Income PREDICT,  
Products   
(  
ProductName  
) WITH FILTER(NOT OnSale)  
) USING Microsoft_Decision_Trees   
WITH FILTER(EXISTS (Products))  
```  
  
### <a name="sample-query-1-returning-a-column-from-the-mining-structure"></a>Образец запроса 1: Возвращает столбец из структуры интеллектуального анализа данных  
 Следующий образец запроса возвращает столбцы `CustomerName` и `Age`, которые определены как часть модели интеллектуального анализа данных. Однако запрос возвращает также столбец `Age`, который является частью структуры, но не входит в модель интеллектуального анализа данных.  
  
```  
SELECT CustomerName, Age, StructureColumn(‘Occupation’) FROM MyModel.CASES   
WHERE Age > 30  
```  
  
 Обратите внимание, что фильтрация строк для ограничения числа вариантов до заказчиков возрастом более 30 лет выполняется на уровне модели. Поэтому данное выражение не будет возвращать те варианты, которые включены в данные структуры, но не используются в модели. Поскольку условие фильтра, используемого при создании модели (`EXISTS (Products)`), ограничивает число вариантов теми заказчиками, которые уже приобретали продукты, в структуре могут оказаться варианты, которые не будут возвращены этим запросом.  
  
### <a name="sample-query-2-applying-a-filter-to-the-structure-column"></a>Образец запроса 2: Применение фильтра к столбцу структуры  
 Следующий образец запроса возвращает не только столбцы модели `CustomerName` и `Age` и вложенную таблицу `Products`, но и значение столбца `Quantity` вложенной таблицы, которая не является частью модели.  
  
```  
SELECT CustomerName, Age,  
(SELECT ProductName, StructureColumn(‘Quantity’) FROM Products) FROM MA.CASES   
WHERE StructureColumn(‘Occupation’) = ‘Architect’  
```  
  
 Обратите внимание, что в этом примере фильтр применен к столбцу структуры для ограничения числа вариантов данные о клиентах, имеющими профессию «Архитектор» (`WHERE StructureColumn(‘Occupation’) = ‘Architect’`). Поскольку условие фильтра модели всегда применяется к вариантам при создании модели, в модель попадут только те варианты, которые содержат в таблице `Products` как минимум одну строку, включенную в число вариантов модели. Таким образом, применяется как фильтр для вложенной таблицы `Products`, так и фильтр для варианта `(‘Occupation’)`.  
  
### <a name="sample-query-3-selecting-columns-from-a-nested-table"></a>Образец запроса 3: Выбор столбцов из вложенной таблицы  
 Следующий образец запроса возвращает имена заказчиков, которые были использованы в модели в качестве обучающих вариантов. Для каждого из заказчиков запрос возвращает также вложенную таблицу с подробными сведениями о заказах. Несмотря на то, что модель включает `ProductName` столбец, модель не использует значение `ProductName` столбца. Модель только проверяет, если продукт был приобретен по обычной (`NOT``OnSale`) цены. Этот запрос возвращает не только название продукта, но и размер приобретенной партии, который не указан в модели.  
  
```  
SELECT CustomerName,    
(SELECT ProductName, StructureColumn('Quantity')FROM Products)   
FROM MyModel.CASES  
```  
  
 Обратите внимание, что столбец `ProductName` или `Quantity` может быть возвращен, только если для модели интеллектуального анализа данных включена детализация.  
  
### <a name="sample-query-4-filtering-on-and-returning-nested-table-columns"></a>Пример запроса 4: Фильтрация по и возврат столбцов вложенной таблицы  
 Три следующих образца запросов возвращают вариант и столбцы вложенной таблицы, включенные в структуру интеллектуального анализа данных, но не являющиеся частью модели. К модели уже применен фильтр по наличию продуктов `OnSale`, но данный запрос добавит еще один фильтр по столбцу структуры интеллектуального анализа данных `Quantity`.  
  
```  
SELECT CustomerName, Age, StructureColumn('Occupation'),   
(SELECT ProductName, StructureColumn('Quantity') FROM Products)   
FROM MyModel.CASES   
WHERE EXISTS (SELECT * FROM Products WHERE StructureColumn('Quantity')>1)  
```  
  
## <a name="see-also"></a>См. также:  
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Справочник по функциям](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Функции &#40; расширений интеллектуального анализа данных &#41;](../dmx/functions-dmx.md)   
 [Общие функции прогнозирования &#40; расширений интеллектуального анализа данных &#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
