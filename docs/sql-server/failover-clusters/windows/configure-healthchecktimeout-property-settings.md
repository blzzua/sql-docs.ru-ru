---
title: "Настройка параметров свойства HealthCheckTimeout | Документация Майкрософт"
ms.custom: 
ms.date: 03/09/2017
ms.prod: failover-clusters
ms.prod_service: sql-non-specified
ms.service: database-engine
ms.component: 
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3bbeb979-e6fc-4184-ad6e-cca62108de74
caps.latest.revision: "31"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c3f23375e6ba7a87cd4fa4c0a29f2c61f72e81b4
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="configure-healthchecktimeout-property-settings"></a>Настройка параметров свойства HealthCheckTimeout
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Параметр HealthCheckTimeout используется для задания временного интервала (в миллисекундах) ожидания библиотекой ресурсов SQL Server данных, возвращаемых хранимой процедурой [sp_server_diagnostics](../../../relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql.md), до появления сообщения о том, что экземпляр отказоустойчивого кластера AlwaysOn SQL Server (FCI) не отвечает. Изменения, внесенные в параметры времени ожидания, вступают в силу немедленно и не требуют перезапуска ресурса SQL Server.  
  
-   **Перед началом:**  [Ограничения](#Limits), [Безопасность](#Security)  
  
-   **Настройка параметра HealthCheckTimeout с помощью следующих средств:**  [PowerShell](#PowerShellProcedure), [диспетчер отказоустойчивого кластера](#WSFC), [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Limits"></a> Ограничения  
 Значение по умолчанию для этого свойства составляет 30 000 миллисекунд (30 секунд). Минимальное значение равно 15 000 миллисекундам (15 секундам).  
  
###  <a name="Security"></a> Безопасность  
  
####  <a name="Permissions"></a> Разрешения  
 Требует разрешения ALTER SETTINGS и VIEW SERVER STATE.  
  
##  <a name="PowerShellProcedure"></a> Использование PowerShell  
  
##### <a name="to-configure-healthchecktimeout-settings"></a>Настройка параметров HealthCheckTimeout  
  
1.  Запустите повышенный режим Windows PowerShell с помощью команды **Запуск от имени администратора**.  
  
2.  Импортируйте модуль **FailoverClusters** для включения командлетов кластера.  
  
3.  C помощью командлета **Get-ClusterResource** найдите ресурс [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , а затем используйте командлет **Set-ClusterParameter** , чтобы настроить свойство **HealthCheckTimeout** для экземпляра отказоустойчивого кластера.  
  
> [!TIP]  
>  Каждый раз при открытии нового окна Powershell потребуется импортировать модуль **FailoverClusters** .  
  
### <a name="example-powershell"></a>Пример (PowerShell)  
 В следующем примере демонстрируется изменение параметра HealthCheckTimeout ресурса [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] «`SQL Server (INST1)`» на 60 000 миллисекунд.  
  
```powershell  
Import-Module FailoverClusters  
  
$fci = "SQL Server (INST1)"  
Get-ClusterResource $fci | Set-ClusterParameter HealthCheckTimeout 60000  
  
```  
  
### <a name="related-content-powershell"></a>См. также (PowerShell)  
  
-   [Кластеризация и высокая доступность](http://blogs.msdn.com/b/clustering/archive/2009/05/23/9636665.aspx) (блог группы отказоустойчивой кластеризации и балансировки сетевой нагрузки)  
  
-   [Приступая к работе с Windows PowerShell в отказоустойчивом кластере](http://technet.microsoft.com/library/ee619762\(WS.10\).aspx)  
  
-   [Команды ресурса кластера и соответствующие командлеты Windows PowerShell](http://msdn.microsoft.com/library/ee619744.aspx#BKMK_resource)  
  
##  <a name="WSFC"></a> Использование оснастки «Диспетчер отказоустойчивости кластеров»  
 **Для настройки параметров HealthCheckTimeout**  
  
1.  Откройте оснастку «Диспетчер отказоустойчивости кластеров»  
  
2.  Раскройте узел **Службы и приложения** и выберите требуемый кластер FCI.  
  
3.  Щелкните правой кнопкой мыши **Ресурс SQL Server** в разделе **Другие ресурсы** и выберите из контекстного меню пункт **Свойства** . Откроется диалоговое окно **Свойства** ресурсов SQL Server.  
  
4.  Перейдите на вкладку **Свойства** , введите желаемое значение свойства **HealthCheckTimeout** и нажмите кнопку **ОК** , чтобы применить изменение.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 С помощью инструкции [ALTER SERVER CONFIGURATION](../../../t-sql/statements/alter-server-configuration-transact-sql.md)[!INCLUDE[tsql](../../../includes/tsql-md.md)] вы можете задать значение свойства HealthCheckTimeOut.  
  
###  <a name="TsqlExample"></a> Пример (Transact-SQL)  
 В следующем примере для параметра HealthCheckTimeout устанавливается значение, равное 15 000 миллисекунд (15 секунд).  
  
```  
ALTER SERVER CONFIGURATION   
SET FAILOVER CLUSTER PROPERTY HealthCheckTimeout = 15000;  
```  
  
## <a name="see-also"></a>См. также:  
 [Политика отработки отказа для экземпляров отказоустойчивого кластера](../../../sql-server/failover-clusters/windows/failover-policy-for-failover-cluster-instances.md)  
  
  
