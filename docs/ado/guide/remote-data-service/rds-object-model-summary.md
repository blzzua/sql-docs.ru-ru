---
title: "Сводка по модели объектов служб удаленных рабочих СТОЛОВ | Документы Microsoft"
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
- RDS objects [ADO], object model summary
- RDS object model [ADO]
ms.assetid: 909f9af7-31db-4eec-ad52-650ce74dac2f
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9423b2f6072f142336e1f36f02785b69f9efdae6
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="rds-object-model-summary"></a>Общие сведения о модели объектов служб удаленных рабочих СТОЛОВ
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ больше не включаются в операционной системе Windows (в разделе Windows 8 и [руководство по Windows Server 2012 совместимости](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будут удалены в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ необходимо перенести в [службы данных WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
|Объект|Описание|  
|------------|-----------------|  
|[RDS.DataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md)|Этот объект содержит метод для получения прокси-сервера. Прокси-сервер может быть значение по умолчанию или пользовательского сервера программы (бизнес-объекта). Программа server, могут быть вызваны в Интернет, интрасеть, локальной сети или быть локальной библиотеки динамической компоновки.<br /><br /> **DataSpace** объекта безопасные для использования.|  
|[RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)|Этот объект представляет серверной программы по умолчанию. Он реализует поведение по умолчанию служб удаленных рабочих СТОЛОВ данных выборки и обновления.<br /><br /> **DataFactory** объект не является безопасным для создания сценариев.|  
|[RDS.DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)|Этот объект можно автоматически вызывают **RDS. Пространство данных** и **RDSServer.DataFactory** объектов.<br /><br /> Этот объект можно используйте для вызова по умолчанию поведение извлечение или обновление данных служб удаленных рабочих СТОЛОВ.<br /><br /> Этот объект также предоставляет средства для визуальные элементы управления для доступа к возвращаемый **записей** объекта.<br /><br /> **DataControl** объекта безопасные для использования.|  
  
## <a name="see-also"></a>См. также  
 [Принципы работы служб удаленных рабочих СТОЛОВ](../../../ado/guide/remote-data-service/rds-fundamentals.md)   
 [Сценарии служб удаленных рабочих СТОЛОВ](../../../ado/guide/remote-data-service/rds-scenario.md)   
 [Учебник служб удаленных рабочих СТОЛОВ](../../../ado/guide/remote-data-service/rds-tutorial.md)   
 [Использование RDS и безопасность](../../../ado/guide/remote-data-service/rds-usage-and-security.md)


