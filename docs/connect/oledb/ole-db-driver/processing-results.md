---
title: Обработка результатов | Документы Microsoft
description: Обработка результатов
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb-driver-for-sql-server
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, results processing
- OLE DB, processing results
- rowsets [SQL Server], results processing
- results [OLE DB Driver for SQL Server]
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6b564e696b28ca751179376f66458f7b11652ad9
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2018
---
# <a name="processing-results"></a>Обработка результатов
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Если объект набора строк создан в результате выполнения команды или его формирования непосредственно из поставщика, то пользователю необходимо иметь возможность доступа к данным набора строк и их получения.  
  
 Наборы строк являются важными объектами, включить драйвер OLE DB для SQL Server для предоставления данных в табличной форме. С концептуальной точки зрения объект набора строк — это набор строк, в котором каждая строка содержит данные столбцов. Объект набора строк предоставляет интерфейсы, такие как **IRowset** (содержит методы для последовательной выборки строк из набора строк), **IAccessor** (разрешает определение группы привязок столбцов описывает способ табличных данных привязана к переменным программы потребителей), **IColumnsInfo** (предоставляет сведения о столбцах в наборе строк), и **IRowsetInfo** (предоставляет сведения о наборе строк).  
  
 Пользователь может вызвать **IRowset::GetData** метод для извлечения строки данных из набора строк в буфер. Прежде чем **GetData** является именем, пользователь описывает буфер с помощью набора структур DBBINDING. Каждая привязка описывает способ сохранения столбца набора строк в буфере пользователя и содержит следующее.  
  
-   Порядковый номер столбца (или параметра), к которому относится привязка.  
  
-   Информация о том объекте, для которого выполняется привязка (например, значение данных, длина данных, состояние привязки).  
  
-   Информация о смещении в буфере для каждой из этих частей.  
  
-   Длина и тип значений данных, которые имеются в буфере пользователя.  
  
 При получении данных поставщик использует информацию каждой привязки, чтобы определить, куда и как получить данные из буфера пользователя. При задании значений данных в буфере пользователя поставщик использует информацию каждой привязки, чтобы определить, куда и как вернуть данные в буфер пользователя.  
  
 После задания структур DBBINDING создается метод доступа (**IAccessor::CreateAccessor**). Метод доступа представляет собой коллекцию привязок и используется для получения данных из буфера пользователя или задания значений данных в буфере.  
  
## <a name="see-also"></a>См. также  
 [Создание драйвером OLE DB для приложения SQL Server](../../oledb/ole-db-driver/creating-a-oledb-driver-for-sql-server-application.md)   
 [Разделы руководства по OLE DB](../../oledb/ole-db-how-to/ole-db-how-to-topics.md)  
  
  
