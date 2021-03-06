---
title: "Архитектура серверных объектов ADOMD.NET | Документы Microsoft"
ms.custom: 
ms.date: 02/14/2018
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
helpviewer_keywords:
- ADOMD.NET, object model
- object model [ADOMD.NET]
ms.assetid: bdc81de9-b390-4654-b62a-cd6c0c9ca10d
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 8f0cae374f2670228bbced569d81e87b34a350d2
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2018
---
# <a name="adomdnet-server-object-architecture"></a>Архитектура серверных объектов ADOMD.NET
  Серверные объекты ADOMD.NET являются вспомогательные объекты, которые могут использоваться для создания определяемой пользователем функции (UDF) или хранимых процедур в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
> [!NOTE]  
>  Для использования **Microsoft.AnalysisServices.AdomdServer** пространства имен (и эти объекты), необходимо добавить ссылку на библиотеку msmgdsrv.dll проект определяемой пользователем функции или хранимой процедуры.  
  
 ![Показывает отношения между объектами на сервере ADOMD.NET](../../analysis-services/multidimensional-models-adomd-net-server/media/adomdnetserverobjectmodel.gif "показывает отношения между объектами на сервере ADOMD.NET")  
Модель объектов ADOMD.NET  
  
 Взаимодействие с иерархией объектов ADOMD.NET обычно начинается с одного или нескольких объектов верхнего уровня, как описано в следующей таблице.  
  
|Чтобы|Используемый объект|  
|--------|---------------------|  
|Вычисление многомерных выражений|<xref:Microsoft.AnalysisServices.AdomdServer.Expression><br /> Объект <xref:Microsoft.AnalysisServices.AdomdServer.Expression> позволяет выполнить многомерное выражение и вычислить его по указанному кортежу.|  
|Обеспечение поддержки выполнения функций MDX без создания полной инструкции многомерных выражений|<xref:Microsoft.AnalysisServices.AdomdServer.MDX><br /> С помощью объекта <xref:Microsoft.AnalysisServices.AdomdServer.MDX> удобно вызывать стандартные функции MDX без использования объекта <xref:Microsoft.AnalysisServices.AdomdServer.Expression>. В будущих версиях планируется появление дополнительных функций для объекта <xref:Microsoft.AnalysisServices.AdomdServer.MDX>.|  
|Представление текущего контекста выполнения для определяемой пользователем функции|<xref:Microsoft.AnalysisServices.AdomdServer.Context><br /> Объект <xref:Microsoft.AnalysisServices.AdomdServer.Context> выдает такие сведения, как текущий куб или модель интеллектуального анализа данных, а также различные коллекции метаданных. Объект <xref:Microsoft.AnalysisServices.AdomdServer.Context> используется главным образом в качестве свойства <xref:Microsoft.AnalysisServices.AdomdServer.Hierarchy.CurrentMember%2A> объекта <xref:Microsoft.AnalysisServices.AdomdServer.Hierarchy>. Благодаря этому основному варианту использования автор определяемой пользователем функции или хранимой процедуры может принимать решения, исходя из того, какой элемент из определенного измерения запроса включен.|  
|Создание наборов и кортежей|<xref:Microsoft.AnalysisServices.AdomdServer.SetBuilder>, <xref:Microsoft.AnalysisServices.AdomdServer.TupleBuilder><br /> Объект <xref:Microsoft.AnalysisServices.AdomdServer.SetBuilder> позволяет создавать неизменяемые наборы, а объект <xref:Microsoft.AnalysisServices.AdomdServer.TupleBuilder> — неизменяемые кортежи.|  
|Поддержка неявного преобразования и приведения для шести основных типов языка многомерных выражений|<xref:Microsoft.AnalysisServices.AdomdServer.MDXValue><br /> Объект <xref:Microsoft.AnalysisServices.AdomdServer.MDXValue> обеспечивает неявное преобразование и приведение для следующих типов:<br /><br /> <xref:Microsoft.AnalysisServices.AdomdServer.Hierarchy><br /><br /> <xref:Microsoft.AnalysisServices.AdomdServer.Level><br /><br /> <xref:Microsoft.AnalysisServices.AdomdServer.Member><br /><br /> <xref:Microsoft.AnalysisServices.AdomdServer.Tuple><br /><br /> <xref:Microsoft.AnalysisServices.AdomdServer.Set><br /><br /> Скалярные типы или типы значений|  
  
## <a name="see-also"></a>См. также  
 [Программирование сервера ADOMD.NET](../../analysis-services/multidimensional-models-adomd-net-server/adomd-net-server-programming.md)  
  
  
