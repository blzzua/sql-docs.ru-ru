---
title: "Биржевые диаграммы (построитель отчетов и службы SSRS) | Документы Майкрософт"
ms.custom: 
ms.date: 05/30/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: report-design
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f75ca11e-b7f5-4ac0-ba17-fe6f82742dad
caps.latest.revision: "8"
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: f92366bf3f1e262f033827a5db0aa44d3526bde5
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/09/2018
---
# <a name="stock-charts-report-builder-and-ssrs"></a>Биржевые диаграммы (построитель отчетов и службы SSRS)

  Биржевая диаграмма — это диаграмма, специально созданная для работы с финансовыми или научными данными, в которой на каждую точку данных приходится до четырех значений. Эти значения сравниваются со значениями максимума, минимума, открытия и закрытия, используемыми для отображения биржевых данных. В этом типе диаграммы значения открытия и закрытия отображаются с помощью маркеров (обычно это линии или треугольники). В следующем примере значения открытия помечены маркерами слева, а значения закрытия — маркерами справа.  
  
 ![Биржевая диаграмма](../../reporting-services/report-design/media/rs-stockchart.gif "Биржевая диаграмма")  
  
 Пример биржевой диаграммы доступен в виде образца отчета построителя отчетов. Дополнительные сведения о скачивании этого и других примеров отчетов см. в статье [Report Builder and Report Designer sample reports](http://go.microsoft.com/fwlink/?LinkId=198283).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="variations"></a>Разновидности  
  
-   **Диаграмма «японские свечи»**. Диаграмма «японские свечи» — это специализированная форма биржевой диаграммы, в которой для отражения расстояния между значениями открытия и закрытия используются прямоугольники. Как и в биржевой диаграмме, в диаграмме «японские свечи» может быть отображено до четырех значений для каждой точки данных.  
  
## <a name="data-considerations-for-stock-charts"></a>Соображения касательно данных в биржевых диаграммах  
  
-   При представлении большого количества биржевых точек данных, например изменения курса акций в течение года, сложно определить каждое отдельное значение максимума, минимума, открытия и закрытия каждой точки данных. В этом случае вместо биржевой диаграммы следует использовать график.  
  
-   При создании осей метки на них обычно начинаются с нуля.  Обычно колебания курса акций не так велики, как разброс значений в других наборах данных. В связи с этим можно отключить метки осей, начиная с нуля, чтобы обеспечить лучший просмотр данных. Это можно сделать, установив свойство **IncludeZero** в значение **false** в диалоговом окне **Свойства оси** окна «Свойства». Дополнительные сведения о том, как диаграмма создает метки осей, см. в разделе [Форматирование меток оси на диаграмме (построитель отчетов и службы SSRS)](../../reporting-services/report-design/formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md).  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] предоставляют множество вычисляемых формул для работы с биржевыми диаграммами, включая «Индикатор цен», «Индекс относительной силы», «Схождение/расхождение скользящего среднего» и т.п.  

## <a name="next-steps"></a>Следующие шаги

[Диаграммы диапазонов](../../reporting-services/report-design/range-charts-report-builder-and-ssrs.md)   
[Диаграммы](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)   
[Форматирование диаграммы](../../reporting-services/report-design/formatting-a-chart-report-builder-and-ssrs.md)   
[Диалоговое окно "Свойства оси" — "Параметры оси"](http://msdn.microsoft.com/library/b276e210-7a12-48ae-971b-7dabae51df11)  

Остались вопросы? [Посетите форум служб Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231).
