---
title: "Внедрение изображения в отчет (построитель отчетов и службы SSRS) | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: report-design
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.rtp.rptdesigner.embeddedimages.f1
- "10060"
ms.assetid: aed77345-5eeb-41f0-96c9-db6b4a11ec6f
caps.latest.revision: "8"
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 79f6ff70c869da699a7505bdbe5b4b1490e9eb23
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/09/2018
---
# <a name="embed-an-image-in-a-report-report-builder-and-ssrs"></a>Внедрение изображения в отчет (построитель отчетов и службы SSRS)
  Отчет может содержать внедренное изображение. Внедрение изображения гарантирует постоянную доступность изображения для отчета, однако увеличивает размер определения отчета (файла, который определяет отчет). Изображения, внедренные в отчет, перечислены на панель данных отчета.  
  
 Может возникнуть необходимость внедрить изображение в определение отчета перед добавлением изображения в область конструктора. Дополнительные сведения см. в разделе [Добавление фонового изображения (построитель отчетов и службы SSRS)](../../reporting-services/report-design/add-a-background-image-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-embed-an-image-in-a-report"></a>Внедрение изображения в отчет  
  
1.  В режиме конструктора отчетов нажмите на вкладке **Вставка** кнопку **Изображение**.  
  
2.  В области конструктора щелкните и перетащите рамку, чтобы получилось изображение нужного размера.  
  
3.  На странице **Общие** диалогового окна **Свойства изображения** введите имя в текстовое поле **Имя** или примите имя по умолчанию.  
  
4.  В текстовом поле **Подсказка** введите текст, который будет появляться при наведении курсора на изображение в отчете, готовом для просмотра (необязательно).  
  
5.  В списке **Выберите источник изображения**выберите **Внедренный**.  
  
6.  Нажмите кнопку **Импортировать** рядом с текстовым полем **Использовать это изображение** .  
  
7.  В поле **Файлы типа**выберите тип файлов изображения, перейдите к файлу и нажмите кнопку **Открыть**.  
  
8.  В диалоговом окне **Свойства изображения** нажмите кнопку **ОК**.  
  
     Изображение отображается в рамке, перетащенной в область конструктора, а файл — в папке «Изображения» в области данных отчета.  
  
    > [!NOTE]  
    >  Кроме того, при импорте изображения автоматически извлекается тип MIME (например, BMP). Чтобы изменить тип MIME, см. следующую процедуру.  
  
### <a name="optional-to-change-the-mime-type-of-an-imported-image"></a>Изменение типа MIME импортированного изображения (необязательно)  
  
1.  Откройте отчет в режиме конструктора.  
  
2.  Выберите изображение в области конструктора. В панели **Свойства** отображаются свойства изображения.  
  
    > [!NOTE]  
    >  Если панель "Свойства" не отображается, на вкладке **Вид** выберите пункт **Свойства**.  
  
3.  Щелкните текстовое поле рядом со свойством **MIMEType** и выберите из раскрывающегося списка новый тип MIME.  
  
## <a name="see-also"></a>См. также:  
 [Изображения (построитель отчетов и службы SSRS)](../../reporting-services/report-design/images-report-builder-and-ssrs.md)   
 [Добавление привязанного к данным изображения (построитель отчетов и службы SSRS)](../../reporting-services/report-design/add-a-data-bound-image-report-builder-and-ssrs.md)   
 [Диалоговое окно "Свойства изображения" — "Общие" (построитель отчетов и службы SSRS)](http://msdn.microsoft.com/library/c2218b93-f7fe-46ef-995f-d7dadf9752ec)  
  
  
