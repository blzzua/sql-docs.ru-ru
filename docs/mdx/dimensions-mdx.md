---
title: Измерения (многомерные Выражения) | Документы Microsoft
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
- Dimensions
dev_langs:
- kbMDX
helpviewer_keywords:
- Dimensions function
ms.assetid: 64f63aa0-ef74-4415-a0c9-8acc6cd81739
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: e14d37c916240c0c7cc454df50d44d4de4ba319a
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="dimensions-mdx"></a>Dimensions (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает иерархию, указанную числовым или строковым выражением.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Numeric expression syntax  
Dimensions(Hierarchy_Number)  
  
String expression syntax  
Dimensions(Hierarchy_Name)  
```  
  
## <a name="arguments"></a>Аргументы  
 *Hierarchy_Number*  
 Допустимое числовое выражение, указывающее номер иерархии.  
  
 *Hierarchy_Name*  
 Допустимое строковое выражение, указывающее имя иерархии.  
  
## <a name="remarks"></a>Remarks  
 Если указан номер иерархии, **измерения** функция возвращает иерархии, отсчитываемый от нуля позиция в пределах куба которого является указанным номером иерархии.  
  
 Если имя иерархии указано, **измерения** функция возвращает указанную иерархию. Как правило, используется это строковая версия **измерения** функцию с определяемой пользователем функции.  
  
> [!NOTE]  
>  **Меры** измерения всегда имеет `Dimensions(0)`.  
  
## <a name="examples"></a>Примеры  
 В следующих примерах используется **измерения** функция возвращает имя, количество уровней и количество элементов указанной иерархии, с помощью числового выражения и строкового выражения.  
  
```  
WITH MEMBER Measures.x AS Dimensions  
   ('[Product].[Product Model Lines]').Name  
SELECT Measures.x on 0  
FROM [Adventure Works]  
  
WITH MEMBER Measures.x AS Dimensions  
   ('[Product].[Product Model Lines]').Levels.Count  
SELECT Measures.x on 0  
FROM [Adventure Works]  
  
WITH MEMBER Measures.x AS Dimensions  
   ('[Product].[Product Model Lines]').Members.Count  
SELECT Measures.x on 0  
FROM [Adventure Works]  
  
WITH MEMBER Measures.x AS Dimensions(0).Name  
SELECT Measures.x on 0  
FROM [Adventure Works]  
  
WITH MEMBER Measures.x AS Dimensions(0).Levels.Count  
SELECT measures.x on 0  
FROM [Adventure Works]  
  
WITH MEMBER Measures.x AS Dimensions(0).Members.Count  
SELECT measures.x on 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
