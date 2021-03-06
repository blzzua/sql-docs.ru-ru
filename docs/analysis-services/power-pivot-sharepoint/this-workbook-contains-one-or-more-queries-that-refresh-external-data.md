---
title: "Эта книга содержит один или несколько запросов на обновление внешних данных | Документы Microsoft"
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
ms.assetid: aa65c992-eb41-4032-9e11-a9ba871b6a3c
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 354c8c0baca1372c0bc6cb17e2acbfc74c45b9b4
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2018
---
# <a name="this-workbook-contains-one-or-more-queries-that-refresh-external-data"></a>Эта книга содержит один или несколько запросов на обновление внешних данных
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
Для книг Excel, содержащих данные [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , службы Excel Services отображают это предупреждение при обнаружении сведений о подключении и предлагают включить или отключить запросы для этой книги.  
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] для SharePoint|  
|Номер версии продукта|[!INCLUDE[ssKilimanjaro_md](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11_md](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14_md](../../includes/sssql14-md.md)]|  
|Причина|Службы Excel настроены на предупреждение об обновлении данных.|  
|Текст сообщения|Эта книга содержит один или несколько запросов на обновление внешних данных. Злоумышленник может создать запрос для доступа к конфиденциальным сведениям и распространения их среди других пользователей или для выполнения других вредоносных действий.<br /><br /> Если вы доверяете источнику этой книги, нажмите кнопку «Да», чтобы разрешить в этой книге запросы к внешним данным. Если вы не уверены, нажмите кнопку «Нет», чтобы изменения к рабочей книге не применялись.<br /><br /> Разрешить в этой книге запросы к внешним данным?|  
  
## <a name="explanation"></a>Объяснение  
 [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] содержат строки подключения к внедренным данным, используемые Excel для обмена данными с внешним сервером [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)], который загружает и вычисляет данные. Если включены предупреждения об обновлении данных, службы Excel обнаруживают эту строку соединения и предупреждают пользователя.  
  
 Для фильтрации и создания срезов данных [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] в книге должны быть включены запросы. Убедитесь, что запросы включены только для доверенных книг [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] .  
  
## <a name="user-action"></a>Действие пользователя  
 Чтобы включить запросы, нажмите кнопку **Да** .  
  
 Также можно изменить параметры конфигурации, чтобы предупреждения об обновлениях больше не выдавались.  
  
1.  В разделе «Управление приложениями» центра администрирования выберите пункт **Управление приложениями служб**.  
  
2.  Щелкните **Приложение служб Excel**.  
  
3.  Щелкните **Надежные расположения файлов**.  
  
4.  Щелкните **http://** или расположение, которое требуется настроить.  
  
5.  В области "Внешние данные" снимите флажок **Предупреждать при обновлении данных**.  
  
6.  Нажмите кнопку **ОК**.  
  
 Или можно создать новое надежное местоположение для сайтов, содержащих книги [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] , а затем изменить параметры конфигурации только для этого сайта. Дополнительные сведения см. в разделе [Создание надежного расположения для сайтов PowerPivot в центре администрирования](../../analysis-services/power-pivot-sharepoint/create-a-trusted-location-for-power-pivot-sites-in-central-administration.md).  
  
  
