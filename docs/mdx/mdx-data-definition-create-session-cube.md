---
title: Инструкция CREATE SESSION CUBE (многомерные Выражения) | Документы Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- CREATE_SESSION_CUBE
- SESSION
- CUBE
- SESSION CUBE
- CREATE SESSION CUBE
- CREATE SESSION
- CREATE
dev_langs:
- kbMDX
helpviewer_keywords:
- CREATE SESSION CUBE
- statements [MDX], CREATE SESSION CUBE
ms.assetid: 06b90f44-d943-4a52-b0d8-4bcbc57ed6ec
caps.latest.revision: 17
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: be395f43e1a372e54f9759edcf58d0b35f03d15c
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="mdx-data-definition---create-session-cube"></a>Определения данных многомерных Выражений — создать КУБ СЕАНСА
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Создает куб сеанса и заполняет его данными существующего куба сервера. Куб сеанса видим только на панели текущего сеанса. Просмотреть куб сеанса и выполнить к нему запрос из любого другого сеанса невозможно. При закрытии сеанса куб сеанса неявно удаляется.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
CREATE SESSION CUBE session_cube_name FROM <cube list> (<param list>)  
  
<cube list>::= source_cube_name [,<cube list>]  
  
<param list>::= <param> ,<param list> | <param>  
  
<param>::= <dims list> | <measures list>  
  
<measures list>::= <measure>[, <measures list>]   
  
<dims list>::= <dim def> [, <dims list>]  
  
<measure>::= MEASURE source_cube_name.measure_name [<visibility qualifier>] [AS measure_name]   
  
<dim def>::= <source dim def> | <derived dim def>  
  
<source dim def>::= DIMENSION source_cube_name.dimension_name [<dim flags>] [<visibility qualifier>] [AS dimension_name>] [FROM <dim from clause> ] [<dim content def>]  
  
<dim flags>::= NOT_RELATED_TO_FACTS   
  
<dim from clause>::= <reg dim from clause>   
  
<dim reg from clause>::= dimension_name  
  
<dim content def>::= ( <level list> [,<grouping list>] [,<member slice list>] [,<default member>] )  
  
<level list>::= <level def> [, <level list>]  
  
<level def>::= LEVEL level_name [<level type> ] [AS level_name] [<level content def>]  
  
<level content def>::= ( <property list> ) | NO_PROPERTIES  
  
<level type>::= GROUPING  
  
<property list>::= <property def> [, <property list>]  
  
<property def>::= PROPERTY property_name   
  
<grouping list>::= <grouping entity> [,<grouping list>]  
  
<grouping entity>::= GROUP group_level_name.group_name (<mixed list>)  
  
<grp mixed list>::= <grp mixed element> [,<grp mixed list>]  
  
<grp mixed element>::= <grouping entity> | <member def>  
  
<member slice list>::= <member list>  
  
<member list>::= <member def> [, <member list>]  
  
<member def>::= MEMBER member_name  
  
<default member>::= DEFAULT_MEMBER AS MDX_expression  
  
<visibility qualifier>::= HIDDEN  
  
