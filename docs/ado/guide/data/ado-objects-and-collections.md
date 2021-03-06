---
title: "Объекты ADO и коллекции | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ADO, objects and collections
ms.assetid: 7a745aae-9372-49b6-8dae-b9c93e5f3216
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ae5e56e0440901de5c40ab4a2256c076f702d6e1
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="ado-objects-and-collections"></a>Объекты ADO и коллекции
ADO состоит из девяти следующие объекты и четыре коллекции.  
  
|Объект или коллекция|Описание|  
|--------------------------|-----------------|  
|**Подключение** объекта|Представляет уникальный сеанс с источником данных. В случае системы базы данных клиента и сервера может быть эквивалентом действительное сетевое подключение к серверу. В зависимости от функциональных возможностей, поддерживаемых поставщика, некоторые коллекции, методы или свойства **подключения** могут оказаться недоступными.|  
|объект**Command** |Используется для определения той или иной команды, такие как SQL-запросе, должны выполняться в источнике данных.|  
|**Набор записей** объекта|Представляет весь набор записей из базовой таблицы или результаты выполнения команды. Все **записей** объекты состоят из записей (строк) и полей (столбцов).|  
|**Запись** объекта|Представляет одну строку данных, либо из **записей** или от поставщика. Эта запись может представлять собой запись в базе данных или другого типа объекта, например файла или каталога, в зависимости от поставщика.|  
|**Поток** объекта|Представляет поток двоичных или текстовых данных. Например XML-документ можно загрузить в поток команды ввода или некоторых поставщиков, возвращенные в результате запроса. Объект **поток** объект может использоваться для обработки поля или записи, содержащие эти потоки данных.|  
|**Параметр** объекта|Представляет параметр или аргумент, связанный с **команда** объекта, на основании параметризованного запроса или хранимой процедуры.|  
|**Поле** объекта|Представляет столбец данных с общим типом данных. Каждый **поле** объекта соответствует столбцу в **записей**.|  
|**Свойство** объекта|Представляет характеристику объекта ADO, определенной поставщиком. Объекты ADO, имеют два типа свойств: встроенные и динамические. Встроенные свойства — это свойства, реализованы в ADO, сразу становятся доступными для каждого нового объекта. **Свойство** объект-контейнер для динамических свойств определением базового поставщика.|  
|объект**Error** |Содержит сведения об ошибках доступа к данным, которые относятся к одной операции с участием поставщика.|  
|**Поля** коллекции|Содержит все **поле** объектов **записей** или **записи** объекта.|  
|**Свойства** коллекции|Содержит все **свойство** объектов для указанного экземпляра объекта.|  
|**Параметры** коллекции|Содержит все **параметр** объектов **команда** объекта.|  
|**Ошибки** коллекции|Содержит все **ошибка** объектов, созданных в ответ на сбой одного поставщика.|  
  
## <a name="see-also"></a>См. также  
 [Объектная модель ADO](../../../ado/reference/ado-api/ado-object-model.md)
