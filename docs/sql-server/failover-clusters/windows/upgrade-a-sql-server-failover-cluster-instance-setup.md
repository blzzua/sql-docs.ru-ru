---
title: "Обновление экземпляра отказоустойчивого кластера SQL Server (программа установки) | Документация Майкрософт"
ms.custom: 
ms.date: 01/22/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: failover-clusters
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- upgrading clusters
- clusters [SQL Server], upgrading
- failover clustering [SQL Server], creating clusters
- clusters [SQL Server], creating
- failover clustering [SQL Server], upgrading
ms.assetid: ea8b7d66-e5a1-402f-9928-8f7310e84f5c
caps.latest.revision: "63"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 9e35eab411af665d7758d76fa7e9f3f1353be7ce
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2017
---
# <a name="upgrade-a-sql-server-failover-cluster-instance-setup"></a>Обновление экземпляра отказоустойчивого кластера SQL Server (программа установки)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Отказоустойчивый кластер [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] можно обновить до отказоустойчивого кластера [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с помощью пользовательского интерфейса установки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] или из командной строки.  
  
 Для локальных установок программу установки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] нужно запускать с правами администратора. Если [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] устанавливается с удаленного общего ресурса, необходимо использовать учетную запись домена, у которой есть разрешения на чтение на этом удаленном ресурсе.  
  
 Перед обновлением см. раздел [Обновление экземпляра отказоустойчивого кластера SQL Server](../../../sql-server/failover-clusters/windows/upgrade-a-sql-server-failover-cluster-instance.md).  
  
##  <a name="UpgradeSteps"></a> Обновление отказоустойчивого кластера [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]  
  
#### <a name="to-upgrade-a-includessnoversionincludesssnoversion-mdmd-failover-cluster"></a>Обновление отказоустойчивого кластера [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]  
  
1.  На установочном носителе [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] для выпуска, соответствующего обновляемому выпуску, дважды щелкните файл setup.exe в корневой папке. Может появиться запрос на установку обязательных компонентов, если они не установлены ранее.  
  
2.  После установки необходимых компонентов мастер установки запустит центр установки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Чтобы обновить существующий экземпляр служб [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], выберите свой экземпляр.  
  
3.  Если требуются файлы поддержки программы установки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , программа установки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] установит их. Если будет предложено перезагрузить компьютер, перезапустите его перед продолжением.  
  
4.  Средство проверки конфигурации системы запускает операцию обнаружения на компьютере. Чтобы продолжить, [!INCLUDE[clickOK](../../../includes/clickok-md.md)].  
  
