---
title: "Метод iRowsetFastLoad (OLE DB) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-interfaces
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apitype: COM
helpviewer_keywords:
- IRowsetFastLoad interface
ms.assetid: d19a7097-48d9-409a-aff9-277891b7aca7
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 13801cad3857262405f70ce43bc6f321dfc5622f
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2018
---
# <a name="irowsetfastload-ole-db"></a>Метод IRowsetFastLoad (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  **IRowsetFastLoad** интерфейс обеспечивает поддержку [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] памяти операциях массового копирования. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Потребители поставщика собственного клиента OLE DB используйте интерфейс для быстрого добавления данных в существующий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицы.  
  
 Если присвоить SSPROP_ENABLEFASTLOAD значение VARIANT_TRUE для сеанса, то будет невозможно считывать данные из наборов строк, возвращаемых впоследствии в этом сеансе. Если присвоить SSPROP_ENABLEFASTLOAD значение VARIANT_TRUE, будет иметь тип IRowsetFastLoad все наборы строк, созданные для сеанса. Наборы строк iRowsetFastLoad не поддерживают функциональные возможности; Таким образом не удается прочитать данные из этих наборов строк.  
  
## <a name="in-this-section"></a>В этом разделе  
  
|Метод|Описание|  
|------------|-----------------|  
|[IRowsetFastLoad::Commit &#40; OLE DB &#41;](../../relational-databases/native-client-ole-db-interfaces/irowsetfastload-commit-ole-db.md)|Обозначает конец пакета вставляемых строк и записывает эти строки в таблицу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[IRowsetFastLoad::InsertRow &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/irowsetfastload-insertrow-ole-db.md)|Добавляет строку в набор строк для массового копирования.|  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы &#40; OLE DB &#41;](http://msdn.microsoft.com/library/34c33364-8538-45db-ae41-5654481cda93)   
 [Массовое копирование данных с помощью IRowsetFastLoad &#40; OLE DB &#41;](../../relational-databases/native-client-ole-db-how-to/bulk-copy-data-using-irowsetfastload-ole-db.md)   
 [Отправка данных BLOB на SQL SERVER с помощью IROWSETFASTLOAD и ISEQUENTIALSTREAM &#40; OLE DB &#41;](../../relational-databases/native-client-ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md)  
  
  