```  
  
## <a name="syntax-elements"></a>Элементы синтаксиса  
 session_cube_name  
 Имя куба сеанса.  
  
 source_cube_name  
 Имя куба, на котором основан куб сеанса.  
  
 source_cube_name.measure_name  
 Полное имя исходной меры, включаемой в куб сеанса. Вычисляемые элементы измерения «Меры» недопустимы.  
  
 measure_name  
 Имя меры в кубе сеанса.  
  
 source_cube_name.dimension_name  
 Полное имя исходного измерения, включаемого в куб сеанса.  
  
 dimension_name  
 Имя измерения в кубе сеанса.  
  
 ИЗ \<dim предложение from >  
 Спецификация, допустимая только для определения производного измерения.  
  
 NOT_RELATED_TO_FACTS  
 Спецификация, допустимая только для определения производного измерения.  
  
 \<Тип уровня >  
 Спецификация, допустимая только для определения производного измерения.  
  
## <a name="remarks"></a>Remarks  
 В отличие от кубов сервера и локальных кубов куб сеанса не сохраняется вне области сеанса, в котором он был создан. Куб сеанса определяется на основе мер и измерений, которые его определяют. Существует два типа измерений.  
  
-   Измерения источника — это измерения, которые были частью одного из исходных кубов.  
  
-   Производные измерения — это измерения, которые обеспечивают новые возможности анализа. Производным измерением может являться обычное измерение, определенное на основе исходного измерения, которое является горизонтальным или вертикальным срезом либо содержит пользовательское группирование элементов измерения. Производным также может быть измерение интеллектуального анализа данных, основанное на модели интеллектуального анализа данных.  
  
> [!NOTE]  
>  Ключевое слово «измерение» может относиться либо к измерениям, либо к иерархиям.  
  
 Кубы сеанса в первую очередь используются для динамического группирования элементов атрибутов в пользовательские группы элементов с помощью клиентских приложений, таких как Microsoft Excel. В кубе сеанса можно выполнять следующие задачи:  
  
-   Исключать измерения, которые существуют в исходном кубе.  
  
-   Добавлять или исключать иерархии из измерения.  
  
-   Исключать группы мер или определенные меры.  
  
-   Добавлять новые атрибуты, основанные на привязке атрибутов, для создания групп в зависимости от существующего атрибута.  
  
> [!IMPORTANT]  
>  Безопасность объектов куба сеанса наследуется от базовых исходных объектов. Другие объекты, такие как действия и скрипты вычисления, также наследуются кубом сеанса.  
  
 Инструкция CREATE SESSION CUBE следует следующим правилам.  
  
-   Группирование на основе иерархий типа «родители-потомки» выполнить нельзя.  
  
-   Группирование на основе измерений ROLAP выполнить нельзя.  
  
-   Группирование на основе связанных измерений выполнить нельзя.  
  
-   Группирование на основе уровней с пользовательскими свертками выполнить нельзя.  
  
-   Группирование на основе иерархий дискретизированных атрибутов выполнить нельзя.  
  
-   Нельзя выполнить группирование на искусственных иерархиях, которые являются иерархиями со связями типа «многие ко многим» между уровнями.  
  
-   Явные ссылки на имя куба в скрипте многомерных выражений при группировании нарушаются, потому что куб сеанса имеет другое имя. Используйте вместо них ключевое слово CURRENTCUBE.  
  
-   Группирование на измерениях с явно указанными элементами по умолчанию выполнить нельзя.  
  
-   При группировании вычисляемые элементы области сеанса в исходном кубе сервера удаляются.  
  
-   При выполнении группирования по измерению куба в кубе сервера группирование влияет на все измерения куба, основанные на этом измерении.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как создать версию куба Adventure Works области сеанса, содержащую меру Reseller Sales Amount и измерения Reseller, Product, Geography и Date. В рамках этого куба сеанса создаются две группы. Одна группа содержит страны в Европе, а другая группа содержит группы в Северной Америке. В этом примере приведен упрощенный вариант инструкции CREATE SESSION CUBE, сформированной Microsoft Excel при создании пользовательского группирования элементов.  
  
```  
CREATE SESSION CUBE [Adventure Works_XL_GROUPING1]   
   FROM [Adventure Works]   
   ( MEASURE [Adventure Works].[Internet Sales Amount]  
   ,MEASURE [Adventure Works].[Reseller Sales Amount]  
   ,DIMENSION [Adventure Works].[Date].[Calendar]  
   ,DIMENSION [Adventure Works].[Date].[Calendar Year]  
   ,DIMENSION [Adventure Works].[Date].[Calendar Semester]  
   ,DIMENSION [Adventure Works].[Date].[Calendar Quarter]  
   ,DIMENSION [Adventure Works].[Date].[Month Name]  
   ,DIMENSION [Adventure Works].[Date].[Date]  
   ,DIMENSION [Adventure Works].[Geography].[Country]   
      HIDDEN AS _XL_GROUPING81  
   ,DIMENSION [Adventure Works].[Geography].[State-Province]  
   ,DIMENSION [Adventure Works].[Geography].[City]  
   ,DIMENSION [Adventure Works].[Geography].[Postal Code]  
   ,DIMENSION [Adventure Works].[Geography].[Geography]  
   ,DIMENSION [Adventure Works].[Product].[Product Categories]  
   ,DIMENSION [Adventure Works].[Product].[Category]  
   ,DIMENSION [Adventure Works].[Product].[Subcategory]  
   ,DIMENSION [Adventure Works].[Product].[Product]  
   ,DIMENSION [Adventure Works].[Product].[Product Key]  
   ,DIMENSION [Adventure Works].[Reseller].[Reseller]  
   ,DIMENSION [Adventure Works].[Reseller].[Geography Key]  
   ,DIMENSION [Geography].[Country]   
      NOT_RELATED_TO_FACTS FROM _XL_GROUPING81   
          ( LEVEL [(All)]  
         ,LEVEL [Country1] GROUPING  
         ,LEVEL [Country]  
            ,GROUP [Country1].[CountryXl_Grp_1]   
                ( MEMBER [Geography].[Country].&[Canada]  
                  ,MEMBER [Geography].[Country].&[United States] )  
            ,GROUP [Country1].[CountryXl_Grp_2]   
                ( MEMBER [Geography].[Country].&[France]  
                  ,MEMBER [Geography].[Country].&[Germany]  
                  ,MEMBER [Geography].[Country].&[United Kingdom] )   
            )   
   )  
```  
  
## <a name="see-also"></a>См. также:  
 [Инструкции определения данных &#40; Многомерные Выражения &#41;](../mdx/mdx-data-definition-statements-mdx.md)   
 [СОЗДАТЬ инструкцию глобального КУБА &#40; Многомерные Выражения &#41;](../mdx/mdx-data-definition-create-global-cube.md)  
  
  
