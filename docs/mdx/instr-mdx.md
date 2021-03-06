---
title: "InStr (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 5638c358-47da-40ad-b988-1a5214c05492
caps.latest.revision: "6"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 7a6b5a1a987662fbe4ec0bcab4241ac0d6ff3109
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="instr-mdx"></a>Instr (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает положение первого экземпляра строки внутри другой строки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
InStr([start, ]searched_string, search_string[, compare])  
```  
  
## <a name="arguments"></a>Аргументы  
 *Запуск*  
 Числовое выражение, задающее начальную позицию для каждого поиска (необязательный). Если это значение не указано, поиск начинается с позиции первого символа. Если параметр start имеет значение null, возвращаемое значение функции не определено.  
  
 *searched_string*  
 Строковое выражение, в котором выполняется поиск.  
  
 *search_string*  
 Строковое выражение, которое необходимо найти.  
  
 *Сравнение*  
 Целочисленное значение (не обязательно). Этот аргумент никогда не учитывается. Определяется для совместимости с другими **Instr** функции на других языках.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Целочисленное значение, начальная позиция *String2* в *String1*.  
  
 Кроме того **InStr** функция возвращает значения, перечисленные в следующей таблице, в зависимости от условия:  
  
|Условие|Возвращаемое значение|  
|---------------|------------------|  
|String1 имеет нулевую длину|ноль (0)|  
|String1 содержит значение NULL|неопределенный|  
|String2 имеет нулевую длину|start|  
|String2 содержит значение NULL|неопределенный|  
|Значение String2 не найдено|ноль (0)|  
|начало больше Len(String2)|ноль (0)|  
  
## <a name="remarks"></a>Remarks  
  
> [!WARNING]  
>  **InStr** всегда выполняет сравнение без учета регистра.  
  
## <a name="example"></a>Пример  
 В следующем примере показано использование метода **Instr** и различные сценарии результатов.  
  
```  
with   
    member [Date].[Date].[Results] as "Results"  
    member measures.[lowercase found in lowercase string] as InStr( "abcdefghijklmnñopqrstuvwxyz", "o")  
    member measures.[uppercase found in lowercase string] as InStr( "abcdefghijklmnñopqrstuvwxyz", "O")  
    member measures.[searched string is empty]            as InStr( "", "o")  
    member measures.[searched string is null]             as iif(IsError(InStr( null, "o")), "Is Error", iif(IsNull(InStr( null, "o")), "Is Null","Is undefined"))  
    member measures.[search string is empty]              as InStr( "abcdefghijklmnñopqrstuvwxyz", "")  
    member measures.[search string is empty start 10]     as InStr(10, "abcdefghijklmnñopqrstuvwxyz", "")  
    member measures.[search string is null]               as iif(IsError(InStr( null, "o")), "Is Error", iif(IsNull(InStr( null, "o")), "Is Null","Is undefined"))  
    member measures.[found from start 10]                 as InStr( 10, "abcdefghijklmnñopqrstuvwxyz", "o")  
    member measures.[NOT found from start 17]             as InStr( 17, "abcdefghijklmnñopqrstuvwxyz", "o")  
    member measures.[NULL start]                          as iif(IsError(InStr( null, "abcdefghijklmnñopqrstuvwxyz", "o")), "Is Error", iif(IsNull(InStr( null, "abcdefghijklmnñopqrstuvwxyz", "o")), "Is Null","Is undefined"))  
    member measures.[start greater than searched length]  as InStr( 170, "abcdefghijklmnñopqrstuvwxyz", "o")  
  
select  [Results] on columns,  
       { measures.[lowercase found in lowercase string]  
       , measures.[uppercase found in lowercase string]  
       , measures.[searched string is empty]  
       , measures.[searched string is null]  
       , measures.[search string is empty]  
       , measures.[search string is empty start 10]  
       , measures.[search string is null]  
       , measures.[found from start 10]  
       , measures.[NOT found from start 17]  
       , measures.[NULL start]   
       , measures.[start greater than searched length]  
       } on rows  
  
from [Adventure Works]  
```  
  
 В следующей таблице показаны полученные результаты.  
  
|||  
|-|-|  
||Результаты|  
|в строке нижнего регистра найдены символы в нижнем регистре|16|  
|в строке нижнего регистра найдены символы в верхнем регистре|16|  
|искомая строка пуста|0|  
|искомая строка имеет значение NULL|Не задано|  
|строка поиска пуста|1|  
|строка поиска пуста, начало 10|10|  
|искомая строка имеет значение NULL|Не задано|  
|найдено от начало 10|16|  
|НЕ найдено от начало 17|0|  
|Значение NULL в начале|Не задано|  
|начало больше искомой длины|0|  
  
  
