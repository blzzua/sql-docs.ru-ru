---
title: Сетевая конфигурация устройства (система платформы аналитики)
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
ms.assetid: 8e2b9abe-963d-479b-a4a7-1739fcb3e249
caps.latest.revision: 27
ms.openlocfilehash: fcee7a037b3fbffc56e923f9be875074628398c3
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2018
---
# <a name="appliance-network-configuration"></a>Сетевая конфигурация устройства
SQL Server PDW appliance строится и настроен исправление набор IP-адресов на протяжении всех серверов и соответствующие устройства из фабричной установки Оборудования. При доставке устройства необходимо изменить конфигурацию IP-адрес внешнего (Ethernet) обращаться для соответствия требованиям центра данных определенного клиента.  
  
> [!NOTE]  
> PDW V1 требуется 8 внешние IP (*клиента с выходом*) адреса для обеспечения возможности внешнего подключения для каждого элемента управления в стойке узлов. 2012 PDW (V2) расширенного сетевого взаимодействия, предоставляя все компоненты устройства извне через IP-адресов. Такой подход обеспечивает надежность уменьшения затрат и повысить гибкость и расширяет возможности перемещения данных, загрузки данных и интеграции Hadoop. Число IP-адресов, которые требуется зависит от числа узлов в устройстве, а также наличие функций, таких как HDInsight. Для размещения этого большего размера блока IP-адреса, клиент должен настроить отдельную подсеть для PDW. В этой подсети будет достаточно адресного пространства (до 250 адреса) для размещения компонентов до 5 стеллажей PDW.  
  
**Сетевая конфигурация** страница позволяет просматривать внешний параметры сети для узлов на устройстве Analytics Platform System. Эта страница доступна только для чтения.  
  
![DWConfig Appliance Network](./media/appliance-network-configuration/SQL_Server_PDW_DWConfig_ApplTopNetwork.png "SQL_Server_PDW_DWConfig_ApplTopNetwork")  
  
## <a name="to-update-the-network-configuration-on-your-appliance"></a>Чтобы обновить конфигурацию сети на устройстве  
Изменить, изменив IP-адреса домена структуры, рабочая нагрузка домена и доменов HDInsight **AplianceInfo.xml** файл и затем запустить программу установки. Эта операция выполняется в автономном режиме. HDInsight (при его наличии) и PDW областей останавливается автоматически при изменении IP-адреса.  
  
> [!NOTE]  
> Имена доменов предоставляется во время установки и указано не более 6 буквенно-цифровые символы, начиная с буквы. Часто систему именования создает структуры домена, начиная с F, начиная с P домен рабочей нагрузки PDW и домен HDInsight, начиная с з. Этот формат, что служба выполняется во всех разделах файла справки, но не является обязательным. <!-- MISSING LINKS For more information about the domain structure, see [PDW Domain Security &#40;SQL Server PDW&#41;](../sqlpdw/pdw-domain-security-sql-server-pdw.md) and [Understanding the Security Model of the HDInsight Region &#40;Analytics Platform System&#41;](../hdinsight/understanding-the-security-model-of-the-hdinsight-region.md)  -->  
  
#### <a name="to-change-the-ip-addresses-of-the-analytics-platform-system"></a>Чтобы изменить IP-адреса система платформы аналитики  
  
1.  С помощью **удаленного рабочего стола** приложения, подключиться к **HST01** с помощью учетной записи администратора домена рабочей нагрузки.  
  
2.  На узле HST01 открыть файл info устройства в **c:\pdwinst\media\AplianceInfo.xml**.  
  
    > [!NOTE]  
    > Если файл отсутствует, может потребоваться создать новый файл.  
  
3.  При необходимости обновите значения IP-адреса Ethernet и сохраните файл.  
  
4.  В окне командной строки выполните следующую команду установки для обновления IP-адреса для региона PDW, с помощью P/F-H доменные имена и пароли администратора.  
  
    ```  
    c:\pdwinst\media\setup.exe /action="ConfigureEthernet" /DomainAdminPassword="<password>" /ApplianceInfoFile="C:\PDWINST\media\ApplianceInfo.xml"  
    ```  
  
## <a name="manufacturer-references"></a>Изготовитель ссылки  
Дополнительные сведения о Dell устройств см. в разделе:  
  
-   Инструкции PowerConnect Switch [Dell PowerConnect 6200 системная CLI ссылки руководства](http://downloads.dell.com/Manuals/all-products/esuprt_ser_stor_net/esuprt_powerconnect/powerconnect-6224f_Reference%20Guide_en-us.pdf)  
  
-   iDRAC/BMC [интеграции Dell удаленного доступа контроллера 7 (iDRAC7) 1.30.30 версия руководство](http://downloads.dell.com/Manuals/all-products/esuprt_electronics/esuprt_software/esuprt_remote_ent_sys_mgmt/integrated-dell-remote-access-cntrllr-7-v1.30.30_User%27s%20Guide_en-us.pdf?c=us&l=en&cs=555&s=biz)  
  
-   PDU **Dell измеряемые стойку PDU**`ftp://ftp.dell.com/Manuals/all-products/esuprt_ser_stor_net/esuprt_rack_infrastructure/dell-metered-pdu-led_User's%20Guide_en-us.pdf`  
  
## <a name="see-also"></a>См. также  
[Запустите диспетчер конфигурации &#40;система платформы аналитики&#41;](launch-the-configuration-manager.md)  
  
