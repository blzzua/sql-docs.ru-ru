---
title: Заметки языка CSDL для бизнес-аналитики (CSDLBI) | Документы Microsoft
ms.custom: ''
ms.date: 03/30/2018
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: bf6f372a-bc67-45ea-a771-b2dc5b0527e5
caps.latest.revision: 21
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: f2f0d4c06b15a6bb2fab3eaf44a9bcb17f225a91
ms.sourcegitcommit: 8f1d1363e18e0c32ff250617ab6cb2da2147bf8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/03/2018
---
# <a name="csdl-annotations-for-business-intelligence-csdlbi"></a>Заметки языка CSDL для бизнес-аналитики (CSDLBI)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] поддерживает представление определения табличной модели в формате XML, называемое языком определения концептуальной схемы с заметками бизнес-аналитики (CSDLBI). В этом разделе представлены общие сведения о CSDLBI и его использовании в моделях данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
## <a name="understanding-the-role-of-csdl"></a>Основные сведения о роли языка CSDL  
 Язык концептуальной схемы данных (CSDL) — это язык на основе XML, описывающий сущности, связи и функции. Язык CSDL определен как часть платформы Entity Data Framework. Заметки бизнес-аналитики — это расширение, разработанное для поддержки моделирования данных с помощью [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
 Несмотря на то что язык CSDL совместим с платформой Entity Data Framework, для построения с его помощью табличной модели или основанного на модели отчета не требуются ни знания модели «сущность-связь», ни какие-либо специальные средства. Модели создаются с помощью клиентских средств, таких как [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], или API, таких как объекты AMO, и развертываются на сервере.  
  
 Схема CSDLBI создается сервером служб Analysis Services в ответ на запрос определения модели от клиентских средств, таких как [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]. Клиентское приложение отправляет XML-запрос серверу служб Analysis Services, на котором размещены данные модели. В ответ сервер отправляет XML-сообщение, содержащее определение сущностей в модели с использованием заметок CSDLBI. С помощью этих сведений клиентское средство создания отчетов представляет поля, статистические выражения и меры, доступные в модели. Заметки CSDLBI также содержат сведения о том, как группировать, сортировать и форматировать данные.  
  
 Общие сведения о CSDLBI см. в разделе [основные понятия CSDLBI](../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/csdlbi-concepts.md).  
  
### <a name="working-with-csdl"></a>Работа с языком CSDL  
 Набор заметок CSDLBI, представляющий любую конкретную табличную модель, — это XML-документ, содержащий коллекцию сущностей, как простых, так и сложных. Сущности определяют таблицы (или измерения), столбцы (атрибуты), ассоциации (связи) и формулы, включенные в вычисляемые столбцы, меры и ключевые показатели эффективности.  
  
 Эти объекты нельзя изменять непосредственно, для их изменения следует использовать клиентские средства и API-интерфейсы для работы с табличными моделями.  
  
 CSDL-код для модели можно получить, отправив запрос DISCOVER на сервер, на котором размещается модель. Запрос следует уточнить, указав сервер и модель, а также при необходимости представление или перспективу. Возвращаемое сообщение является XML-строкой. Некоторые элементы зависят от языка и могут возвращать разные значения в зависимости от языка текущего соединения. Дополнительные сведения см. в разделе [строк DISCOVER_CSDL_METADATA](../../analysis-services/schema-rowsets/xml/discover-csdl-metadata-rowset.md).  
  
### <a name="csdlbi-versions"></a>Версии CSDLBI  
 Изначальная спецификация языка CSDL (для платформы Entity Data Framework) предоставляет большинство сущностей и свойств, необходимых для моделирования. Заметки бизнес-аналитики поддерживают особые требования табличных моделей, необходимые для клиентов (таких как [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]) свойства отчетов и дополнительные метаданные, необходимые для многомерных моделей. В этом разделе описаны изменения в каждой версии.  
  
 **CSDLBI 1.0**  
  
 Начальный набор добавлений в схему CSDL для поддержки табличных моделей [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] содержал заметки для поддержки моделирования данных, пользовательских вычислений и расширенного представления.  
  
-   Новые элементы и свойства для поддержки табличных моделей. Например, было добавлено свойство для указания типа запроса к базе данных, используемого для заполнения модели.  
  
-   Новые свойства и расширения существующих сущностей.  Например, элемент Association был расширен для поддержки связей.  
  
-   Свойства визуализации и навигации. Например, добавлены свойства для поддержки пользовательских полей сортировки, изображений по умолчанию и  
  
 **CSDLBI 1.1**  
  
 Эта версия схемы CSDLBI включает расширения для поддержки многомерных баз данных (таких как кубы OLAP). Новые элементы и свойства имеют следующий вид:  
  
-   Поддержка измерений как сущностей.  
  
-   Поддержка иерархий.  
  
-   Доступ к разделам ROLAP.  
  
-   Поддержка переводов.  
  
-   Поддержка перспектив.  
  
 Подробные сведения об отдельных элементах в заметки CSDLBI см [Технический справочник по заметки бизнес-Аналитики для языка CSDL](../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/technical-reference-for-bi-annotations-to-csdl.md). Сведения о базовой спецификации языка CSDL см. в разделе [спецификация языка CSDL](http://go.microsoft.com/fwlink/?LinkId=205855) на сайте MSDN.  
  
## <a name="see-also"></a>См. также  
 [Общие сведения о модели табличного объекта на совместимость уровни 1050 до 1103](../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)   
 [Основные понятия CSDLBI](../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/csdlbi-concepts.md)   
 [Общие сведения о модели табличного объекта на совместимость уровни 1050 до 1103](../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)  
  
  
