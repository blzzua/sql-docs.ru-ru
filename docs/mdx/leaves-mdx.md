---
title: Leaves (многомерные Выражения) | Документы Microsoft
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
- LEAVES
dev_langs:
- kbMDX
helpviewer_keywords:
- Leaves function
ms.assetid: 09f908aa-1b2d-4af9-8c8d-c023915241b2
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: e8038145cf8587c6c0d5a86461302fd7075bcee9
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="leaves-mdx"></a>Leaves (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает набор, состоящий из всех атрибутов (при необходимости, принадлежащих конкретному измерению). Для каждого атрибута x в результирующем наборе, если x является атрибутом гранулярности или напрямую или косвенно связан с атрибутом гранулярности, гранулярность устанавливается на атрибут x, не влияя на срез. **Оставляет** функция предназначена для использования внутри инструкции SCOPE или в левой части назначения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Leaves( [ Dimension_expression ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Аргумент Dimension_Expression*  
 Допустимое многомерное выражение, возвращающее измерение.  
  
## <a name="remarks"></a>Remarks  
 Конечные элементы являются кортежами, которые образуются при перекрестном соединении самых нижних уровней всех иерархий атрибутов. Вычисляемые элементы исключаются.  
  
-   Если имя измерения указано, **оставляет** функция возвращает набор, содержащий конечные элементы ключевого атрибута для заданного измерения.  
  
-   Если измерение связано с несколькими группами мер, используется группа мер в текущей области.  
  
-   Если имя измерения не указывается, функция возвращает конечные элементы всего куба.  
  
    > [!NOTE]  
    >  Если выражение измерения выносится в иерархию и уникальное имя иерархии совпадает с уникальным именем измерения (свойство измерения куба HierarchyUniqueNameStyle=ExcludeDimensionName и имя иерархии совпадает с именем измерения), используется измерение.  
  
    > [!IMPORTANT]  
    >  Если не все атрибуты имеют одинаковую гранулярность в группе мер в текущей области действия, функция возвращает ошибку.  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
