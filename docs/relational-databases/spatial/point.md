---
title: "Точка | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: spatial
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-spatial
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Point geometry subtype [SQL Server]
- geometry data type [SQL Server], spatial data
ms.assetid: 2a596ec4-8b2f-4962-bcb4-e5c8f77edad5
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 3fd20af212e94f33bf72ca35f6cf674bb46e50d0
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/12/2018
---
# <a name="point"></a>Точка
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
В пространственных данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляр **Point** является объектом без измерения, представляющим отдельное месторасположение, и может содержать значения Z (уровень) и M (мера).  
  
## <a name="geography-data-type"></a>Тип данных Geography  
 Тип Point для типа данных geography представляет единичное расположение, где *Lat* представляет широту, а *Long* — долготу. Значения широты и долготы измеряются в градусах. Значения широты всегда находятся в интервале [-90, 90]. Все значения, находящиеся вне этого диапазона, вызывают исключение. Значения долготы всегда находятся в интервале [-180, 180]. Все значения, находящиеся вне этого диапазона, преобразуются в соответствующие значения в его пределах. Например, если введено значение долготы 190, то оно будет преобразовано в значение -170. *SRID* представляет идентификатор пространственной ссылки экземпляра **geography** , который необходимо вернуть.  
  
## <a name="geometry-data-type"></a>Тип данных Geometry  
 Тип элемента для геометрических типов данных представляет собой единое место, где *X* представляет координату x создаваемого экземпляра Point, а *Y* — координату Y создаваемого экземпляра Point. *SRID* представляет идентификатор пространственной ссылки экземпляра **geometry** , который необходимо вернуть.  
  
## <a name="examples"></a>Примеры  
 В следующем примере показано создание экземпляра `geometry Point`, представляющего точку (3, 4) со значением SRID, равным 0.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POINT (3 4)', 0);  
```  
  
 В следующем примере показано создание экземпляра `geometry``Point` , представляющего точку (3, 4) со значениями Z (уровень) и M (мера), равными соответственно 7 и 2,5, и значением SRID по умолчанию, равным 0.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('POINT(3 4 7 2.5)');  
```  
  
 В последнем примере возвращаются значения X, Y, Z и M для экземпляра `geometry``Point` .  
  
```  
SELECT @g.STX;  
SELECT @g.STY;  
SELECT @g.Z;  
SELECT @g.M;  
```  
  
 Для Z и M может быть явно указано значение NULL, как показано в следующем примере.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('POINT(3 4 NULL NULL)');  
```  
  
## <a name="see-also"></a>См. также:  
 [MultiPoint](../../relational-databases/spatial/multipoint.md)   
 [STX (тип данных geometry)](../../t-sql/spatial-geometry/stx-geometry-data-type.md)   
 [STY (тип данных geometry)](../../t-sql/spatial-geometry/sty-geometry-data-type.md)   
 [Пространственные данные (SQL Server)](../../relational-databases/spatial/spatial-data-sql-server.md)  
  
  
