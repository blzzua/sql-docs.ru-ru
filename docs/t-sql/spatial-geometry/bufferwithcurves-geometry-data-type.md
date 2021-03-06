---
title: "BufferWithCurves (тип данных geometry) | Документы Майкрософт"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- BufferWithCurves method (geometry)
ms.assetid: 8ffaba3f-d2dd-4e57-9f41-3ced9f14b600
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d248c248d4b5d9b4a4e90954e01f15841d305319
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="bufferwithcurves-geometry-data-type"></a>BufferWithCurves (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

  Возвращает экземпляр **geometry**, представляющий набор всех точек, расстояние которых от вызывающего экземпляра **geometry** меньше параметра *distance* или равно ему.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.BufferWithCurves ( distance )  
```  
  
## <a name="arguments"></a>Аргументы  
 *distance*  
 Имеет тип **float** и указывает максимальное расстояние, на котором точки, составляющие буфер, могут находиться от экземпляра **geometry**.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
Тип возвращаемых данных SQL Server: **geometry**  
  
 Тип возвращаемых данных CLR: **SqlGeometry**  
  
## <a name="exceptions"></a>Исключения  
 Следующие критерии вызовут исключение **ArgumentException**.  
  
-   Методу, такому как `@g.BufferWithCurves()`, не передаются никакие параметры  
  
-   Методу, например `@g.BufferWithCurves('a')`, передается нечисловой параметр  
  
-   **NULL** передается методу, например `@g.BufferWithCurves(NULL)`  
  
## <a name="remarks"></a>Remarks  
 На следующем рисунке показан пример экземпляра объекта геометрии (geometry), возвращенного этим методом.  
  
 ![BufferedCurve](../../t-sql/spatial-geometry/media/bufferedcurve.gif)
  
 В следующей таблице показаны результаты, возвращенные для разных значений расстояния.  
  
|Значение расстояния|Измерения типа|Возвращенный пространственный тип|  
|--------------------|---------------------|---------------------------|  
|расстояние < 0|Ноль или один|Пустой экземпляр **GeometryCollection**|  
|расстояние < 0|Два и более|Экземпляр **CurvePolygon** или **GeometryCollection** с отрицательным буфером. **Примечание.** Отрицательный буфер может создать пустой экземпляр **GeometryCollection**|  
|расстояние = 0|Все измерения|Копия вызывающего экземпляра **geometry**|  
|расстояние > 0|Все измерения|Экземпляр **CurvePolygon** или **GeometryCollection**|  
  
> [!NOTE]  
>  Поскольку аргумент *distance* относится к типу **float**, в расчетах очень маленькое значение может быть приравнено к нулю. Когда это происходит, возвращается копия вызывающего экземпляра **geometry**. См. статью [Типы данных float и real (Transact-SQL)](../../t-sql/data-types/float-and-real-transact-sql.md).  
  
 Отрицательный буфер удаляет все точки в пределах указанного расстояния от границы геометрического объекта. На следующей иллюстрации отрицательный буфер показан в виде области круга со светлой тенью. Пунктирная линия — это граница первоначального многоугольника, а сплошная линия — граница получаемого многоугольника.  
  
 Если методу передается параметр **string**, то он будет преобразован в тип **float** или возникнет исключение `ArgumentException`.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-calling-bufferwithcurves-with-a-parameter-value--0-on-one-dimensional-geometry-instance"></a>A. Вызов метода BufferWithCurves() со значением параметра < 0 для экземпляра одномерного геометрического объекта  
 В следующем примере возвращается пустой экземпляр `GeometryCollection`:  
  
```
 DECLARE @g geometry= 'LINESTRING(3 4, 8 11)'; 
 SELECT @g.BufferWithCurves(-1).ToString(); 
 ```
  
### <a name="b-calling-bufferwithcurves-with-a-parameter-value--0-on-a-two-dimensional-geometry-instance"></a>Б. Вызов метода BufferWithCurves() со значением параметра < 0 для экземпляра двумерного геометрического объекта  
 В следующем примере возвращается экземпляр `CurvePolygon` с отрицательным буфером:  
  
```
 DECLARE @g geometry = 'CURVEPOLYGON(COMPOUNDCURVE(CIRCULARSTRING(0 4, 4 0, 8 4), (8 4, 0 4)))'; 
 SELECT @g.BufferWithCurves(-1).ToString()
 ```  
  
### <a name="c-calling-bufferwithcurves-with-a-parameter-value--0-that-returns-an-empty-geometrycollection"></a>В. Вызов функции BufferWithCurves() со значением параметра < 0, которая возвращает пустую коллекцию GeometryCollection  
 Следующий пример демонстрирует, что происходит, когда параметр *distance* равняется –2:  
  
```
 DECLARE @g geometry = 'CURVEPOLYGON(COMPOUNDCURVE(CIRCULARSTRING(0 4, 4 0, 8 4), (8 4, 0 4)))'; 
 SELECT @g.BufferWithCurves(-2).ToString();
 ```  
  
 Эта инструкция **SELECT** возвращает `GEOMETRYCOLLECTION EMPTY`  
  
### <a name="d-calling-bufferwithcurves-with-a-parameter-value--0"></a>Г. Вызов функции BufferWithCurves() со значением параметра = 0  
 В следующем примере возвращается копия вызывающего экземпляра **geometry**:  
  
```
 DECLARE @g geometry = 'LINESTRING(3 4, 8 11)'; 
 SELECT @g.BufferWithCurves(0).ToString();
 ```  
  
### <a name="e-calling-bufferwithcurves-with-a-non-zero-parameter-value-that-is-extremely-small"></a>Д. Вызов функции BufferWithCurves() с ненулевым, но очень малым значением параметра  
 В следующем примере также возвращается копия вызывающего экземпляра **geometry**:  
  
```
 DECLARE @g geometry = 'LINESTRING(3 4, 8 11)'; 
 DECLARE @distance float = 1e-20; 
 SELECT @g.BufferWithCurves(@distance).ToString();
 ```  
  
### <a name="f-calling-bufferwithcurves-with-a-parameter-value--0"></a>Е. Вызов функции BufferWithCurves() со значением параметра > 0  
 В следующем примере возвращается экземпляр `CurvePolygon`:  
  
```
 DECLARE @g geometry= 'LINESTRING(3 4, 8 11)'; 
 SELECT @g.BufferWithCurves(2).ToString();
 ```  
  
### <a name="g-passing-a-valid-string-parameter"></a>Ж. Передача допустимого строкового параметра  
 В следующем примере возвращается тот же экземпляр `CurvePolygon`, который упоминался ранее, но методу передается строковый параметр:  
  
```
 DECLARE @g geometry= 'LINESTRING(3 4, 8 11)'; 
 SELECT @g.BufferWithCurves('2').ToString();
 ```  
  
### <a name="h-passing-an-invalid-string-parameter"></a>З. Передача недопустимого строкового параметра  
 В следующем примере возникнет ошибка:  
  
```
 DECLARE @g geometry = 'LINESTRING(3 4, 8 11)' 
 SELECT @g.BufferWithCurves('a').ToString();
 ```  
  
 Обратите внимание на то, что в предыдущих двух примерах передавался строковый литерал методу `BufferWithCurves()`. Первый пример будет работать, поскольку строковый литерал может быть преобразован в числовое значение. Но во втором примере возникнет исключение `ArgumentException`.  
  
### <a name="i-calling-bufferwithcurves-on-multipoint-instance"></a>И. Вызов метода BufferWithCurves() для экземпляра объекта MultiPoint  
 Следующий пример возвращает два экземпляра `GeometryCollection` и один экземпляр `CurvePolygon`:  
  
```
 DECLARE @g geometry = 'MULTIPOINT((1 1),(1 4))'; 
 SELECT @g.BufferWithCurves(1).ToString(); 
 SELECT @g.BufferWithCurves(1.5).ToString(); 
 SELECT @g.BufferWithCurves(1.6).ToString();
 ```  
  
 Первые две инструкции **SELECT** возвращают экземпляр `GeometryCollection`, поскольку параметр *distance* меньше или равен 1/2 расстояния между двумя точками (1 1) и (1 4). Третья инструкция **SELECT** возвращает экземпляр `CurvePolygon`, поскольку находящиеся в буферной памяти экземпляры двух точек (1 1) и (1 4) перекрываются.  
  
## <a name="see-also"></a>См. также:  
 [Расширенные методы экземпляров Geometry](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)  
 
