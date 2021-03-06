---
title: "Основные понятия AMO и объектной моделью | Документы Microsoft"
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
- AMO, classes
- Analysis Management Objects, classes
- objects [Analysis Management Objects]
- AMO, objects
- classes [AMO]
- AMO
- Analysis Management Objects
- Analysis Management Objects, objects
ms.assetid: 3b0cdf8e-46d5-4dfe-8b2c-233c27e1473e
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 5fb57ba499669e09d177892eb861ad8994819e85
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2018
---
# <a name="amo-concepts-and-object-model"></a>Основные понятия и модель объектов AMO
  Этот раздел содержит определения для анализа Management объекты AMO, как они связаны с другими средствами и библиотеками из архитектуры [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]и общие сведения обо всех основных объектах AMO.  
  
 Объекты AMO являются полной коллекцией классов управления для служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], доступных для использования программным способом в управляемой среде, через пространство имен <xref:Microsoft.AnalysisServices>. Эти классы включены в файл AnalysisServices.dll, который обычно находится [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] программа установки устанавливает файлы в папке \100\SDK\Assemblies\\. Для работы с классами AMO укажите в своем проекте ссылку на эту сборку.  
  
 С помощью объектов AMO, можно создавать, изменять и удалять объекты, такие как кубы, измерения, структуры интеллектуального анализа данных и [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] баз данных, со всеми этими объектами, действия могут выполняться из приложения в .NET Framework. Кроме этого, существует также возможность обновления и обработки данных, хранящихся в базах данных служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
 Объекты AMO не позволяют выполнять запросы к данным. Чтобы запрашивать данные, используйте [разработка с использованием ADOMD.NET](../../../analysis-services/multidimensional-models/adomd-net/developing-with-adomd-net.md).  
  
 Этот раздел состоит из следующих подразделов.  
  
 [Объекты AMO в архитектуре служб анализа](#AMOintheAnalysisServicesArchitecture)  
  
 [Архитектура объектов AMO](#AMOArchitecture)  
  
 [С помощью объектов AMO](#bkmk_UsingAMO)  
  
 [Автоматизация административных задач с помощью объектов AMO](#AutomatingAdministrativeTaskswithAMO)  
  
##  <a name="AMOintheAnalysisServicesArchitecture">Объекты AMO в архитектуре служб анализа</a>  
 Объекты AMO предназначены только для управления объектами, а не для выполнения запросов к данным. Если пользователю требуется запрос [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] данных из клиентского приложения, которые должны использовать клиентское приложение [разработка с использованием ADOMD.NET](../../../analysis-services/multidimensional-models/adomd-net/developing-with-adomd-net.md).  
  
##  <a name="AMOArchitecture">Архитектура объектов AMO</a>  
 Объекты AMO — это полная библиотека классов, предназначенных для управления экземпляром [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] из клиентского приложения в управляемом коде на платформе .NET Framework версии 2.0.  
  
 Библиотека классов AMO содержит иерархию классов, где для использования в коде сначала создаются экземпляры одних классов, а затем других. Существуют также дополнительные классы, экземпляры которых могут быть в любой момент созданы в коде, однако сначала, вероятно, потребуется создать экземпляры одного или нескольких классов иерархии.  
  
 Приведенная ниже иллюстрация является представлением иерархии AMO высокого уровня, содержащей основные классы. На иллюстрации показано размещение классов среди контейнеров и одноранговых узлов. Объект <xref:Microsoft.AnalysisServices.Dimension> принадлежит объекту <xref:Microsoft.AnalysisServices.Database> и объекту <xref:Microsoft.AnalysisServices.Server> и может быть создан одновременно с объектами <xref:Microsoft.AnalysisServices.DataSource> и <xref:Microsoft.AnalysisServices.MiningStructure>. Необходимо создать экземпляры некоторых одноранговых узлов перед тем, как можно будет пользоваться остальными. Например, перед добавлением нового объекта <xref:Microsoft.AnalysisServices.DataSource> или <xref:Microsoft.AnalysisServices.Dimension> должен быть создан экземпляр объекта <xref:Microsoft.AnalysisServices.MiningStructure>.  
  
 ![Высокоуровневое представление классов AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/media/amo-highlevelview-majorobjectshighlighted.gif "высокоуровневое представление классов AMO")  
  
 Объект *основной объект* — это класс, который представляет полный объект как единую сущность, а не как часть другого объекта. Основными являются объекты <xref:Microsoft.AnalysisServices.Server>, <xref:Microsoft.AnalysisServices.Cube>, <xref:Microsoft.AnalysisServices.Dimension> и <xref:Microsoft.AnalysisServices.MiningStructure> (поскольку являются самостоятельными сущностями). А вот объект <xref:Microsoft.AnalysisServices.Level> не является основным, поскольку является составной частью объекта <xref:Microsoft.AnalysisServices.Dimension>. Основные объекты можно создавать, удалять, изменять или обрабатывать, независимо от других объектов. Второстепенными называются объекты, которые могут быть созданы только в рамках создания родительского основного объекта. Обычно второстепенные объекты создаются после создания основного объекта. Значения для второстепенных объектов следует задавать во время создания, поскольку значения по умолчанию для них не существуют.  
  
 На следующей иллюстрации показаны основные объекты, содержащиеся в объекте <xref:Microsoft.AnalysisServices.Server>.  
  
 ![Главные объекты AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/media/amo-majorobjects.gif "Главные объекты AMO")  
  
 ![Главные объекты AMO выделяются (2)](../../../analysis-services/multidimensional-models/analysis-management-objects/media/amo-majorobjects-02.gif "Главные объекты AMO выделяются (2)")  
  
 При программировании с помощью объектов AMO в ассоциации между классами и содержащимися в них классами используются атрибуты типа коллекции, например <xref:Microsoft.AnalysisServices.Server> и <xref:Microsoft.AnalysisServices.Dimension>. Для работы со вложенным экземпляром класса необходимо сначала получить ссылку на объект коллекции, в которой он содержится или может содержаться. Затем в коллекции необходимо найти нужный объект и получить ссылку на него, чтобы начать с ним работу.  
  
### <a name="amo-classes"></a>Классы AMO  
 Объекты AMO — это библиотека классов, предназначенных для управления экземпляром служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] из клиентского приложения. Библиотеку объектов AMO можно описать как логически связанные группы объектов, используемых для выполнения определенной задачи. Классы AMO можно разбить на категории следующим образом.  
  
|Набор классов|Назначение|  
|---------------|-------------|  
|[Основные классы объектов AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-fundamental-classes.md)|Классы, необходимые для работы с любым другим набором классов.|  
|[Классы OLAP объектов AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-olap-classes.md)|Классы для управления объектами OLAP в службах [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Классы интеллектуального анализа данных объектов AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-data-mining-classes.md)|Классы для управления объектами интеллектуального анализа данных в службах [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Классы безопасности объектов AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-security-classes.md)|Классы для управления доступом к другим объектам и поддержки безопасности.|  
|[Другие классы и методы объектов AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-other-classes-and-methods.md)|Классы и методы, помогающие администраторам OLAP и интеллектуального анализа данных выполнять свои повседневные задачи.|  
  
##  <a name="bkmk_UsingAMO">С помощью объектов AMO</a>  
 Объекты AMO особенно полезны для автоматизации часто выполняемых задач (например, для создания новых секций в группе мер при появлении новых данных в таблице фактов или для повторного обучения модели интеллектуального анализа при появлении новых данных). Обычно эти задачи, которые создают новые объекты, выполняются ежемесячно, еженедельно или ежеквартально, а приложение может легко именовать эти новые объекты на основе новых данных.  
  
##### <a name="analysis-services-administrators"></a>Администраторы служб Analysis Services  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Администраторы могут использовать объекты AMO для автоматизации обработки [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] баз данных. Проектирование и развертывание баз данных служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] следует производить в среде [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].  
  
##### <a name="developers"></a>Разработчики  
 Разработчикам объекты AMO дают возможность создавать интерфейсы администрирования для определенных наборов пользователей. Эти интерфейсы позволяют ограничивать доступ к объектам служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] и разрешать пользователям выполнять только определенные задачи. На основе объектов AMO можно, например, создать приложение для создания резервных копий, которое позволит пользователям видеть все объекты баз данных, выбрать любую из баз данных и создать ее резервную копию на любом устройстве из указанного набора.  
  
 Разработчики могут также внедрять в приложения логику служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Это возможно благодаря созданию кубов, измерений, структур и моделей интеллектуального анализа на основе пользовательского ввода и других факторов.  
  
##### <a name="olap-advanced-users"></a>Опытные пользователи OLAP  
 Опытными пользователями OLAP обычно являются специалисты по анализу данных и другие опытные пользователи баз данных, обладающие обширными знаниями в программировании, которые хотят повысить качество анализа данных за счет более глубокого использования объектов данных. Пользователям, которым необходимо работать в режиме «вне сети», объекты AMO могут пригодиться для автоматизации создания локальных кубов перед переходом в режим «вне сети».  
  
##### <a name="data-mining-advanced-users"></a>Опытные пользователи интеллектуального анализа данных  
 Для опытных пользователей интеллектуального анализа данных объекты AMO наиболее полезны в тех случаях, когда необходимо периодически переобучать большие наборы моделей.  
  
##  <a name="AutomatingAdministrativeTaskswithAMO">Автоматизация административных задач с помощью объектов AMO</a>  
 Проектирование, развертывание и обслуживание большинства наиболее часто выполняемых задач лучше всего выполняется при помощи приложений на основе служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], написанных на любом языке. А для тех повторяющихся задач, автоматизировать которые при помощи служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] невозможно, можно использовать объекты AMO. Объекты AMO также полезны при разработке специализированных приложений для бизнес-аналитики на основе служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
