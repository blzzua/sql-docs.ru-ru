---
title: "Командлет Update-PowerPivotSystemService | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a90f1158-68d3-4330-98c1-fb0f81e13328
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 045979085e6d8e1622fef2a961f6c9fdb21d772a
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2018
---
# <a name="update-powerpivotsystemservice-cmdlet"></a>Командлет «Update-PowerPivotSystemService»
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
Обновляет родительский объект системной службы [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] в ферме.  

>[!NOTE] 
>В этой статье может содержать устаревшие сведения и примеры. С помощью командлета Get-Help для последней версии.
  
 **Применимо для следующих объектов:** SharePoint 2010 и SharePoint 2013.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Update-PowerPivotSystemService [-Confirm <switch>] [<CommonParameters>]  
```  
  
## <a name="description"></a>Описание  
 Командлет **Update-PowerPivotSystemService** выполняет ряд операций обновления применительно к родительскому объекту системной службы [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , экземплярам и приложениям службы [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] в ферме. Все службы и приложения среднего уровня в развертывании [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint должны работать на одном функциональном уровне. Этот командлет выполняет действия обновления для всех таких объектов.  
  
 Запустите этот командлет после выполнения программы установки SQL Server для установки новой версии [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint или применения накопительного обновления к серверу. Для проверки того, была ли операция обновления успешной, выполните `Get-PowerPivotSystemService` для определения значения свойства **NeedsUpgrade** . Если свойство **NeedsUpgrade** имеет значение true, необходимо выполнить указанный командлет для обновления объектов [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] промежуточного уровня в ферме.  
  
 Развертывание [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint включает службы данных промежуточного уровня и уровня сервера, поэтому необходимо выполнять командлет **Update-PowerPivotEngineService** каждый раз после выполнения командлета **Update-PowerPivotSystemService** , чтобы гарантировать использование одной и той же версии на обоих уровнях в ферме.  
  
 Обновление не может быть отменено до предыдущей версии. Если требуется вернуться к предыдущей версии, удалите [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] из фермы SharePoint и установите заново. Для проверки того, была ли операция обновления успешной, выполните `Get-PowerPivotSystemService` для определения глобальных свойств, относящихся к информации о версии, и проверки того, что свойство **NeedsUpgrade** больше не имеет значение true.  
  
## <a name="parameters"></a>Параметры  
  
### <a name="-confirm-switch"></a>-Подтверждение \<переключения >  
 Выводит приглашение для подтверждения перед выполнением команды. Это значение включено по умолчанию. Чтобы исключить подтверждения в команде, укажите параметр Confirm:$ false.  
  
|||  
|-|-|  
|Обязательно?|false|  
|Позиция?|именованный|  
|Значение по умолчанию||  
|Принимать входные данные конвейера?|false|  
|Принимать символы-шаблоны?|false|  
  
### <a name="commonparameters"></a>\<Общие параметры >  
 Этот командлет поддерживает следующие параметры:  
  
-   Подробный  
  
-   Отладка  
  
-   ErrorAction  
  
-   ErrorVariable  
  
-   WarningAction  
  
-   WarningVariable  
  
-   OutBuffer  
  
-   OutVariable  
  
 Дополнительные сведения см. в разделе [Об общих параметрах](http://go.microsoft.com/fwlink/?linkID=227825).  
  
## <a name="inputs-and-outputs"></a>Входы и выходы  
 Входной тип — это тип объектов, которые можно направить в командлет. Тип возвращаемого значения — это тип объектов, возвращаемых командлетом.  
  
|||  
|-|-|  
|Входные данные|Нет.|  
|Выходные данные|Нет.|  
  
  
