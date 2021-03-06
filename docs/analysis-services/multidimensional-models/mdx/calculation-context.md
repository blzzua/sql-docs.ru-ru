---
title: "Контекст вычисления | Документы Microsoft"
ms.custom: 
ms.date: 03/13/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aec8aa98-b77d-4f8f-9684-2618b1d8e970
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: fde665f7dea3efe26d61d6d183f8ca35834f732e
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2018
---
# <a name="calculation-context"></a>Контекст вычисления
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
Контекстом вычисления является известное подпространство куба, где оценивается выражение, а все координаты либо известны, либо могут получены с помощью выражения.  
  
## <a name="determining-the-calculation-context"></a>Определение контекста вычисления  
 Любые набор, элемент, кортеж, числовая функция выполняются в контексте всего многомерного выражения или инструкции. Когда такой аргумент, как кортеж, передается в функцию, в явном виде задаются только некоторые координаты в пространстве куба. Для получения остальных координат используется текущий контекст вычисления.  
  
 Контекст вычисления для неуказанных координат ячейки или элементов атрибута определяется в следующем порядке.  
  
1.  Предложение FROM (если применимо). В этом предложении можно или указать куб полностью, или указать вложенный куб в виде инструкции SELECT.  
  
2.  Предложение WHERE (если применимо). В этом предложении, которое также называется *осью среза*, можно указать набор, кортеж или элемент, ограничивающий элементы, которые возвращаются запросом по осям столбцов и строк. Элемент по умолчанию каждой иерархии атрибута, который не указан явно по осям столбцов или строк, по существу является частью оси среза.  
  
    > [!NOTE]  
    >  Когда координаты ячейки для отдельного атрибута указаны и по оси среза, и по другой оси, координаты, указанные в функции, могут иметь преимущество при определении элементов набора по этой оси. Примерами таких функций являются [Filter (многомерные выражения)](../../../mdx/filter-mdx.md) и [Order (многомерные выражения)](../../../mdx/order-mdx.md) , результат можно отфильтровать или упорядочить по элементам атрибута, которые исключены из контекста вычисления предложением WHERE или инструкцией SELECT в предложении FROM.  
  
3.  Именованные наборы и вычисляемые элементы, определенные в запросе или выражении.  
  
4.  Кортежи и наборы, заданные по осям строк и столбцов и использующие элемент по умолчанию для атрибутов, которые не появляются по осям строк и столбцов и оси среза.  
  
5.  Ячейки куба или вложенного куба на каждой оси, устраняющие пустые кортежи на оси и применяющие предложение HAVING.  
  
6.  Дополнительные сведения см. в разделе [Establishing Cube Context in a Query &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/establishing-cube-context-in-a-query-mdx.md).  
  
 В следующем запросе контекст вычисления для каждой оси строк ограничен элементом атрибута Country и элементом атрибута Calendar Year, указанным в предложении WHERE.  
  
```  
SELECT Customer.City.City.Members ON 0  
FROM [Adventure Works]  
WHERE (Customer.Country.France, [Date].[Calendar].[Calendar Year].[CY 2004],  
   Measures.[Internet Sales Amount])  
```  
  
 Тем не менее, если изменить запрос, указав функцию **FILTER** по оси строк, и передать в функцию **FILTER** элемент иерархии атрибута Calendar Year, то этот элемент, который раньше использовался для определения контекста вычисления элементов набора по оси столбцов, можно изменить.  
  
```  
SELECT FILTER  
   (  
      Customer.City.City.Members,   
         ([Date].[Calendar].[Calendar Year].[CY 2003],  
            Measures.[Internet Order Quantity]) > 75   
   ) ON 0  
FROM [Adventure Works]  
WHERE (Customer.Country.France,  
   [Date].[Calendar].[Calendar Year].[CY 2004],  
   Measures.[Internet Sales Amount])  
```  
  
 В предыдущем запросе контекст вычисления ячеек в кортежах по оси столбцов фильтровался по элементу «CY 2003» иерархии атрибута Calendar Yea, даже если номинальным контекстом вычисления для иерархии атрибута Calendar Year является элемент «CY 2004». Кроме того, он фильтруется по мере Internet Order Quantity (объемов заказов через Интернет). Тем не менее, поскольку элементы набора по оси столбцов заданы, контекст вычисления значений элементов, которые отображаются на оси, опять определяется предложением WHERE.  
  
> [!IMPORTANT]  
>  Чтобы увеличить производительность запроса, следует удалить элементы и кортежи как можно раньше в процессе разрешений. Таким образом уменьшается время вычисления сложного запроса на конечном наборе элементов, поскольку запрос обрабатывает минимально возможное количество ячеек.  
  
## <a name="see-also"></a>См. также  
 [Определение контекста куба в запросе &#40; Многомерные Выражения &#41;](../../../analysis-services/multidimensional-models/mdx/establishing-cube-context-in-a-query-mdx.md)   
 [Основные принципы запросов многомерных Выражений &#40; Службы Analysis Services &#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)   
 [Ключевые понятия многомерных Выражений &#40; Службы Analysis Services &#41;](../../../analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services.md)  
  
  
