---
title: "Вычисляемые меры представление (табличное) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
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
ms.assetid: 4cb9fea5-1616-467b-a539-d051e5833aea
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: c0b0d371298d083d23d2ecf6549a8954b8665657
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2018
---
# <a name="tables---calculated-measure-representation"></a>Таблицы - представление вычисляемой меры
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
Вычисляемая мера — это именованное выражение DAX, вычисляемое при каждом использовании.  
  
## <a name="calculated-measure-representation"></a>Представление вычисляемой меры  
  
### <a name="calculated-measure-in-amo"></a>Вычисляемая мера в объектах AMO  
 При использовании объектов AMO для управления вычисляемой мерой табличной модели существует соответствие «один к одному» между объектом вычисляемой меры и мерой, определенной в объекте <xref:Microsoft.AnalysisServices.Command> объекта <xref:Microsoft.AnalysisServices.MdxScript>. Каждый **вычисляемая мера** определяется как **Создание меры** выражение внутри <xref:Microsoft.AnalysisServices.Command> объекта и разделяются точкой с запятой. Все вычисляемые меры в табличной модели соответствуют строке коллекции **Создание меры** строки в одном командном объекте в <xref:Microsoft.AnalysisServices.MdxScript> объекта. Для каждой вычисляемой меры существует соответствие «один к одному» с объектом <xref:Microsoft.AnalysisServices.CalculationProperty>.  
  
 В следующем фрагменте кода показано, как создать вычисляемую меру.  
  
```  
  
private void addCalculatedMeasure(  
                   AMO.Cube modelCube  
                 , string cmTableName  
                 , string cmName  
                 , string newCalculatedMeasureExpression  
             )  
{  
    //Verify input requirements  
    if (string.IsNullOrEmpty(cmName) || string.IsNullOrWhiteSpace(cmName))  
    {  
        MessageBox.Show(String.Format("Calculated Measure name is not defined."), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Error);  
        return;  
    }  
    if (string.IsNullOrEmpty(newCalculatedMeasureExpression) || string.IsNullOrWhiteSpace(newCalculatedMeasureExpression))  
    {  
        MessageBox.Show(String.Format("Calculated Measure expression is not defined."), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Error);  
        return;  
    }  
  
    StringBuilder measuresCommand = new StringBuilder();  
  
    AMO.MdxScript mdxScript = modelCube.MdxScripts["MdxScript"];  
  
    //ToDo: Verify if measure already exits and ask user what wants to do next  
  
    if (mdxScript.Commands.Count == 1)  
    {  
        measuresCommand.AppendLine("-------------------------------------------------------------");  
        measuresCommand.AppendLine("-- Tabular Model measures command (do not modify manually) --");  
        measuresCommand.AppendLine("-------------------------------------------------------------");  
        measuresCommand.AppendLine();  
        measuresCommand.AppendLine();  
        mdxScript.Commands.Add(new AMO.Command(measuresCommand.ToString()));  
  
    }  
    else  
    {  
        measuresCommand.Append(mdxScript.Commands[1].Text);  
    }  
    measuresCommand.AppendLine(string.Format("CREATE MEASURE '{0}'[{1}]={2};", cmTableName, cmName, newCalculatedMeasureExpression));  
  
    mdxScript.Commands[1].Text = measuresCommand.ToString();  
  
    if (!mdxScript.CalculationProperties.Contains(cmName))  
    {  
        AMO.CalculationProperty cp = new AMO.CalculationProperty(cmName, AMO.CalculationType.Member);  
        cp.FormatString = ""; // ToDo: Get formatting attributes for the member  
        cp.Visible = true;  
        mdxScript.CalculationProperties.Add(cp);  
    }  
  
    try  
    {  
        modelCube.Update(AMO.UpdateOptions.ExpandFull, AMO.UpdateMode.UpdateOrCreate);  
        MessageBox.Show(String.Format("Calculated Measure successfully defined."), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Information);  
    }  
    catch (AMO.OperationException amoOpXp)  
    {  
        MessageBox.Show(String.Format("Calculated Measure expression contains syntax errors, or references undefined or missspelled elements.\nError message: {0}", amoOpXp.Message), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Warning);  
        return;  
    }  
    catch (AMO.AmoException amoXp)  
    {  
        MessageBox.Show(String.Format("AMO exception accessing the server.\nError message: {0}", amoXp.Message), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Warning);  
        return;  
    }  
    catch (Exception)  
    {  
        throw;  
    }  
}  
  
```  
  
  
