---
title: "Настройка служб удаленных рабочих СТОЛОВ в Windows 2000 | Документы Microsoft"
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
- RDS configuration [ADO], Windows 2000
ms.assetid: ef37e858-c05f-4f52-a65f-3ce6037e0d03
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 483cbe5243c9a5d2d6d63eb2b7c5f009a98cf33d
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="configuring-rds-on-windows-2000"></a>Настройка служб удаленных рабочих СТОЛОВ в Windows 2000
При возникновении затруднений при получении служб удаленных рабочих СТОЛОВ для правильной работы после обновления до Windows 2000, выполните следующие действия для устранения неполадок.  
  
1.  Убедитесь, что запущено первой службы публикации, перейдя к http:// сервера с помощью Internet Explorer. Если не удается получить доступ к веб-сервера таким образом, откройте командную строку и введите следующую команду «NET запустить W3SVC».  
  
2.  Выберите в меню Пуск выберите выполнить. Введите msdfmap.ini и нажмите кнопку ОК, чтобы открыть файл msdfmap.ini в блокноте. Проверьте в разделе [подключения по умолчанию] и если параметр доступа имеет значение NOACCESS, измените его только для чтения.  
  
3.  С помощью служебной программы RegEdit, перейдите к «HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DataFactory\HandlerInfo» и убедитесь, что **HandlerRequired** равен 0 и **DefaultHandler** — «» (значение Null, строка).  
  
     **Примечание** внести изменения в этот раздел реестра, необходимо остановить и перезапустить службу веб-публикации, введя следующие команды в командной строке: «NET STOP W3SVC» и «W3SVC ЗАПУСТИТЕ NET».  
  
4.  С помощью служебной программы RegEdit, перейдите в реестре для «HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\W3SVC\Parameters\ADCLaunch» и убедитесь, что ключ с именем **RDSServer.Datafactory**. Если нет, создайте его.  
  
5.  С помощью диспетчера служб Интернета, перейдите по умолчанию веб-сайт и просмотрите свойства MSADC виртуального корневого каталога. Проверьте каталог безопасности или IP-адрес и ограничения имен доменов. Если установлен флажок «доступ запрещен» выберите «Предоставлена».  
  
 Убедитесь, что попробуйте перезагрузить сервер, если изменения не будут устранены сначала.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ больше не включаются в операционной системе Windows (в разделе Windows 8 и [руководство по Windows Server 2012 совместимости](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будут удалены в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ необходимо перенести в [службы данных WCF](http://go.microsoft.com/fwlink/?LinkId=199565). Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ больше не включены в операционной системе Windows. Миграция приложений, использующих служб удаленных рабочих СТОЛОВ для [службы данных WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="see-also"></a>См. также  
 [Основные принципы RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)


