---
title: "Свойства хранилища файлов | Документы Microsoft"
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
ms.topic: reference
helpviewer_keywords:
- Income property
- InitialBonus property
- PercentScanPerPrice property
- FileStore properties
- BackgroundTrimCost property
- Tax property
- PerformanceTrace property
- MinimumBalance property
- UnbufferedThreshold property
- BackgroundTrimAmount property
- MaximumBalance property
- MemoryLimitMin property
- MemoryLimit property
ms.assetid: 580cf0aa-7425-4d48-aa8d-128f5b488fcd
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 24a18751c7686de2d3d3731806374fe7a6db2080
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2018
---
# <a name="filestore-properties"></a>свойства хранилища файлов
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] поддерживают свойства сервера хранилища файлов, перечисленные в следующих таблицах. Эти дополнительные свойства следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] . Дополнительные сведения о дополнительных свойствах сервера и их настройке см. в разделе [Свойства сервера в службах Analysis Services](../../analysis-services/server-properties/server-properties-in-analysis-services.md).  
  
 **Область применения:** многомерный и табличный режим сервера  
  
## <a name="properties"></a>Свойства  
 **MemoryLimit**  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **MemoryLimitMin**  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **PercentScanPerPrice**  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **PerformanceTrace**  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **RandomFileAccessMode**  
 Логическое свойство, которое указывает, происходит ли доступ к файлам базы данных и кэшированным файлам в режиме случайного доступа к файлам. По умолчанию это свойство отлючено. По умолчанию службы Analysis Services не установливают флаг случайного доступа к файлам, когда открывают файлы данных для чтения.  
  
 Случайный доступ к файлам может быть полезен в мощных системах, особенно в системах с большими объемами памяти и несколькими узлами NUMA. В режиме случайного доступа операционная система Windows обходит операции сопоставления страниц, которые считывают данные с диска в кэш файлов системы, снижая таким образом конфликты в кэше.  
  
 Следует выполнить сравнительные проверки для определения того, можно ли повысить производительность выполнения запросов в результате изменения этого свойства. Рекомендации по выполнению сравнительных проверок (включая способы очистки кэша и предотвращения распространенных ошибок) см. в [руководстве по использованию служб SQL Server 2008 R2 Analysis Services](http://go.microsoft.com/fwlink/?LinkID=225539). Дополнительные сведения о компромиссах в случае использования этого свойства см. в статье [http://support.microsoft.com/kb/2549369](http://support.microsoft.com/kb/2549369).  
  
 Чтобы просмотреть или изменить это свойство в среде Management Studio, необходимо включить список дополнительных свойств на странице свойств сервера. Изменить свойство можно также в файле msmdsrv.ini. После установки этого свойства рекомендуется перезапустить сервер; иначе доступ к уже открытым файлам будет продолжаться в прежнем режиме.  
  
 **UnbufferedThreshold**  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
## <a name="memory-model-category"></a>Категория модели памяти  
 **MemoryModel\Tax**  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **MemoryModel\Income**  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **MemoryModel\MaximumBalance**  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **MemoryModel\MinimumBalance**  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **MemoryModel\InitialBonus**  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
## <a name="see-also"></a>См. также  
 [Свойства сервера в службах Analysis Services](../../analysis-services/server-properties/server-properties-in-analysis-services.md)   
 [Определение режима работы сервера экземпляра служб Analysis Services](../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
