---
title: LinRegPoint (многомерные Выражения) | Документы Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- LINREGPOINT
dev_langs:
- kbMDX
helpviewer_keywords:
- LinRegPoint function
ms.assetid: 28298d7c-2b8a-4423-ae52-9c2d6f0f0064
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 37c0f4b4ef73ff14d8c0f46208b94d1b96d995e7
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="linregpoint-mdx"></a>LinRegPoint (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Вычисляет линейную регрессию множества и возвращает значение *y-intercept* в линии регрессии y = ax + b для некоторого значения x.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
LinRegPoint(Slice_Expression_x, Set_Expression, Numeric_Expression_y [ ,Numeric_Expression_x ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Slice_Expression_x*  
 Допустимое числовое выражение (обычно многомерное выражение над координатами ячейки), возвращающее число, которое представляет значения для оси среза.  
  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Numeric_Expression_y*  
 Допустимое числовое выражение (обычно многомерное выражение координат ячейки), возвращающее число, которое представляет значения по оси Y.  
  
 *Numeric_Expression_x*  
 Допустимое числовое выражение (обычно многомерное выражение координат ячейки), возвращающее число, которое представляет значения по оси X.  
  
## <a name="remarks"></a>Remarks  
 Линейная регрессия, которая использует метод наименьших квадратов, вычисляет уравнение линии регрессии (то есть наиболее подходящую линию для последовательности точек). Линия регрессии имеет следующее уравнение, где — это наклон, а b-отсекаемый отрезок:  
  
 y = ax+b  
  
 **LinRegPoint** функция вычисляет заданный набор относительно второго численного выражения, чтобы получить значения для оси y. Затем функция вычисляет третье числовое выражение (если оно указано) над заданным набором, чтобы получить значения для оси X. Если третье числовое выражение не указано, функция использует текущий контекст ячеек в указанном наборе в качестве значений для оси X. Аргумент для оси X часто опускается при работе с измерением времени.  
  
 После вычисления линии линейной регрессии значение уравнения подставляется в первое числовое выражение и возвращается результат.  
  
> [!NOTE]  
>  **LinRegPoint** функция пропускает пустые ячейки и ячейки, содержащие текст. Однако функция обрабатывает ячейки с нулевыми значениями.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается прогнозируемое значение показателя Unit Sales за последние 10 периодов на основе статистической связи показателей Unit Sales и Store Sales.  
  
```  
LinRegPoint([Measures].[Unit Sales],LastPeriods(10),[Measures].[Unit Sales],[Measures].[Store Sales])  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
