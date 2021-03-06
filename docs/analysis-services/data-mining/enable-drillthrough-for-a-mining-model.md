---
title: "Включить детализацию для модели интеллектуального анализа данных | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
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
- data mining [Analysis Services], how-to topics
- drillthrough [Analysis Services]
ms.assetid: 4fa44f60-ef9a-4b59-98c0-c0baf1195c8e
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 81778c4f9b2602c8fa49d5b33f8e1725c05122b7
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2018
---
# <a name="enable-drillthrough-for-a-mining-model"></a>включить детализацию для модели интеллектуального анализа данных
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
Если в модели интеллектуального анализа данных включена детализация, то при просмотре модели можно извлекать подробные сведения о вариантах, использованных при создании модели. Для просмотра этой информации необходимо иметь соответствующие разрешения. Структура к моменту просмотра должна быть уже обработана.  
  
 **Разрешения** . Чтобы пользователь мог детализировать данные модели или структуры, он должен быть членом роли, имеющей разрешения [AllowDrillThrough](../../analysis-services/scripting/properties/allowdrillthrough-element-assl.md) в отношении такой модели или структуры интеллектуального анализа данных. Разрешения на детализацию устанавливаются отдельно для структуры и для модели.  
  
-   Разрешения на детализацию модели позволяют проводить детализацию на основе модели даже при отсутствии разрешений на детализацию структуры.  
  
-   Разрешения на детализацию структуры предоставляют дополнительную возможность включать столбцы структуры в запросы детализации с помощью функции [StructureColumn (DMX)](../../dmx/structurecolumn-dmx.md). Можно также создавать запросы к обучающим и тестовым вариантам структуры с помощью синтаксиса SELECT… ИЗ \<структуры >. ВАРИАНТЫ синтаксиса.  
  
 **Кэширование обучающих вариантов** . Детализация работает посредством получения информации об обучающих вариантах в структуре интеллектуального анализа данных. При обработке структуры эта информация кэшируется. Поэтому, если произвести удаление всех кэшированных данных путем изменения свойства <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> на **ClearAfterProcessing**, детализация работать не будет.  
  
> [!NOTE]  
>  Если обучающие варианты не кэшированы, для просмотра данных варианта нужно сначала изменить свойство <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> на **KeepTrainingCases** , а затем провести повторную обработку модели.  
  
 Дополнительные сведения см. в разделе [Запросы детализации (интеллектуальный анализ данных)](../../analysis-services/data-mining/drillthrough-queries-data-mining.md).  
  
### <a name="to-enable-drillthrough-on-a-mining-model"></a>Включение детализации в модели интеллектуального анализа данных  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]на вкладке **Модели интеллектуального анализа данных** конструктора интеллектуального анализа данных щелкните правой кнопкой мыши модель интеллектуального анализа данных, для которой нужно включить детализацию, и выберите **Свойства**.  
  
2.  В окне **Свойства** щелкните свойство **AllowDrillthrough**и выберите значение **True**.  
  
3.  На вкладке **Модели интеллектуального анализа данных** щелкните правой кнопкой мыши нужную модель и выберите команду **Обработать модель**.  
  
### <a name="to-enable-caching-for-a-mining-structure"></a>Включение кэширования для структуры интеллектуального анализа данных  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]на вкладке **Структура интеллектуального анализа данных** конструктора интеллектуального анализа данных щелкните правой кнопкой мыши имя структуры интеллектуального анализа данных.  
  
2.  Откройте окно **Свойства** .  
  
3.  В окне **Свойства** найдите свойство **CacheMode** , а затем выберите **KeepTrainingCases** из списка.  
  
4.  В меню **База данных** выберите **Обработать**.  
  
## <a name="see-also"></a>См. также  
 [Запросы детализации &#40; интеллектуального анализа данных &#41;](../../analysis-services/data-mining/drillthrough-queries-data-mining.md)  
  
  
