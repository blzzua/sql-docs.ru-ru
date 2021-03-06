---
title: "Занятие 9 Создание перспектив | Документы Microsoft"
ms.custom: 
ms.date: 03/27/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to: SQL Server 2016
ms.assetid: 55b0f0d0-1cdf-4876-9c3d-d0c848be3f5d
caps.latest.revision: "23"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 76fc2643bf8d160b38dbcc1009ad37926051407c
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="lesson-8-create-perspectives"></a>Занятие 8. Создание перспектив
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

На этом занятии будет создана перспектива «Продажи через Интернет». Перспектива определяет просматриваемое подмножество модели, реализующее точки наблюдения, которые сосредоточены на определенном аспекте бизнеса либо предназначены для использования в конкретном приложении. Когда пользователь подключается к модели с помощью перспективы, они видят только те объекты модели (таблицы, столбцы, меры, иерархии и ключевые показатели эффективности) как поля, определенные в перспективе.  
  
Перспективы Internet Sales, создаваемая на этом занятии, исключает объект таблицы DimCustomer. При создании перспективы, которая исключает из представления определенные объекты, такие объекты продолжают существовать в модели, однако они не видны в списке полей клиентского средства создания отчетов. Вычисляемые столбцы и меры, как входящие в перспективу, так и нет, все равно смогут проводить вычисления с использованием данных из исключенного объекта.  
  
Цель этого занятия — описать создание перспектив и ознакомиться со средствами разработки табличных моделей. Если потом развернуть эту модель и включить дополнительные таблицы, можно создать дополнительные перспективы для определения разных точек обзора модели, например, инвентаризации и продажи. Дополнительные сведения см. в разделе [Перспективы](../analysis-services/tabular-models/perspectives-ssas-tabular.md).  
  
Предполагаемое время выполнения этого занятия: **5 минут**.  
  
## <a name="prerequisites"></a>предварительные требования  
Этот раздел является частью учебника по табличному моделированию, который необходимо изучать по порядку. Перед выполнением задач этого занятия, необходимо завершить предыдущее занятие: [занятии 7: Создание ключевых показателей эффективности](../analysis-services/lesson-7-create-key-performance-indicators.md).  
  
## <a name="create-perspectives"></a>Создание перспектив  
  
#### <a name="to-create-an-internet-sales-perspective"></a>Создание перспективы «Продажи через Интернет»  
  
1.  Нажмите кнопку **модель** меню > **перспективы** > **Создание и управление**.  
  
2.  В диалоговом окне **Перспективы** щелкните **Создать перспективу**.  
  
3.  Дважды щелкните **новую перспективу** заголовок столбца и переименовать **продажи через Интернет**.  
  
4.  Выберите все таблицы *за исключением* **DimCustomer**.  
  
    ![как табличных lesson8-перспектив](../analysis-services/media/as-tabular-lesson8-perspectives.png)
  
    В одном из следующих занятий будет использовать функции анализа в Excel для проверки этой перспективы. Список полей сводной таблицы Excel будет содержать все таблицы, за исключением того, в таблице DimCustomer.  

## <a name="whats-next"></a>Дальнейшие действия
Перейдите к следующему занятию: [занятии 9: создание иерархий](../analysis-services/lesson-9-create-hierarchies.md).
  
  
  
  
