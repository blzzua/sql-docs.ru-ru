---
title: "Указание согласованных цветов в нескольких фигурных диаграммах (построитель отчетов и службы SSRS) | Документация Майкрософт"
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
ms.assetid: d52f68e9-2ba7-4bff-9053-4089e5164ab4
caps.latest.revision: "8"
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: fecb8cd6e36040876e21baa9e1789d95fb5dba49
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/09/2018
---
# <a name="specify-consistent-colors-across-multiple-shape-charts-report-builder-and-ssrs"></a>Указание согласованных цветов для нескольких фигурных диаграмм (построитель отчетов и службы SSRS)
  На нефигурных диаграммах в отчете с разбиением на страницы [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] выбирает новый цвет из палитры, связанной с индексом рядов в диаграмме. Например, первый ряд в диаграмме сопоставлен с первым цветом палитры. Однако в фигурных диаграммах используется другой принцип. В фигурных диаграммах каждый цвет палитры сопоставлен с точкой данных в наборе данных. Так, точка данных 1 сопоставлен с первым цветом палитры, точка данных 2 — со вторым цветом палитры и т. д.  
  
 Если точка данных не имеет значения, она опускается из изображения на фигурной диаграмме. Это означает, что точка данных не включается в число окрашиваемых. Так, если точка 2 имеет значение «ноль», точка 1 будет соответствовать первому цвету палитры, а точка 3 — второму цвету палитры. Такой подход полезен, поскольку пустые точки набора данных круговой диаграммы не обязательно используют палитру цветов, когда нет необходимости рисования пустой точки.  
  
 В качестве побочного эффекта при отображении в отчете нескольких круговых диаграмм расположенные в этих диаграммах точки данных одной и той же категории группирования могут отображаться различными цветами. Для решения этой проблемы необходимо определять индивидуальные цвета, соответствующие группе категорий, а не индивидуальным значениям данных. Способ определения зависит от того, представляет ли собой фигурная диаграмма sparkline-график в таблице или матрице или она непосредственно находится в отчете.  
  
 Условные обозначения связаны с рядом, поэтому любой цвет, заданный пользователем для ряда, будет автоматически отображаться в условных обозначениях.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="to-specify-consistent-colors-across-multiple-sparkline-shape-charts-in-a-table-or-matrix"></a>Указание согласованных цветов для нескольких фигурных диаграмм в виде спарклайн-графиков в таблице или матрице  
  
1.  Щелкните диаграмму, чтобы отобразить панель «Данные диаграммы».  
  
2.  Щелкните правой кнопкой мыши в области **Группы категорий** и выберите пункт **Свойства группы категорий**.  
  
3.  На вкладке «Общие» в окне **Синхронизация групп в** выберите название категории, которую вы хотите синхронизовать по цвету, и нажмите кнопку **ОК**.  
  
## <a name="to-specify-consistent-colors-across-multiple-shape-charts"></a>Указание согласованных цветов в нескольких фигурных диаграммах  
  
1.  Щелкните правой кнопкой мыши область за пределами текста отчета и выберите пункт **Свойства отчета**.  
  
2.  В текстовом поле **Код**введите следующий код.  
  
    ```  
    Private colorPalette As String() = {"Color1", "Color2", "Color3"}  
    Private count As Integer = 0  
    Private mapping As New System.Collections.Hashtable()  
    Public Function GetColor(ByVal groupingValue As String) As String  
        If mapping.ContainsKey(groupingValue) Then  
            Return mapping(groupingValue)  
        End If  
        Dim c As String = colorPalette(count Mod colorPalette.Length)  
        count = count + 1  
        mapping.Add(groupingValue, c)  
        Return c  
    End Function  
    ```  
  
    > [!NOTE]  
    >  Строки «Color1» пользователю следует заменять собственными цветами. Можно использовать именованные цвета, например, «Красный», или представляющие тот или иной цвет шестиразрядные шестнадцатеричные значения, такие, как "#FFFFFF" для черного. Если определено более трех цветов, нужно расширить массив цветов, чтобы число цветов в массиве соответствовало числу точек в фигурной диаграмме. Можно добавлять новые цвета к массиву, составив список строковых значений с разделителями-запятыми, содержащий именованные цвета или шестнадцатеричные представления цветов.  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
4.  Щелкните правой кнопкой мыши фигурную диаграмму и выберите пункт **Свойства ряда**.  
  
5.  В меню **Заливка**нажмите кнопку **Выражение** (*fx*) и измените выражение для свойства **Цвет** .  
  
6.  Введите следующее выражение, где "MyCategoryField" ― это поле, отображаемое в области **Группы Категорий (Category Groups)** :  
  
    ```  
    =Code.GetColor(Fields!MyCategoryField)  
    ```  
  
## <a name="see-also"></a>См. также:  
 [Форматирование цветов для рядов на диаграмме (построитель отчетов и службы SSRS)](../../reporting-services/report-design/formatting-series-colors-on-a-chart-report-builder-and-ssrs.md)   
 [Добавление в диаграмму стилей рамки, рельефа и текстуры &#40;построитель отчетов и службы SSRS&#41;](../../reporting-services/report-design/chart-effects-add-bevel-emboss-or-texture-report-builder.md)   
 [Задание цветов диаграммы с помощью палитры &#40;построитель отчетов и службы SSRS&#41;](../../reporting-services/report-design/define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs.md)   
 [Добавление пустых точек на диаграмму &#40;построитель отчетов и службы SSRS&#41;](../../reporting-services/report-design/add-empty-points-to-a-chart-report-builder-and-ssrs.md)   
 [Фигурные диаграммы &#40;построитель отчетов и службы SSRS&#41;](../../reporting-services/report-design/shape-charts-report-builder-and-ssrs.md)   
 [Связывание нескольких областей данных с одним набором данных (построитель отчетов и службы SSRS)](../../reporting-services/report-design/linking-multiple-data-regions-to-the-same-dataset-report-builder-and-ssrs.md)   
 [Вложенные области данных (построитель отчетов и службы SSRS)](../../reporting-services/report-design/nested-data-regions-report-builder-and-ssrs.md)   
 [Спарклайны и гистограммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/sparklines-and-data-bars-report-builder-and-ssrs.md)  
  
  