5.  На странице «Ключ продукта» введите ключ идентификатора продукта (PID) для выпуска новой версии, соответствующий выпуску старой версии продукта. Например, чтобы обновить отказоустойчивый кластер выпуска Enterprise, нужно ввести ключ PID для выпуска [!INCLUDE[ssEnterprise](../../../includes/ssenterprise-md.md)]. Чтобы продолжить, нажмите кнопку **Далее** . Не забудьте, что используемый для обновления отказоустойчивого кластера ключ PID должен быть согласован во всех узлах данного экземпляра отказоустойчивого кластера [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
6.  На странице «Условия лицензии» прочтите лицензионное соглашение, а затем установите флажок, подтверждая принятие условий соглашения. Чтобы помочь в улучшении [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], можно также включить параметр наблюдения за использованием компонентов и отправлять отчеты в [!INCLUDE[msCoName](../../../includes/msconame-md.md)]. **Чтобы продолжить, нажмите кнопку "Далее"**. Чтобы выйти из программы установки, нажмите кнопку **Отмена**.  
  
7.  На странице «Выбор экземпляра» укажите экземпляр [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , который необходимо обновить до [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. **Чтобы продолжить, нажмите кнопку "Далее"**.  
  
8.  На странице Выбор компонентов компоненты для обновления предварительно выбраны. После выбора компонента описание его группы отображается в правой панели окна. Не забудьте, что во время обновления невозможно ни изменять обновляемые компоненты, ни добавлять их. Инструкции по добавлению компонентов к обновляемому экземпляру [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] после завершения обновления см. в разделе [Добавление компонентов в экземпляр SQL Server 2016 (программа установки)](../../../database-engine/install-windows/add-features-to-an-instance-of-sql-server-2016-setup.md).  
  
     Требования для выбранных компонентов показаны на правой панели. Программа установки SQL Server установит обязательный компонент, который еще не был установлен, в шаге установки, описанном ниже в данной процедуре. Чтобы сэкономить время, следует предварительно установить эти обязательные компоненты на каждом узле.  
  
9. На странице «Конфигурация экземпляра» поля автоматически заполняются из старого экземпляра. Можно указать новое значение идентификатора экземпляра.  
  
     **Идентификатор экземпляра** — по умолчанию в качестве идентификатора экземпляра используется его имя. Предназначен для идентификации каталогов установки и разделов реестра для данного экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Действует как для экземпляров по умолчанию, так и для именованных экземпляров. Для экземпляра по умолчанию именем и идентификатором экземпляра является «MSSQLSERVER». Если необходимо, чтобы идентификатор экземпляра отличался от значения по умолчанию, установите флажок **Идентификатор экземпляра** и введите значение. При переопределении значения по умолчанию необходимо указывать один и тот же идентификатор экземпляра для обновляемого экземпляра на всех узлах отказоустойчивого кластера. Значение идентификатора экземпляра должно быть идентичным для всех узлов.  
  
     **Обнаруженные экземпляры и компоненты** — в сетке показаны все установленные экземпляры [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] на компьютере, на котором запущена программа установки. **Чтобы продолжить, нажмите кнопку "Далее"**.  
  
10. На странице «Требования к свободному месту на диске» показан расчет требуемого пространства на диске для выбранных компонентов, а также приведено сравнение требуемого и имеющегося свободного места на компьютере, на котором работает программа установки.  
  
11. На странице «Обновление полнотекстового поиска» укажите параметры обновления для обновляемых баз данных. Дополнительные сведения см. в разделе [Параметры обновления полнотекстового поиска](http://msdn.microsoft.com/library/16c9376b-5fbb-4495-a429-06a2493849c9).  
  
12. На странице **Отчеты об ошибках** укажите сведения, которые будут отправлены в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] и помогут улучшить [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. По умолчанию параметры создания отчетов об ошибках включены.  
  
13. Перед началом операции обновления средство проверки конфигурации выполнится еще раз для оценки конфигурации компьютера с выбранными компонентами [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
14. На странице «Отчет по обновлению кластера» отображается список узлов экземпляра отказоустойчивого кластера и сведения о версии экземпляра для компонентов [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] на каждом узле. Также отображается состояние скрипта базы данных и состояние скрипта репликации. Кроме того, на этой странице выводятся информационные сообщения о том, что произойдет при нажатии кнопки **Далее**. В программе установки отображается поведение при отработке отказа после нажатия кнопки **Далее**в зависимости от количества уже обновленных узлов отказоустойчивого кластера и общего числа узлов. Кроме того, если еще не установлены необходимые компоненты, программа предупреждает о возможных простоях.  
  
15. На странице готовности к обновлению отображается представление параметров установки в виде дерева, заданных в программе установки. Чтобы продолжить, нажмите кнопку **Обновить**. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Программа установки вначале устанавливает требуемые компоненты для выбранных средств, затем устанавливает сами средства.  
  
16. В ходе обновления на странице выполнения установки отображается информация о состоянии, так что во время выполнения программы установки можно наблюдать за ходом обновления на текущем узле.  
  
17. По завершении обновления текущего узла на странице «Отчет по обновлению кластера» отображаются сведения о состоянии обновления для всех узлов отказоустойчивого кластера, компонентов на каждом узле отказоустойчивого кластера, а также информация об их версиях. Подтвердите отображенную информацию о версии и продолжайте обновление оставшихся узлов. В случае отработки отказа с переходом на обновленные узлы информация об этом будет также отображена на странице состояния. Эти данные можно также проверить в оснастке Windows «Администрирование кластера».  
  
18. После обновления на завершающей странице будет приведена ссылка на файл сводного журнала установки и даны другие важные примечания. Чтобы завершить процесс установки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , нажмите кнопку **Готово**.  
  
19. Если будет предложено перезагрузить компьютер, выполните перезагрузку. После завершения установки важно прочитать сообщение мастера установки. Дополнительные сведения о файлах журналов установки см. в разделе [Просмотр и чтение файлов журналов программы установки SQL Server](../../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md).  
  
20. Чтобы завершить процесс обновления, повторите эти шаги на всех остальных узлах отказоустойчивого кластера [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
## <a name="to-upgrade-a-includessnoversionincludesssnoversion-mdmd-multi-subnet-failover-cluster"></a>Обновление отказоустойчивого кластера с несколькими подсетями [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]  
  
#### <a name="to-upgrade-to-a-includessnoversionincludesssnoversion-mdmd-multi-subnet-failover-cluster-existing-includessnoversionincludesssnoversion-mdmd-cluster-is-a-non-multi-subnet-cluster"></a>Обновление до отказоустойчивого кластера [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с несколькими подсетями (Существующий кластер [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] не является кластером с несколькими подсетями).  
  
1.  Выполните действия, перечисленные выше, чтобы обновить кластер до [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
2.  С помощью действия установки AddNode добавьте узел из другой подсети и подтвердите значение зависимости OR для ресурса IP-адреса на странице **Конфигурация сети кластера**. Дополнительные сведения см. на странице [Добавление и удаление узлов в отказоустойчивом кластере SQL Server (настройка)](../../../sql-server/failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md).  
  
#### <a name="to-upgrade-a-multi-subnet-cluster-currently-using-stretch-v-lan"></a>Обновление кластера с несколькими подсетями, использующего технологию распределенных виртуальных ЛС.  
  
1.  Выполните действия, перечисленные выше, чтобы обновить кластер до [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
2.  Измените параметры сети, чтобы переместить удаленный узел в другую подсеть.  
  
3.  С помощью средства управления отказоустойчивым кластером Windows добавьте новый IP-адрес для новой подсети и задайте значение OR для зависимости ресурса IP-адреса.  
  
## <a name="next-steps"></a>Следующие шаги  
 После обновления до [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]выполните следующие задачи.  
  
-   [Завершение обновления ядра СУБД](../../../database-engine/install-windows/complete-the-database-engine-upgrade.md)  
  
-   [Изменение режима совместимости базы данных и использование хранилища запросов](../../../database-engine/install-windows/change-the-database-compatibility-mode-and-use-the-query-store.md)  
  
-   [Использование преимуществ новых функций SQL Server 2016](http://msdn.microsoft.com/library/d8879659-8efa-4442-bcbb-91272647ae16)  
  
## <a name="see-also"></a>См. также:  
 [Обновление экземпляра отказоустойчивого кластера SQL Server](../../../sql-server/failover-clusters/windows/upgrade-a-sql-server-failover-cluster-instance.md)   
 [Просмотр и чтение файлов журналов программы установки SQL Server](../../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)   
 [Добавление компонентов в экземпляр SQL Server 2016 (программа установки)](../../../database-engine/install-windows/add-features-to-an-instance-of-sql-server-2016-setup.md)  
  
  
