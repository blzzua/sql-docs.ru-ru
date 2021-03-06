---
title: "Определение хранимых процедур | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- stored procedures [Analysis Services]
- OLAP [Analysis Services], stored procedures
- external routines [Analysis Services]
- stored procedures [Analysis Services], about stored procedures
ms.assetid: f9c57d91-f60f-4f0e-8f7f-d87f4ba97b7c
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: af5d0ffc0b7aaa1b03ca4166d59667692566b036
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2018
---
# <a name="defining-stored-procedures"></a>Определение хранимых процедур
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
Хранимые процедуры можно использовать для вызова внешних подпрограмм из [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Для написания внешней подпрограммы, вызываемой хранимой процедурой, можно использовать любой язык среды CLR, например C, C++, C#, Visual Basic или Visual Basic .NET. Хранимую процедуру можно создать один раз и затем вызывать из множества контекстов, например из других хранимых процедур, вычисляемых мер или клиентских приложений. Хранимые процедуры упрощают разработку и реализацию базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] благодаря тому, что общий код создается один раз и сохраняется в одном месте. Хранимые процедуры можно использовать для расширения функциональности приложений за счет добавления дополнительных функций к собственной функциональности многомерных выражений.  
  
 В данном разделе приводятся сведения, необходимые для понимания, проектирования и реализации хранимых процедур.  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Конструирование хранимых процедур](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/designing-stored-procedures.md)|Содержит описание проектирования сборок для использования со службами [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|[Создание хранимых процедур](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/creating-stored-procedures.md)|Содержит описание создания сборок для служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|[Вызов хранимых процедур](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/calling-stored-procedures.md)|Предоставляет сведения об использовании сборок в службах [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|[Доступ к контексту запросов в хранимых процедурах](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/accessing-query-context-in-stored-procedures.md)|Содержит описание получения доступа к данным области и контекстным данным при помощи сборок.|  
|[Настройка безопасности для хранимых процедур](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/setting-security-for-stored-procedures.md)|Содержит описание настройки безопасности для сборок в службах [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|[Отладка хранимых процедур](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/debugging-stored-procedures.md)|Содержит описание отладки сборок в службах [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
  
## <a name="see-also"></a>См. также  
 [Управление сборками многомерной модели](../../analysis-services/multidimensional-models/multidimensional-model-assemblies-management.md)  
  
  
