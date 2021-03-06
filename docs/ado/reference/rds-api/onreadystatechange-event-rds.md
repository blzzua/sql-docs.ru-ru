---
title: "onReadyStateChange событий (RDS) | Документы Microsoft"
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
apitype: COM
helpviewer_keywords:
- onReadyStateChange event [ADO]
ms.assetid: bf2ae3ac-bfe4-4709-b50a-ea7c282c3164
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e2641f28169199907fdfb66771a3a8e86ff1a86e
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="onreadystatechange-event-rds"></a>onReadyStateChange событий (RDS)
**OnReadyStateChange** событий вызывается всякий раз, когда значение [состояние готовности](../../../ado/reference/rds-api/readystate-property-rds.md) изменения свойств.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ больше не включаются в операционной системе Windows (в разделе Windows 8 и [руководство по Windows Server 2012 совместимости](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будут удалены в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ необходимо перенести в [службы данных WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
onReadyStateChange  
```  
  
#### <a name="parameters"></a>Параметры  
 Нет.  
  
## <a name="remarks"></a>Remarks  
 **Состояние готовности** свойство отражает ход выполнения [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) как асинхронно, он извлекает данные в его [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта. Используйте **onReadyStateChange** событий для отслеживания изменений в **состояние готовности** свойство всякий раз, когда они встречаются. Это более эффективно, чем периодической проверки наличия значения свойства.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект DataControl (служба удаленных рабочих столов)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>См. также  
 [Пример модели событий ADO (VC ++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Общие сведения об обработчике событий ADO](../../../ado/guide/data/ado-event-handler-summary.md)


