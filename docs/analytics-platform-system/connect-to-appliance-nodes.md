---
title: Подключиться к узлам устройства (система платформы аналитики)
author: barbkess
ms.author: barbkess
manager: craigg
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: ''
ms.component: ''
ms.technology: mpp-data-warehouse
ms.custom: ''
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f975aa91-c816-4b29-89bf-923ab5b4abb4
caps.latest.revision: 19
ms.openlocfilehash: 9b95bc8285625170c9c9b4a91eeae99dcd3907a5
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2018
---
# <a name="connect-to-appliance-nodes"></a>Подключиться к узлам устройства
В этом разделе рассматриваются различные способы для подключения к каждому узлу в устройстве Analytics Platform System.  
  
## <a name="connecting-with-hadoop"></a>Соединение с помощью Hadoop  
Перед использованием Hadoop с SQL Server PDW следует связаться с администратором устройства для установки среды выполнения Java на SQL Server PDW. Инструкции см. в разделе [Настройка PolyBase подключения к внешним данным &#40;Analytics Platform System&#41; ](configure-polybase-connectivity-to-external-data.md) в руководстве пользователя устройства.  
  
## <a name="ConnectingToIndividualNodes"></a>Подключение к узлы устройств  
Каждый из узлов устройства осуществляется напрямую только в конкретных сценариев использования и определенных пользователем типов. В следующей таблице перечислены каждый узел устройства и сценарии, с которыми пользователи будут подключаться непосредственно к этому узлу.  
  
<!-- MISSING LINKS For information on the purpose of each node, see [Understanding SQL Server PDW &#40;SQL Server PDW&#41;](../sqlpdw/understanding-sql-server-pdw-sql-server-pdw.md).  -->  
  
|||  
|-|-|  
|**Node**|**Сценарии доступа**|  
|Узел элемента управления|Используйте веб-браузер для доступа к консоли администрирования, которая работает на узле управления. Дополнительные сведения см. в разделе [отслеживать устройства с помощью консоли администрирования &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md).<br /><br />Все клиентские приложения и средства подключения к узлу управления, независимо от того, использует соединение Ethernet или InfiniBand.<br /><br />Чтобы настроить Ethernet-подключение к узлу управления, используйте элемент управления узла IP-адрес кластера и порта **17001**. Например «192.168.0.1,17001».<br /><br />Чтобы настроить подключение InfiniBand на узел элемента управления, используйте ***appliance_domain *-SQLCTL01** и порт **17001**. С помощью ***appliance_domain *-SQLCTL01**, устройство DNS-сервер будет подключите сервер к сети InfiniBand active. Чтобы настроить сервер не является специализированным, чтобы использовать это, обратитесь [настройки сетевых адаптеров InfiniBand](configure-infiniband-network-adapters.md).<br /><br />Администратор приложения подключается к узлу элемента управления для выполнения операций управления. Например администратор приложения выполняет следующие операции с узла управления:<br /><br />Настройка система платформы аналитики с **dwconfig.exe** средство настройки.|  
|Вычислительный узел|Вычислительный узел соединения направляются узлом элемента управления. IP-адреса вычислительных узлов, никогда не вносятся в команды приложения в качестве параметров.<br /><br />Для загрузки, резервного копирования, копирования удаленной таблицы и Hadoop, SQL Server PDW отправляют и получают данные непосредственно в параллельном режиме между вычислительные узлы и узлы не устройств или серверами. Эти приложения подключаются с SQL Server PDW, подключившись к узлу управления, а затем узел элемента управления выполнен SQL Server PDW для установления связи между вычислительных узлов и не является специализированным сервером.<br /><br />Например эти операции передачи данных проходит параллельно с прямые подключения для вычислительных узлов:<br /><br />Загрузка загрузка сервера SQL Server PDW.<br /><br />Резервное копирование базы данных из SQL Server PDW на резервный сервер.<br /><br />Восстановление базы данных из резервной копии сервера SQL Server PDW.<br /><br />Запрос данных Hadoop с SQL Server PDW.<br /><br />Экспорт данных из SQL Server PDW во внешнюю таблицу Hadoop.<br /><br />Копирование таблицы SQL Server PDW в удаленной базе данных SMP SQL Server.|  
  
## <a name="connecting-to-the-ethernet-and-infiniband-networks"></a>Подключить к сети InfiniBand и Ethernet  
Удаленные серверы можно подключиться через сеть InfiniBand устройств или через сеть Ethernet. Для повышения производительности, загрузка серверов, резервное копирование серверов и серверов, получение данных с помощью **СОЗДАНИЯ УДАЛЕННОГО TABLE AS SELECT** операторов, обычно передачи данных по сети InfiniBand устройства.  
  
Настройка серверов не является специализированным принадлежать собственного клиента рабочей группы или домена и затем использовать собственную сеть клиента для подключения к этих серверов и передачи данных на них. Кроме того не является специализированным серверов, подключенных к устройству InfiniBand появится возможность передавать данные друг с другом по сети InfiniBand устройства; Будьте внимательны с данным, так как может привести к снижению производительности SQL Server PDW.  
  
Например Эта инструкция добавляет сетевые учетные данные для выполнения резервного копирования через InfiniBand резервный сервер, который InfiniBand IP-адрес 192.168.0.1. Домен устройства *mypdw*, и инструкция выполняется на сервере резервного копирования. Перед выполнением этой инструкции, необходимо заполнить свои собственные параметры.  
  
```  
sqlcmd -S "mypdw-sqlctl01,17001" -U sa -P password -I -Q "exec sp_pdw_add_network_credentials '192.168.0.1', 'mypdw\Administrator', 'password'"  
```  
  
Например команда загрузка начнется со следующими:  
  
```  
dwloader –S mypdw-SQLCTL01  
```  
  
<!-- MISSING LINKS ## See Also  
[Configure an External Windows System To Receive Remote Table Copies Using InfiniBand &#40;SQL Server PDW&#41;](../sqlpdw/configure-an-external-windows-system-to-receive-remote-table-copies-using-infiniband-sql-server-pdw.md)  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  