##### <a name="automatic-object-management"></a>Автоматическое управление объектами  
 Объекты AMO обеспечивают простоту создания, обновления и удаления объектов служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] (например, <xref:Microsoft.AnalysisServices.Database>, <xref:Microsoft.AnalysisServices.Dimension>, <xref:Microsoft.AnalysisServices.Cube>, <xref:Microsoft.AnalysisServices.MiningStructure>, <xref:Microsoft.AnalysisServices.MiningModel> или <xref:Microsoft.AnalysisServices.Role>) на основе пользовательского ввода или новых данных. Объекты AMO идеально подходят для приложений установки, целью которых является развертывание разработанного решения (от независимого поставщика программного обеспечения до конечного потребителя). Приложение может проверить наличие предыдущей версии и обновить структуру, удалить устаревшие объекты и создать новые. При отсутствии предыдущей версии приложение может создать установку с нуля.  
  
 Объекты AMO позволяют создавать новые секции на основе новых данных и удалять старые секции, которые вышли за пределы области действия проекта. Например, в решении для финансового анализа, которое работает с данными за 36 месяцев, после получения данных за новый месяц все данные за старый тридцать седьмой месяц можно удалить. Для оптимизации производительности можно спроектировать новые агрегаты на основе использования и применить их к последним 12 месяцам.  
  
