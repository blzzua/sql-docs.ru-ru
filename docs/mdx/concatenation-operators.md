---
title: Операторы объединения | Документы Microsoft
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
dev_langs:
- kbMDX
helpviewer_keywords:
- concatenation operators [MDX]
ms.assetid: 9e4c181a-b71e-41ec-98a1-ec8b5b5103b1
caps.latest.revision: 25
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 53d8d860a6725c9967dc3f16459a1782bdf93db8
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="concatenation-operators"></a>Операторы объединения
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Оператором объединения является знак плюс (+). Можно объединить две или более символьные строки в одну символьную строку. Кроме того, можно выполнять объединение двоичных строк.  
  
 В следующем примере с помощью оператора объединения выполняется объединение имени продукта и уникального имени продукта.  
  
```  
WITH MEMBER Measures.ProductName AS   
   Product.Product.CurrentMember.Name + " (" + Product.Product.CurrentMember.UniqueName + ")"  
SELECT   
   {Measures.ProductName} ON COLUMNS,  
   Product.Product.Members ON ROWS  
FROM [Adventure Works]  
```  
  
## <a name="language-considerations"></a>Дополнительные сведения  
 Если строки, участвующие в объединении, имеют одинаковые параметры сортировки, результирующая объединенная строка будет иметь те же параметры сортировки, что и исходные строки. В противном случае параметры сортировки результирующей объединенной строки определяются правилами очередности параметров сортировки. Дополнительные сведения см. в разделе [Языки и параметры сортировки (службы Analysis Services)](../analysis-services/languages-and-collations-analysis-services.md).  
  
## <a name="see-also"></a>См. также:  
 [Справочник по операторам Многомерных &#40; Многомерные Выражения &#41;](../mdx/mdx-operator-reference-mdx.md)   
 [Операторы &#40; Синтаксис многомерных Выражений &#41;](../mdx/operators-mdx-syntax.md)  
  
  
