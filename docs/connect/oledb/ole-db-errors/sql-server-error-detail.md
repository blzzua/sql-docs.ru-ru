---
title: Подробные сведения об ошибках SQL Server | Документы Microsoft
description: Подробные сведения об ошибках SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-errors
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, errors
- errors [OLE DB], error details
- IErrorRecords interface
- IErrorInfo interface
- OLE DB error handling, error details
- ISQLServerErrorInfo interface
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c9d23ec9cdc323f80f7a65a6221eff0ac2bdc9ef
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2018
---
# <a name="sql-server-error-detail"></a>Подробные сведения об ошибках SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Драйвер OLE DB для SQL Server определяет интерфейс, ошибка поставщика [ISQLServerErrorInfo](http://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1). Интерфейс возвращает более подробные сведения об ошибке [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и полезен, если выполнение команды или операции работы с наборами строк завершились с ошибкой.  
  
 Существует два способа для получения доступа к **ISQLServerErrorInfo** интерфейса.  
  
 Потребитель может вызвать **IErrorRecords::GetCustomerErrorObject** для получения **ISQLServerErrorInfo** указателя, как показано в следующем образце кода. (Нет необходимости для получения **ISQLErrorInfo.**) Оба **ISQLErrorInfo** и **ISQLServerErrorInfo** , пользовательские объекты ошибок OLE DB с **ISQLServerErrorInfo** является интерфейсом для получения сведений об ошибках на сервере, включая такие данные, как процедуры имени и номера строк.  
  
```  
// Get the SQL Server custom error object.  
if(FAILED(hr=pIErrorRecords->GetCustomErrorObject(  
   nRec, IID_ISQLServerErrorInfo,  
   (IUnknown**)&pISQLServerErrorErrorInfo)))  
```  
  
 Еще одним способом извлечения **ISQLServerErrorInfo** указатель является вызов **QueryInterface** метод уже получен **ISQLErrorInfo** указателя. Обратите внимание, что поскольку **ISQLServerErrorInfo** содержит надмножество информации, доступной из **ISQLErrorInfo**, имеет смысл перейти непосредственно на **ISQLServerErrorInfo** через **GetCustomerErrorObject**.  
  
 **ISQLServerErrorInfo** интерфейс предоставляет одну функцию-член [ISQLServerErrorInfo::GetErrorInfo](../../oledb/ole-db-interfaces/isqlservererrorinfo-geterrorinfo-ole-db.md). Функция возвращает указатель на структуру SSERRORINFO и указатель на буфер строк. Оба указателя ссылаются на память, потребитель должен освободить с помощью **IMalloc::Free** метод.  
  
 Элементы структуры SSERRORINFO обрабатываются потребителем следующим образом.  
  
|Член|Description|  
|------------|-----------------|  
|*pwszMessage*|Сообщение об ошибке [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Идентично строке, возвращенной в **IErrorInfo::GetDescription**.|  
|*pwszServer*|Имя экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] для сеанса.|  
|*pwszProcedure*|При необходимости, имя процедуры, в которой произошла ошибка. Пустая строка в противном случае.|  
|*lNative*|Номер собственной ошибки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Идентичен значению, возвращенному в *plNativeError* параметр **ISQLErrorInfo::GetSQLInfo**.|  
|*bState*|Состояние сообщения об ошибке [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|*bClass*|Серьезность сообщения об ошибке [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|*wLineNumber*|Если применимо, номер строки хранимой процедуры, в которой возникла ошибка.|  
  
## <a name="see-also"></a>См. также:  
 [Ошибки](../../oledb/ole-db-errors/errors.md)   
 [Инструкция RAISERROR & #40; Transact-SQL & #41;](../../../t-sql/language-elements/raiserror-transact-sql.md)  
  
  
