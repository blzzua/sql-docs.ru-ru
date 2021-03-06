---
title: Мастер формирования схем (службы Analysis Services) | Документы Microsoft
ms.custom: ''
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- relational schema [Analysis Services]
ms.assetid: 68bf7ba3-d0cb-437f-9a3e-9edc0999af19
caps.latest.revision: 16
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 92996e941d5ac3a96bf684ef499f9de663df0a24
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="schema-generation-wizard-analysis-services"></a>Мастер формирования схем (службы Analysis Services)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)][!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] поддерживает два метода работы с реляционными схемами при определении объектов OLAP в пределах [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] проекте или базе данных. В целом, определение объектов OLAP основано на модели логических данных, созданной в представлении источника данных в проекте или базе данных [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Такое представление источника данных определяется на основе элементов схемы одного или более источников реляционных данных в соответствии с настройками представления источников данных.  
  
 Можно также сначала определять объекты OLAP, а затем генерировать представление источника данных, источник данных и базовую схему реляционной базы данных, поддерживающую эти объекты OLAP. Эта реляционная база данных называется базой данных предметной области.  
  
 Такой подход иногда называют нисходящим и часто используют для создания прототипов и аналитического моделирования. В этом случае воспользуйтесь мастером создания схем для создания базового представления источников данных и объектов источника данных на основе объектов OLAP, определенных в проекте или базе данных [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
 Это итеративный подход. Мастер, скорее всего, придется запустить несколько раз для изменения проекта размерностей и кубов. При каждом запуске мастер объединяет изменения в основных объектах и, насколько возможно, сохраняет данные, содержащиеся в основных базах данных.  
  
 Создаваемая схема — это схема ядра реляционной базы данных SQL Server. Мастер не создает схемы для других продуктов реляционной базы данных.  
  
 Данные, вставляемые в предметную область, добавляются отдельно с помощью любых средств и методов, обычно используемых для заполнения реляционной базы данных SQL Server. В большинстве случаев данные сохраняются при повторном запуске мастера, однако существуют исключения. Например, некоторые данные будут сброшены при удалении измерения или атрибута, содержащего эти данные. Если мастер формирования схем сбрасывает некоторые данные при изменении схемы, то выдается запрос на подтверждение сброса данных и можно отменить процесс повторного формирования.  
  
 В качестве общего правила любые изменения объекта, изначально созданного мастером формирования схем, перезаписываются при последующем повторном формировании объекта мастером формирования схем. Первичным исключением из этого правила является добавление столбцов к таблице, созданной мастером формирования схем. В этом случае мастер формирования схем сохраняет добавленные к таблице столбцы, а также данные в этих столбцах.  
  
## <a name="in-this-section"></a>В этом разделе  
 В следующей таблице приводятся дополнительные темы, объясняющие принципы работы с мастером формирования схем.  
  
|Раздел|Description|  
|-----------|-----------------|  
|[Использование мастера формирования схем (службы Analysis Services)](../../analysis-services/multidimensional-models/use-the-schema-generation-wizard-analysis-services.md)|Содержит описание формирования схемы для баз данных предметной области и промежуточной области хранения.|  
|[Основные сведения о схемах баз данных](../../analysis-services/multidimensional-models/understanding-the-database-schemas.md)|Содержит описание схемы, формируемой для баз данных предметной области и промежуточной области.|  
|[Основные сведения о добавочном создании](../../analysis-services/multidimensional-models/understanding-incremental-generation.md)|Содержит описание возможностей постепенного создания мастера формирования схем.|  
  
## <a name="see-also"></a>См. также:  
 [Представления источников данных в многомерных моделях](../../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md)   
 [Источники данных в многомерных моделях](../../analysis-services/multidimensional-models/data-sources-in-multidimensional-models.md)   
 [Поддерживаемые источники данных (службы SSAS — многомерные базы данных)](../../analysis-services/multidimensional-models/supported-data-sources-ssas-multidimensional.md)  
  
  
