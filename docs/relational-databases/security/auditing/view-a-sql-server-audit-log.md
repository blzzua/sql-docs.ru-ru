---
title: "Просмотр журнала подсистемы аудита SQL Server | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: security
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- audits [SQL Server], viewing logs
- viewing audit logs
- logs [SQL Server], audit
ms.assetid: e8feaca0-7852-422b-895a-319b965d8d9b
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 8932e1673d49509c421f2db0e9445910dc0ebfbd
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="view-a-sql-server-audit-log"></a>Просмотр журнала подсистемы аудита SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] В этом разделе описано, как просмотреть журнал аудита SQL Server в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Безопасность](#Security)  
  
-   **Просмотр журнала подсистемы аудита SQL Server с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> Безопасность  
  
####  <a name="Permissions"></a> Разрешения  
 Требуется разрешение **CONTROL SERVER** .  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-view-a-sql-server-audit-log"></a>Просмотр журнала подсистемы аудита SQL Server  
  
1.  В обозревателе объектов раскройте папку **Безопасность** .  
  
2.  Разверните папку **Аудит** .  
  
3.  Щелкните правой кнопкой мыши журнал аудита, который необходимо просмотреть, и выберите пункт **Просмотр журналов аудита**. Открывается диалоговое окно **Просмотр файла журнала —***имя_сервера* . Дополнительные сведения см. в статье [Log File Viewer F1 Help](../../../relational-databases/logs/log-file-viewer-f1-help.md).  
  
4.  После завершения нажмите кнопку **Закрыть**.  
  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] рекомендует просматривать журнал аудита, используя средство просмотра файлов журнала. Однако при создании автоматизированной системы мониторинга информацию в файле аудита можно просматривать напрямую с помощью функции [sys.fn_get_audit_file (Transact-SQL)](../../../relational-databases/system-functions/sys-fn-get-audit-file-transact-sql.md). При чтении файла напрямую данные возвращаются в несколько ином (необработанном) формате. Дополнительные сведения см. в статье **sys.fn_get_audit_file** .  
  
## <a name="see-also"></a>См. также:  
 [Подсистема аудита SQL Server (компонент Database Engine)](../../../relational-databases/security/auditing/sql-server-audit-database-engine.md)   
 [Запись событий подсистемы аудита SQL Server в журнал безопасности](../../../relational-databases/security/auditing/write-sql-server-audit-events-to-the-security-log.md)  
  
  
