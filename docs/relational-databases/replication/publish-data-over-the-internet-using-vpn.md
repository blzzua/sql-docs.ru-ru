---
title: "Публикация данных через Интернет с помощью виртуальных частных сетей | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VPNs [SQL Server replication]
- Web publishing [SQL Server replication], VPNs
- Internet [SQL Server replication], VPNs
ms.assetid: 9ffb6546-9973-4574-aaa0-8fe0017e3601
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 760dd1341cc9a6aab18644b3777b007519322c7b
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/08/2018
---
# <a name="publish-data-over-the-internet-using-vpn"></a>Публикация данных через Интернет с помощью виртуальных частных сетей
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Обеспечивая защищенный обмен данными, технология виртуальных частных сетей (Virtual Private Networking, VPN) предоставляет работающим дома пользователям, филиалам компании, удаленным пользователям и другим компаниям возможность подключения к корпоративной сети через Интернет. Пользователи могут использовать проверку подлинности Windows, как если бы они находились в локальной сети. Репликации [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] всех типов могут реплицировать данные через виртуальную частную сеть, но для репликации слиянием необходимо предусмотреть веб-синхронизацию, так как в этом случае применение виртуальной частной сети не требуется. Дополнительные сведения см. в статье [Web Synchronization for Merge Replication](../../relational-databases/replication/web-synchronization-for-merge-replication.md).  
  
 Виртуальная частная сеть включает клиентское программное обеспечение, так что компьютеры подключаются к программному обеспечению выделенного компьютера или сервера через Интернет (или, в особых случаях, даже через корпоративную сеть). При желании можно использовать как шифрование с обеих сторон, так и пользовательские методы проверки подлинности. Соединение с виртуальной частной сетью через Интернет логически функционирует как соединение глобальной сети (WAN) между сайтами.  
  
 Виртуальная частная сеть связывает компоненты сети с помощью другой сети. Чтобы подключиться, пользователь осуществляет связь через Интернет или иную общедоступную сеть, используя протоколы, такие как [!INCLUDE[msCoName](../../includes/msconame-md.md)] PPTP (Point-to-Point Tunneling Protocol) или L2TP (Layer Two Tunneling Protocol). Этот процесс предоставляет такую же безопасность и возможности, которые были доступны ранее только в частных сетях. Протокол PPTP доступен в операционных системах Microsoft Windows NT 4.0 и [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 2000 (или более поздних версиях); протокол L2TP доступен в операционных системах Windows 2000 (или более поздних версиях).  
  
 Промежуточная инфраструктура маршрутизации Интернета остается невидимой для пользователя и ему кажется, будто данные посылаются через выделенную частную линию. С точки зрения пользователей виртуальная частная сеть представляет собой двухточечное соединение между компьютером пользователя и корпоративным сервером.  
  
 После того как у удаленного клиента выполнена настройка для подключения с использованием виртуальной частной сети и клиент, имеющий доступ в Интернет, зарегистрировался в корпоративной сети, можно настроить репликацию так, будто удаленный пользователь напрямую подключен к локальной сети. По соображениям безопасности можно предоставить доступ к разным сетевым ресурсам для пользователей, подключающихся через виртуальную частную сеть и для тех, кто подключается непосредственно к локальной сети.  
  
 Дополнительные сведения о настройке виртуальных частных сетей см. в документации по [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.  
  
## <a name="see-also"></a>См. также:  
 [Репликация через Интернет](../../relational-databases/replication/replication-over-the-internet.md)  
  
  
