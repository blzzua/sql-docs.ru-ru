---
title: "Метод isSparseColumnSet (SQLServerResultSetMetaData) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ac363670-78ae-49f1-aeda-4fba3329a258
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0486fd19f95b6a9b4d987c4b4dc7f1810e82543d
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="issparsecolumnset-method-sqlserverresultsetmetadata"></a>Метод isSparseColumnSet (SQLServerResultSetMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Указывает, является ли столбец из результирующего набора набором разреженных столбцов.  
  
## <a name="syntax"></a>Синтаксис  
  
```scr  
public boolean isSparseColumnSet(int column)  
```  
  
#### <a name="parameters"></a>Параметры  
 *столбец*  
  
 Индекс столбца (начинающийся с единицы).  
  
## <a name="return-value"></a>Возвращаемое значение  
 **значение true,** Если столбца в результирующем наборе набор разреженных столбцов, в противном случае **false**.  
  
## <a name="remarks"></a>Замечания  
 Этот метод не извлекает данные из базы данных.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-methods.md)   
 [Элементы SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-members.md)   
 [Класс SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)  
  
  
