---
title: "Определение свойства среза секции (службы Analysis Services) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
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
- partitions [Analysis Services], data slices
- data slices [Analysis Services]
ms.assetid: 507b91e5-7f85-4c22-be97-4d7a676e6667
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 92a61b6d5d860ae94fdc3d38212fed45ed2363bc
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2018
---
# <a name="set-the-partition-slice-property-analysis-services"></a>Определение свойства среза секции (службы Analysis Services)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
Срез данных является важной функцией оптимизации, которая помогает направить запросы к данным соответствующих секций. Прямое указание свойства Slice позволяет повысить производительность запросов, переписав стандартные срезы, сформированные для секций MOLAP и HOLAP. Также свойство Slice обеспечивает дополнительную проверку при обработке секции.  
  
 С помощью свойства Slice можно задать срез данных после создания секции, но до ее обработки. На вкладке "Секции" разверните группу мер, щелкните правой кнопкой мыши секцию и выберите **Свойства**.  
  
 Описание преимуществ использования срезов данных см. в разделе [Указание среза в секции куба служб SSAS](http://go.microsoft.com/fwlink/?LinkId=317783).  
  
## <a name="defining-a-slice"></a>Определение среза  
 Допустимые значения для свойства среза — элемент многомерного выражения, набор или кортеж. В следующем примере показан допустимый синтаксис среза.  
  
|Срез|Элемент, набор или кортеж|  
|-----------|--------------------------|  
|[Date].[Calendar].[Calendar Year].&[2010]|Укажите этот срез в секции, содержащей факты из 2010 года (предполагается, что модель включает измерение Date с иерархией Calendar Year, в которую входит элемент 2010). Хотя предложение WHERE (источник секции) или таблица уже могли выполнить фильтрацию по 2010, указание Slice дает дополнительную проверку во время обработки, а также более точное сканирование во время выполнения запроса.|  
|{ [Sales Territory].[Sales Territory Country].&[Australia], [Sales Territory].[Sales Territory Country].&[Canada] }|Укажите данный срез для секции, содержащей факты, которые включают сведения о продажах по территориям. Срез может быть набором многомерных выражений, состоящим из двух и более элементов.|  
|[Measures].[Sales Amount Quota] > '5000'|Этот срез демонстрирует многомерное выражение.|  
  
 Срез данных секции должен как можно точнее соответствовать данным в секции. Например, если секция ограничена данными за 2012 год, то срез данных секции должен определять элемент 2012 измерения «Время». Не всегда возможно указать срез данных, точно отражающий содержимое секции. Например, если секция содержит данные только за январь и февраль, а уровнями измерения Time являются «Год», «Квартал» и «Месяц», то мастер секционирования не может выбрать только элементы «Январь» и «Февраль». В таких случаях выберите родительский элемент, отражающий содержимое секции. В данном примере выберите «Квартал 1».  
  
> [!NOTE]  
>  Обратите внимание, что динамические функции многомерных выражений (такие как [Generate (многомерное выражение)](../../mdx/generate-mdx.md) или [Except (многомерное выражение)](../../mdx/except-mdx-function.md)) не поддерживаются в свойстве Slice для секций. Необходимо определить срез с помощью явных кортежей или ссылок на элементы.  
>   
>  Например, вместо того чтобы использовать оператор диапазона (:) для определения диапазона, потребуется перечислить каждый элемент по конкретным годам.  
>   
>  Если необходимо определить сложный срез, рекомендуется идентифицировать кортежи в срезе с помощью скрипта изменения XMLA. Затем вы можете использовать программу командной строки ascmd или элемент [Задача "Выполнение DDL службами Analysis Services"](../../integration-services/control-flow/analysis-services-execute-ddl-task.md) в службах Integration Services для запуска скрипта и создания указанного набора элементов непосредственно перед секционированием.  
  
## <a name="see-also"></a>См. также  
 [Создание и управление локальной секции &#40; Службы Analysis Services &#41;](../../analysis-services/multidimensional-models/create-and-manage-a-local-partition-analysis-services.md)  
  
  
