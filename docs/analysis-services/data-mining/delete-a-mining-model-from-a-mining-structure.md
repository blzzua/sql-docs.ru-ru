---
title: "Удалить модель интеллектуального анализа данных из структуры интеллектуального анализа данных | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
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
- mining structures [Analysis Services], mining models
- deleting mining models
- removing mining models
- mining models [Analysis Services], deleting
ms.assetid: 9ab1506b-856e-4762-a663-5adf15ac71e3
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 363ac575844136dee04f9cf249253479e64836dd
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2018
---
# <a name="delete-a-mining-model-from-a-mining-structure"></a>удалить модель интеллектуального анализа данных из структуры интеллектуального анализа данных
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
Модели интеллектуального анализа данных можно удалять в конструкторе интеллектуального анализа данных с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]или инструкций расширений интеллектуального анализа данных.  
  
### <a name="delete-a-mining-model-using-sql-server-data-tools"></a>Удаление модели интеллектуального анализа данных с помощью SQL Server Data Tools  
  
1.  Перейдите на вкладку **Модели интеллектуального анализа данных** в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
2.  Щелкните правой кнопкой мыши модель, которую необходимо удалить, и выберите пункт **Удалить**.  
  
     Откроется диалоговое окно **Удаление объектов** .  
  
3.  Нажмите кнопку **ОК**.  
  
### <a name="delete-a-mining-model-using-sql-server-management-studio"></a>Удаление модели интеллектуального анализа данных с помощью среды SQL Server Management Studio  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]откройте базу данных [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , содержащую модель.  
  
2.  Разверните **Структуры интеллектуального анализа данных**, затем **Модели интеллектуального анализа данных**.  
  
3.  Щелкните правой кнопкой мыши модель, которую необходимо удалить, и выберите пункт **Удалить**.  
  
     Удаление модели не приводит к удалению обучающих данных. Удаляются только метаданные и шаблоны, созданные при обучении модели.  
  
### <a name="delete-a-mining-model-using-dmx"></a>Удаление модели интеллектуального анализа данных с помощью расширений интеллектуального анализа данных  
  
-   [УДАЛЕНИЕ МОДЕЛИ ИНТЕЛЛЕКТУАЛЬНОГО АНАЛИЗА ДАННЫХ &#40; РАСШИРЕНИЙ ИНТЕЛЛЕКТУАЛЬНОГО АНАЛИЗА ДАННЫХ &#41;](../../dmx/drop-mining-model-dmx.md)  
  
## <a name="see-also"></a>См. также  
 [Задачи модели интеллектуального анализа данных и инструкции](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)  
  
  
