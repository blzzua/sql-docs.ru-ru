---
title: "Создание и управление секциями табличной модели | Документы Microsoft"
ms.custom: 
ms.date: 02/22/2018
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dab72cf0-95bc-4b63-95dc-505b5cd881c1
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 1dfe0ae7dd1ee92cd365a34cf6502d8358c474cb
ms.sourcegitcommit: d8ab09ad99e9ec30875076acee2ed303d61049b7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/23/2018
---
# <a name="create-and-manage-tabular-model-partitions"></a>Создание и управление секциями табличной модели
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]

  Секции разделяют таблицу на логические части. Каждая секция затем может обрабатываться (обновляться) независимо от других секций. Секции, определенные для модели во время разработки модели, дублируются в модели развертывания. После развертывания можно настроить управление секциями с помощью диалогового окна **Секции** в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или с помощью скрипта. В задачах этого раздела описывается создание и управление секциями в развернутой модели.  
  
  > [!NOTE]  
>  Секции в табличных моделей, созданных на уровне совместимости 1400 определяются с помощью инструкции запроса M. Дополнительные сведения см. в разделе [ссылка M](https://msdn.microsoft.com/library/mt211003.aspx). 
>
  
## <a name="tasks"></a>Задания  
 Создание секций и управление ими в развернутой базе данных с табличной моделью выполняются в диалоговом окне **Секции** среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Чтобы открыть диалоговое окно **Секции** в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], щелкните таблицу правой кнопкой мыши и выберите команду **Секции**.  
  
###  <a name="bkmk_create_new"></a> Создание новой секции  
  
1.  В диалоговом окне **Секции** нажмите кнопку **Создать** .  
  
2.  В поле **Имя секции**введите имя секции. По умолчанию к имени секции, заданной по умолчанию, будет добавляться номер, постепенно увеличивающийся для каждой новой секции.  
  
3.  В **инструкция запроса**введите или вставьте инструкцию запроса SQL или M, который определяет столбцы и любые предложения, которые требуется включить в секцию в окно запроса.  
  
4.  Чтобы проверить инструкцию, нажмите кнопку **Проверить синтаксис**.  
  
###  <a name="bkmk_copy"></a> Копирование секции  
  
1.  В диалоговом окне **Секции** в списке **Секции** выберите секцию, которую необходимо скопировать, и нажмите кнопку **Копировать** .  
  
2.  В поле **Имя секции**введите новое имя секции.  
  
3.  В **инструкция запроса**, изменить инструкцию запроса.  
  
###  <a name="bkmk_merge"></a> Объединение двух или более разделов  
  
-   В диалоговом окне **Секции** в списке **Секции** выберите щелчками мыши при нажатой клавише CTRL секции, которые необходимо объединить, и нажмите кнопку **Объединить** .  
  
> [!IMPORTANT]  
>  Слияние секций не обновляет их метаданные. Необходимо изменить инструкцию SQL или M для получающейся в результате секции, чтобы убедиться в том, что операции обработки обрабатывают все данных в объединенной секции.  
  
###  <a name="bkmk_delete"></a> Удаление секции  
  
-   В диалоговом окне **Секции** в списке **Секции** выберите секцию, которую необходимо удалить, и нажмите кнопку **Удалить** .  
  
## <a name="see-also"></a>См. также:  
 [Секции табличных моделей](../../analysis-services/tabular-models/tabular-model-partitions-ssas-tabular.md)   
 [Секций процесса табличной модели](../../analysis-services/tabular-models/process-tabular-model-partitions-ssas-tabular.md)  
  
  
