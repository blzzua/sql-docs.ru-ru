---
title: + (Объединение) (МНОГОМЕРНЫЕ ВЫРАЖЕНИЯ) | Документы Microsoft
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
- +
dev_langs:
- kbMDX
helpviewer_keywords:
- union operator (+)
- + (union operator)
ms.assetid: 6c6dfca2-7413-452a-98a2-3d8c58a8a3e6
caps.latest.revision: 43
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: a936895822b842d2d08672c4c05bd8c1a416064c
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="union---mdx-operator-reference"></a>UNION - Справочник по операторам многомерных Выражений
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Выполняет операцию над наборами, которая возвращает объединение двух наборов с удалением повторяющихся элементов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Set_Expression + Set_Expression      
```  
  
#### <a name="parameters"></a>Параметры  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Набор, содержащий элементы обоих заданных наборов.  
  
## <a name="remarks"></a>Remarks  
 **+ (Объединения)** оператор функционально эквивалентен [Union &#40; Многомерные Выражения &#41; ](../mdx/union-mdx.md) функции.  
  
## <a name="examples"></a>Примеры  
 В следующем примере демонстрируется использование этого оператора.  
  
```  
-- This member returns the gross profit margin for each year for North American countries.  
SELECT   
    [Date].[Calendar].[Calendar Year].Members ON 0,  
    {[Sales Territory].[Sales Territory].[Country].[United States]} +  
     {[Sales Territory].[Sales Territory].[Country].[Canada]} ON 1  
FROM  
    [Adventure Works]  
WHERE  
    ([Measures].[Gross Profit Margin])  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по операторам Многомерных &#40; Многомерные Выражения &#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