##### <a name="automatic-object-processing"></a>Автоматическая обработка объектов  
 Объекты AMO обеспечивают автоматическую обработку и обновление объектов в ответ на определенные события, возникшие за пределами обычного потока данных, а также из запланированных задач, использующих службы [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].  
  
##### <a name="automatic-security-management"></a>Автоматическое управление безопасностью  
 Автоматизация управления безопасностью подразумевает включение в роли новых пользователей и разрешений, а также удаление из них пользователей по истечении срока действия. Возможность создания новых интерфейсов позволяет упростить управление безопасностью для администраторов безопасности. Решение этой задачи может оказаться даже проще, чем в среде [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].  
  
##### <a name="automatic-backup-management"></a>Управление автоматическим созданием резервных копий  
 Управление автоматическим созданием резервных копий осуществляется либо при помощи задач служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], либо путем создания специальных приложений AMO, запускающихся автоматически. Объекты AMO дают возможность разрабатывать интерфейсы резервного копирования для операторов, чтобы помочь им в выполнении ежедневных задач.  
  
##### <a name="tasks-amo-is-not-intended-for"></a>Задачи, для которых объекты AMO не предназначены  
 Объекты AMO не могут быть использованы для выполнения запросов к данным. Запросы к данным служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], в том числе кубам и моделям интеллектуального анализа данных, из пользовательского приложения необходимо выполнять с помощью ADOMD.NET. Дополнительные сведения см. в разделе [разработка с использованием ADOMD.NET](../../../analysis-services/multidimensional-models/adomd-net/developing-with-adomd-net.md).  
  
  
