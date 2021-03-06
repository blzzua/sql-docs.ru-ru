---
title: "Классы OLAP объектов AMO | Документы Microsoft"
ms.custom: 
ms.date: 02/14/2018
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Analysis Management Objects, OLAP
- OLAP [AMO]
- AMO, OLAP
ms.assetid: 397509b7-a4fb-40de-aa30-c66dc9ed2105
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 609958fd81ee7c703d7608f9a353c15658c1528b
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2018
---
# <a name="amo-olap-classes"></a>Классы OLAP объектов AMO
  Классы OLAP объектов AMO позволяют создавать, изменять, удалять и обрабатывать кубы, измерения и связанные с ними объекты, например ключевые показатели эффективности, действия и упреждающее кэширование.  
  
 Дополнительные сведения о настройке среды программирования объектов AMO как для установления соединения с сервером, доступ к базе данных или определение данных источников и представления источников данных, в разделе [основные классы объектов AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-fundamental-classes.md).  
  
 Этот раздел состоит из следующих подразделов.  
  
-   [Объекты измерений](#Dimensions)  
  
-   [Объекты куба](#Cubes)  
  
-   [Объекты MeasureGroup](#MeasureGroups)  
  
-   [Объекты partition](#Partition)  
  
-   [Объекты AggregationDesign](#AggregationDesign)  
  
-   [Объекты Aggregation](#Aggregation)  
  
-   [Объекты Action](#Action)  
  
-   [Объекты KPI](#KPI)  
  
-   [Объекты перспективы](#Perspective)  
  
-   [Объекты Translation](#Translation)  
  
-   [Объекты ProactiveCaching](#ProactiveCaching)  
  
 На следующем рисунке показана связь между классами, описываемыми в этом разделе.  
  
 ![Классы OLAP объектов AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/media/amo-olapclasses.gif "классы OLAP объектов AMO")  
  
## <a name="basic-classes"></a>Основные классы  
  
###  <a name="Dimensions"></a> Объекты измерений  
 Измерение создается путем его добавления в коллекцию измерений родительской базы данных и обновления объекта <xref:Microsoft.AnalysisServices.Dimension> на сервере методом Update.  
  
 Удалить измерение можно при помощи метода Drop объекта <xref:Microsoft.AnalysisServices.Dimension>. При удалении объекта <xref:Microsoft.AnalysisServices.Dimension> из коллекции измерений базы данных методом Remove он удаляется не на сервере, а только в модели объектов AMO.  
  
 После создания объект <xref:Microsoft.AnalysisServices.Dimension> может быть обработан. Обработка объекта <xref:Microsoft.AnalysisServices.Dimension> производится либо собственным методом обработки, либо методом обработки родительского объекта во время обработки этого родительского объекта.  
  
 Дополнительные сведения о доступных методах и свойствах см. в описании класса <xref:Microsoft.AnalysisServices.Dimension> из пространства имен <xref:Microsoft.AnalysisServices>.  
  
###  <a name="Cubes"></a> Объекты куба  
 Куб создается путем его добавления в коллекцию кубов базы данных и обновления объекта <xref:Microsoft.AnalysisServices.Cube> на сервере методом Update. Методу Update куба может быть передан параметр UpdateOptions.ExpandFull, который обновляет на сервере все изменившиеся объекты куба в рамках текущей операции обновления.  
  
 Удалить куб можно при помощи метода Drop объекта <xref:Microsoft.AnalysisServices.Cube>. Удаление куба из коллекции не влияет на сервер.  
  
 После создания объект <xref:Microsoft.AnalysisServices.Cube> может быть обработан. Обработка объекта <xref:Microsoft.AnalysisServices.Cube> производится либо собственным методом обработки, либо методом обработки родительского объекта во время обработки этого родительского объекта.  
  
 Дополнительные сведения о доступных методах и свойствах см. в описании класса <xref:Microsoft.AnalysisServices.Cube> из пространства имен <xref:Microsoft.AnalysisServices>.  
  
###  <a name="MeasureGroups">Объекты MeasureGroup</a>  
 Группа мер создается путем ее добавления в коллекцию групп мер куба и обновления объекта <xref:Microsoft.AnalysisServices.MeasureGroup> на сервере методом Update. Удалить объект <xref:Microsoft.AnalysisServices.MeasureGroup> можно при помощи собственного метода Drop.  
  
 После создания объект <xref:Microsoft.AnalysisServices.MeasureGroup> может быть обработан. Обработка объекта <xref:Microsoft.AnalysisServices.MeasureGroup> производится либо собственным методом обработки, либо методом обработки родительского объекта во время обработки этого родительского объекта.  
  
 Дополнительные сведения о доступных методах и свойствах см. в описании класса <xref:Microsoft.AnalysisServices.MeasureGroup> из пространства имен <xref:Microsoft.AnalysisServices>.  
  
###  <a name="Partition">Объекты partition</a>  
 Объект <xref:Microsoft.AnalysisServices.Partition> создается путем его добавления в коллекцию секций родительской группы мер и обновления объекта <xref:Microsoft.AnalysisServices.Partition> на сервере методом Update. Удалить объект <xref:Microsoft.AnalysisServices.Partition> можно методом Drop.  
  
 Дополнительные сведения о доступных методах и свойствах см. в описании класса <xref:Microsoft.AnalysisServices.Partition> из пространства имен <xref:Microsoft.AnalysisServices>.  
  
###  <a name="AggregationDesign">Объекты AggregationDesign</a>  
 Создание статистических схем производится методом AggregationDesign объекта <xref:Microsoft.AnalysisServices.AggregationDesign>.  
  
 Дополнительные сведения о доступных методах и свойствах см. в описании класса <xref:Microsoft.AnalysisServices.AggregationDesign> из пространства имен <xref:Microsoft.AnalysisServices>.  
  
###  <a name="Aggregation">Объекты Aggregation</a>  
 Объект <xref:Microsoft.AnalysisServices.Aggregation> создается путем его добавления в коллекцию статистических схем родительской группы мер и ее обновления на сервере методом Update. Удаление агрегата из объекта <xref:Microsoft.AnalysisServices.AggregationCollection> производится методом Remove или RemoveAt.  
  
 Дополнительные сведения о доступных методах и свойствах см. в описании класса <xref:Microsoft.AnalysisServices.Aggregation> из пространства имен <xref:Microsoft.AnalysisServices>.  
  
## <a name="advanced-classes"></a>Дополнительные классы  
 Дополнительные классы обеспечивают функции OLAP, не связанные с построением и обзором куба. Далее приведены некоторые из дополнительных классов и описаны их преимущества.  
  
-   Классы действий позволяют создавать активные ответные действия во время просмотра определенных областей куба.  
  
-   Ключевые показатели эффективности позволяют выполнять сравнительный анализ значений данных.  
  
-   Перспективы предоставляют выбранные представления одного куба, позволяя пользователям концентрироваться на том, что для них важно.  
  
-   Переводы позволяют настраивать куб в соответствии с локалью пользователя.  
  
-   Классы упреждающего кэширования поддерживают баланс между производительностью хранилища MOLAP и оперативностью данных хранилища ROLAP, а также обеспечивают плановую обработку секций.  
  
 Объекты AMO задают определения для этих улучшений, однако фактический результат зависит от обозревателя клиента, который их реализует.  
  
###  <a name="Action">Объекты Action</a>  
 Объект <xref:Microsoft.AnalysisServices.Action> создается путем его добавления в коллекцию действий куба и обновления объекта <xref:Microsoft.AnalysisServices.Cube> на сервере методом Update. Методу Update куба может быть передан параметр UpdateOptions.ExpandFull, который обновляет на сервере все изменившиеся объекты куба в рамках текущей операции обновления.  
  
 Чтобы удалить объект <xref:Microsoft.AnalysisServices.Action>, его необходимо удалить из коллекции и обновить родительский куб.  
  
 Чтобы действие можно было использовать на стороне клиента, сначала необходимо обновить и обработать куб.  
  
 Дополнительные сведения о доступных методах и свойствах см. в описании класса <xref:Microsoft.AnalysisServices.Action> из пространства имен <xref:Microsoft.AnalysisServices>.  
  
###  <a name="KPI"></a> Объекты KPI  
 Объект <xref:Microsoft.AnalysisServices.Kpi> создается путем его добавления в коллекцию ключевых показателей эффективности куба и обновления объекта <xref:Microsoft.AnalysisServices.Cube> на сервере методом Update. Методу Update куба может быть передан параметр UpdateOptions.ExpandFull, который обновляет на сервере все изменившиеся объекты куба в рамках текущей операции обновления.  
  
 Чтобы удалить объект <xref:Microsoft.AnalysisServices.Kpi>, его необходимо удалить из коллекции и обновить родительский куб.  
  
 Вначале должны быть проведены обновление и обработка куба, и только после этого появляется возможность использовать ключевой показатель эффективности.  
  
 Дополнительные сведения о доступных методах и свойствах см. в описании класса <xref:Microsoft.AnalysisServices.Kpi> из пространства имен <xref:Microsoft.AnalysisServices>.  
  
###  <a name="Perspective">Объекты перспективы</a>  
 Объект <xref:Microsoft.AnalysisServices.Perspective> создается путем его добавления в коллекцию перспектив куба и обновления объекта <xref:Microsoft.AnalysisServices.Cube> на сервере методом Update. Методу Update куба может быть передан параметр UpdateOptions.ExpandFull, который обновляет на сервере все изменившиеся объекты куба в рамках текущей операции обновления.  
  
 Чтобы удалить объект <xref:Microsoft.AnalysisServices.Perspective>, его необходимо удалить из коллекции и обновить родительский куб.  
  
 Вначале должны быть проведены обновление и обработка куба, и только после этого появляется возможность использовать перспективу.  
  
 Дополнительные сведения о доступных методах и свойствах см. в описании класса <xref:Microsoft.AnalysisServices.Perspective> из пространства имен <xref:Microsoft.AnalysisServices>.  
  
###  <a name="Translation">Объекты Translation</a>  
 Объект <xref:Microsoft.AnalysisServices.Translation> создается путем его добавления в коллекцию переводов и обновления ближайшего основного родительского объекта на сервере методом Update. Методу Update ближайшего родительского объекта может быть передан параметр UpdateOptions.ExpandFull, который обновляет на сервере все изменившиеся дочерние объекты в рамках текущей операции обновления.  
  
 Чтобы удалить объект <xref:Microsoft.AnalysisServices.Translation>, его необходимо удалить из коллекции и обновить ближайший родительский объект.  
  
 Дополнительные сведения о доступных методах и свойствах см. в описании класса <xref:Microsoft.AnalysisServices.Translation> из пространства имен <xref:Microsoft.AnalysisServices>.  
  
###  <a name="ProactiveCaching">Объекты ProactiveCaching</a>  
 Объект <xref:Microsoft.AnalysisServices.ProactiveCaching> создается путем его добавления в коллекцию объектов упреждающего кэширования измерения или секции и обновления объекта измерения или секции на сервере методом Update.  
  
 Чтобы удалить объект <xref:Microsoft.AnalysisServices.ProactiveCaching>, его необходимо удалить из коллекции и обновить родительский объект.  
  
 Чтобы включить и подготовить к работе упреждающее кэширование, необходимо сначала обновить и обработать измерение или секцию.  
  
 Дополнительные сведения о доступных методах и свойствах см. в описании класса <xref:Microsoft.AnalysisServices.ProactiveCaching> из пространства имен <xref:Microsoft.AnalysisServices>.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.AnalysisServices>   
 [Знакомство с классами объектов AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-classes-introduction.md)   
 [Программирование основных объектов AMO OLAP](../../../analysis-services/multidimensional-models/analysis-management-objects/programming-amo-olap-basic-objects.md)   
 [Программирование объектов AMO расширенных объектов OLAP](../../../analysis-services/multidimensional-models/analysis-management-objects/programming-amo-olap-advanced-objects.md)   
 [Логическая архитектура &#40; Analysis Services — многомерные данные &#41;](../../../analysis-services/multidimensional-models/olap-logical/understanding-microsoft-olap-logical-architecture.md)   
 [Объекты базы данных &#40; Analysis Services — многомерные данные &#41;](../../../analysis-services/multidimensional-models/olap-logical/database-objects-analysis-services-multidimensional-data.md)  
  
  
