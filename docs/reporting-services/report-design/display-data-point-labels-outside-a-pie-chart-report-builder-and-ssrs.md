---
title: "Отображение меток точек данных за пределами круговой диаграммы (построитель отчетов и службы SSRS) | Документы Майкрософт"
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
ms.assetid: 959b7574-cf43-470b-b592-4944d8a9948f
caps.latest.revision: "6"
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 357ea82283601dc936e22273ae2870a45f9704d8
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/09/2018
---
# <a name="display-data-point-labels-outside-a-pie-chart-report-builder-and-ssrs"></a>Отображение меток точек данных за пределами круговой диаграммы (построитель отчетов и службы SSRS)
  В службах [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]присваивание меток круговой диаграммы оптимизируется для отображения меток только для некоторых срезов данных. Метки могут перекрываться, если круговая диаграмма содержит слишком много срезов. Решением проблемы является отображение меток за пределами круговой диаграммы, что создает больше пространства для нанесения дальнейших меток данных. Если метки все еще перекрывают друг друга, можно создать для них больше места путем включения объемных эффектов. Это снижает диаметр круговой диаграммы, создавая больше пространства вокруг диаграммы.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-display-data-point-labels-inside-a-pie-chart"></a>Отображение меток точек данных внутри круговой диаграммы  
  
1.  Добавьте в отчет круговую диаграмму. Дополнительные сведения см. в разделе [Добавление диаграммы в отчет (построитель отчетов и службы SSRS)](../../reporting-services/report-design/add-a-chart-to-a-report-report-builder-and-ssrs.md).  
  
2.  Щелкните правой кнопкой мыши на диаграмме в области конструктора и выберите пункт **Отобразить метки данных**.  
  
### <a name="to-display-data-point-labels-outside-a-pie-chart"></a>Отображение меток точек данных за пределами круговой диаграммы  
  
1.  Создайте круговую диаграмму и отобразите метки данных.  
  
2.  Откройте панель «Свойства».  
  
3.  В области конструктора щелкните круговую диаграмму, чтобы отобразить свойства **Категория** на панели свойств.  
  
4.  Разверните узел **CustomAttributes** . Отобразится список атрибутов круговой диаграммы.  
  
5.  Установите свойство **PieLabelStyle** в значение **За пределами**.  
  
6.  Установите свойство **PieLineColor** в значение **Черный**. Свойство PieLineColor определяет линии выноски для каждой метки точки данных.  
  
### <a name="to-prevent-overlapping-labels-displayed-outside-a-pie-chart"></a>Предотвращение перекрывания меток, отображаемых за пределами круговой диаграммы  
  
1.  Создайте круговую диаграмму с внешними метками.  
  
2.  Щелкните правой кнопкой мыши за пределами круговой диаграммы, но внутри ее границ в рабочей области конструирования и выберите **Свойства области диаграммы**. Откроется диалоговое окно **Свойства области диаграммы** .  
  
3.  На вкладке **Параметры объемного отображения** выберите параметр **Разрешить объемные эффекты**.  
  
4.  Если необходимо предоставить большее пространство для меток в диаграмме, при этом оставив ее двухмерной, то в поле **Вращение** и **Наклон** установите свойства на значение **0**.  
  
## <a name="see-also"></a>См. также:  
 [Круговые диаграммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/pie-charts-report-builder-and-ssrs.md)   
 [Сбор мелких срезов на круговой диаграмме (построитель отчетов и службы SSRS)](../../reporting-services/report-design/collect-small-slices-on-a-pie-chart-report-builder-and-ssrs.md)   
 [Отображение процентных значений на круговой диаграмме (построитель отчетов и службы SSRS)](../../reporting-services/report-design/display-percentage-values-on-a-pie-chart-report-builder-and-ssrs.md)  
  
  
