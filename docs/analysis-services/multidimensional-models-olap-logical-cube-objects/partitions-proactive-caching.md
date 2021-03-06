---
title: "Упреждающее кэширование (секции) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
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
- hybrid OLAP
- partitions [Analysis Services], proactive caching
- relational OLAP
- multidimensional OLAP
- MOLAP
- proactive caching [Analysis Services]
- ROLAP
- cache [Analysis Services]
ms.assetid: 422660b2-4d80-4165-b1c9-3963bcde556b
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 25a6306e19f6eff72f84fffde0372ed0bc3d76e6
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2018
---
# <a name="partitions---proactive-caching"></a>Секции — упреждающее кэширование
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
Упреждающее кэширование позволяет автоматически создавать кэш MOLAP для объектов OLAP, а также управлять им. Кубы мгновенно реагируют на изменения, которые происходят с данными из базы данных, благодаря уведомлениям, получаемым от базы данных. Цель упреждающего кэширования — совмещение производительности, характерной для традиционного MOLAP, со скоростью и простотой управления ROLAP.  
  
 Простой объект <xref:Microsoft.AnalysisServices.ProactiveCaching> содержит спецификации времени и уведомления таблиц. Спецификация времени определяет временной промежуток, за который кэш обновляется после получения уведомления об изменении. В уведомлении таблиц определяется схема обмена уведомлениями между таблицей данных и объектом <xref:Microsoft.AnalysisServices.ProactiveCaching>.  
  
 Хранилище многомерного OLAP (MOLAP) обеспечивает наилучшее время отклика запросов, но с некоторой задержкой данных. Хранилище реляционного OLAP (ROLAP), функционирующее в режиме реального времени, позволяет пользователям немедленно просматривать самые последние изменения в источнике данных, но с гораздо меньшей производительностью, чем хранилище многомерного OLAP (MOLAP), в связи с отсутствием предварительно рассчитанных сводок данных и в связи с тем, что реляционное хранилище не оптимизировано для запросов типа OLAP. При наличии приложений пользователям, которым необходимо видеть последние данные и при необходимости использовать преимущества производительности хранилища MOLAP, службы SQL Server Analysis Services предоставляют возможность упреждающего кэширования для удовлетворения потребностей этого сценария, в особенности в сочетании с использованием секций. Упреждающее кэширование устанавливается на базе секции и измерения. Параметры упреждающего кэширования могут обеспечить баланс между повышенной производительностью хранилища MOLAP и оперативностью данных хранилища ROLAP, а также обеспечить автоматическую обработку секций при изменении базовых данных или по расписанию.  
  
## <a name="proactive-caching-configuration-options"></a>Параметры настройки упреждающего кэширования  
 Службы SQL Server Analysis Services предоставляют несколько параметров конфигурации упреждающего кэширования, позволяющих добиться максимальной производительности и минимальной задержки, а также создать план обработки. Функции упреждающего кэширования упрощают процесс управления устареванием данных. Настройки упреждающего кэширования определяют, насколько часто осуществляется перестроение многомерной структуры OLAP, называемой также кэшем MOLAP, отправляются ли запросы при перестроении кэша к устаревшему хранилищу MOLAP или к базовому источнику данных ROLAP и осуществляется ли перестроение кэша по расписанию или на основе изменений в базе данных.  
  
### <a name="minimizing-latency"></a>Минимизация задержки  
 При настройке упреждающего кэширования для минимизации задержки запросы пользователя к объекту OLAP выполняются к хранилищу ROLAP или к хранилищу MOLAP, в зависимости от того, вносились ли в последнее время изменения в данные, и как настроено упреждающее кэширование. Ядро запросов направляет запросы к данным источника в хранилище MOLAP до внесения изменений в источник данных. Для минимизации задержки после внесения изменений в источник данных кэшированные объекты MOLAP могут удаляться, и выполнение запросов переключается на хранилище ROLAP, в то время как объекты MOLAP перестраиваются в кэше. После перестроения и обработки объектов MOLAP запросы автоматически переключаются на хранилище MOLAP. Обновление кэша может выполняться чрезвычайно быстро для небольших секций, например для текущей секции, которая может быть размером, соответствующему текущему дню.  
  
### <a name="maximizing-performance"></a>Максимизация производительности  
 Для увеличения производительности при уменьшении задержек кэширование может также использоваться без удаления объектов текущего хранилища MOLAP. После этого запросы отправляются к объектам MOLAP, в то время как данные считываются и обрабатываются в новом кэше. Этот метод обеспечивает лучшую производительность, но может привести к тому, что запросы возвращают старые данные во время перестроения нового кэша.  
  
## <a name="see-also"></a>См. также  
 [Хранение измерений](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimensions-storage.md)   
 [Настройка хранилища секций &#40; Службы Analysis Services — многомерные &#41;](../../analysis-services/multidimensional-models/set-partition-storage-analysis-services-multidimensional.md)  
  
  
