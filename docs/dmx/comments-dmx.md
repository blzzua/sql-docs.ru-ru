---
title: Комментарии (расширения интеллектуального анализа данных) | Документы Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- DMX
helpviewer_keywords:
- comments [DMX]
- Data Mining Extensions [Analysis Services], comments
- double forward slashes
- commenting characters
- text strings [SQL Server]
- remarks [DMX]
- forward slash-asterisk character pairs
- DMX [Analysis Services], comments
- /*...*/ (comment)
- double hyphens
- // (comment)
- -- (comment character)
ms.assetid: 64d10eb5-4fe8-42c6-b387-eff336315e56
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 86fd2ea716fd0366149937af749c240fe01e486d
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="comments-dmx"></a>Комментарии (расширения интеллектуального анализа данных)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Комментарии в расширений интеллектуального анализа (DMX) — это текстовые строки в программе кода, [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] не выполняется. Комментарии называются также примечаниями. Комментарии можно использовать для документирования кода или временного отключения частей инструкции или скрипта расширений интеллектуального анализа данных при диагностике кода.  
  
 Использование комментариев для документирования программного кода упрощает обслуживание такого кода в будущем. С помощью комментариев можно записывать такие подробности как имя программы, имя разработчика, писавшего код, а также даты крупных изменений в коде. Комментарии можно также использовать для описания сложных вычислений или метода программирования.  
  
 Ниже приведены правила написания комментариев:  
  
-   В комментарии можно использовать любые алфавитно-цифровые символы. Все символы, находящиеся в пределах комментария, игнорируются службами [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
-   Длина комментария в инструкции или скрипте не ограничивается. Комментарии могут состоять из одной или нескольких строк.  
  
 Службы [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] поддерживают следующие типы символов комментариев:  
  
-   **(две косые черты).** Эти символы комментариев используются при написании комментария в одной строке с выполняемым кодом или для комментирования целой строки. Службы [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] считают частью комментариев все, что расположено после двойной косой черты до конца строки. Для создания многострочных комментариев следует ставить двойную косую черту в начале каждой строки. Дополнительные сведения об этом символе комментария см. в разделе [двойная косая черта &#40; Комментарий &#41; &#40; расширений интеллектуального анализа данных &#41; ](../dmx/double-slash-comment-dmx.md).  
  
-   **--(двойной дефис).** Эти символы комментариев используются при написании комментария в одной строке с выполняемым кодом или для комментирования целой строки. Службы [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] считают частью комментариев все, что расположено после двойного дефиса до конца строки. Для создания многострочных комментариев следует ставить двойной дефис в начале каждой строки. Дополнительные сведения об этом символе комментария см. в разделе [--&#40; Комментарий &#41; &#40; расширений интеллектуального анализа данных &#41; Сводка](../dmx/comment-dmx-summary.md).  
  
-   **/\*... \*/ (косая черта звездочка пары символов).** Эти символы комментариев используются при написании комментария в одной строке с выполняемым кодом, для комментирования целой строки, а также для написания комментариев внутри выполняемого кода. [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]все, что расположено между символами open (/ *) в закрывающей (\*/) в рамках комментария. Для создания многострочных комментариев следует начать комментарий с парой символами комментария (/\*), а закончить его закрывающей парой символов комментарий (\*/). Строки написанного таким образом комментария не должны включать никаких других символов комментариев. Дополнительные сведения об этом символе комментария см. в разделе [косой черты звезда &#40; Комментарий &#41; &#40; расширений интеллектуального анализа данных &#41; ](../dmx/slash-star-comment-dmx.md).  
  
## <a name="see-also"></a>См. также:  
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Ссылка](../dmx/data-mining-extensions-dmx-reference.md)   
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Справочник по функциям](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Справочник по операторам](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Справка по инструкции](../dmx/data-mining-extensions-dmx-statements.md)   
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Синтаксические обозначения](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Элементы синтаксиса](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Общие функции прогнозирования &#40; расширений интеллектуального анализа данных &#41;](../dmx/general-prediction-functions-dmx.md)   
 [Структура и использовании прогнозирующих запросов расширений интеллектуального анализа данных](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Общие сведения об инструкции SELECT в расширении интеллектуального анализа данных](../dmx/understanding-the-dmx-select-statement.md)  
  
  
