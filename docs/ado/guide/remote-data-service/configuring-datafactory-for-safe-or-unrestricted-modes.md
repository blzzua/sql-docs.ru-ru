---
title: "Настройка DataFactory безопасным или неограниченный режимов | Документы Microsoft"
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
- DataFactory configuration in RDS [ADO]
ms.assetid: 8ff24805-dc7a-42ae-b600-5bad0e3f51b8
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 34b33a8b1d729a97fd246edcb4d6056954130c27
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="configuring-datafactory-for-safe-or-unrestricted-modes"></a>Настройка DataFactory безопасным или неограниченный режимов
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ больше не включаются в операционной системе Windows (в разделе Windows 8 и [руководство по Windows Server 2012 совместимости](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будут удалены в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ необходимо перенести в [службы данных WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
 По умолчанию устанавливается ADO с «safe» [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) конфигурации. Безопасный режим компонентов сервера служб удаленных рабочих СТОЛОВ означает, что выполняются следующие условия:  
  
1.  Обработчик должен иметь RDSServer.DataFactory (обязательна, параметр раздела реестра).  
  
2.  Обработчик по умолчанию, msdfmap.handler, зарегистрированных, присутствует в списке безопасный обработчик и помечаются как обработчик по умолчанию.  
  
3.  Файл Msdfmap.ini устанавливается в каталоге Windows. Этот файл необходимо настроить в соответствии с потребностями, перед использованием служб удаленных рабочих СТОЛОВ в трехуровневом режиме.  
  
 Кроме того, можно настроить неограниченное **DataFactory** установки. **DataFactory** можно использовать непосредственно, без пользовательского заголовка. Пользователи по-прежнему можно использовать пользовательский обработчик, изменив строки подключения, но он не является обязательным. Дополнительные сведения о последствиях использования **RDSServer.DataFactory** см. в разделе [обеспечение безопасности приложений служб удаленных рабочих СТОЛОВ](../../../ado/guide/remote-data-service/securing-rds-applications.md).  
  
 Для настройки записи реестра обработчика для безопасная конфигурация было предоставлено handsafe.reg файла реестра. Для запуска в безопасном режиме, запустите handsafe.reg.  
  
 После выполнения handsafe.reg, необходимо остановить и перезапустить службу World Wide Web публикации на веб-сервере, введя следующие команды в командной строке: «NET STOP W3SVC» и «W3SVC ЗАПУСТИТЕ NET».  
  
## <a name="see-also"></a>См. также  
 [Настройка DataFactory](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [Основные принципы RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)



