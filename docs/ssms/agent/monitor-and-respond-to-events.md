---
title: Наблюдение за событиями и их обработка | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssms-agent
ms.reviewer: ''
ms.suite: sql
ms.technology:
- tools-ssms
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- notifications [SQL Server], alert
- events [SQL Server], alerts
- alerts [SQL Server]
- notifications [SQL Server]
- events [SQL Server], automatically responding to
- administrator notifications [SQL Server Agent]
- automatic event responses
- SQL Server Agent alerts
- monitoring [SQL Server], events
- responding to events automatically
ms.assetid: f7fbe155-5b68-4777-bc71-a47637471f32
caps.latest.revision: ''
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: af58193a2ce3b8e1bd6bfb21927dfaf1c96be4b8
ms.sourcegitcommit: 34766933e3832ca36181641db4493a0d2f4d05c6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2018
---
# <a name="monitor-and-respond-to-events"></a>Наблюдение и обработка событий
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Агент производит мониторинг и автоматическую обработку различных *событий*: сообщений от [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], некоторых условий производительности и событий инструментария управления Windows (WMI).  
  
## <a name="in-this-section"></a>в этом разделе  
[Предупреждения](../../ssms/agent/alerts.md)  
Содержит сведения об именовании предупреждений и о выборе событий или условий производительности, которые обрабатываются предупреждениями.  
  
[Создание пользовательского события](../../ssms/agent/create-a-user-defined-event.md)  
Содержит сведения о том, как создать событие, отличное от стандартного для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
[Операторы](../../ssms/agent/operators.md)  
Содержит сведения о создании псевдонимов для администраторов, которым агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] рассылает уведомления при успешном или неуспешном выполнении заданий.  
  
## <a name="about-monitoring-and-responding-to-events"></a>О мониторинге и обработке событий  
Автоматические отклики на события называются *предупреждениями*. Можно назначить предупреждение на одно или несколько событий, определив, каким образом должен реагировать агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] на его возникновение. При обработке события предупреждение может отправить уведомление администратору, выполнить какое-либо задание, либо то и другое. Предупреждение может также переслать событие в журнал приложений Microsoft Windows на другом компьютере. Например, можно задать немедленное уведомление оператора при возникновении события с уровнем серьезности 19. Использование предупреждений позволяет администраторам базы данных более эффективно производить мониторинг и управление [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Агент обрабатывает только те события, для которых назначены предупреждения. Метод, применяемый агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] для мониторинга событий, зависит от их типа.  
  
Если предупреждение агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] определено для счетчика производительности, агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] непосредственно его отслеживает. Для отслеживания событий WMI агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] регистрирует запрос события WMI.  
  
Для отслеживания сообщений [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] производит мониторинг журнала приложений Windows. [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Агент может обрабатывать только те сообщения, которые появляются в этом журнале. По умолчанию SQL Server протоколирует в журнале приложений Windows следующие сообщения.  
  
-   Ошибки из таблицы sysmessages с уровнем серьезности 19 и выше.  
  
    Если необходимо протоколировать и другие ошибки из таблицы sysmessages, которые имеют уровень серьезности ниже 19, с помощью хранимой процедуры sp_altermessage можно обозначить такие ошибки как «протоколируемые всегда».  
  
-   Инструкции RAISERROR, вызываемые при использовании синтаксиса WITH LOG.  
  
    Этот способ рекомендуется для записи в журнал приложений Windows из экземпляра сервера SQL Server.  
  
-   Любые события приложения, протоколируемые при помощи процедуры xp_logevent.  
  
    > [!NOTE]  
    > Протоколирование событий приложений занимает место в журнале, в результате чего может произойти превышение его максимально допустимого размера. Чтобы предотвратить потери данных о событиях SQL Server, необходимо установить в качестве максимального размера журнала приложений Windows достаточно большое значение.  
  
После того, как [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] записал сообщение в журнал, служба агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] сравнивает его с предупреждениями, определенными администратором [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] .  
  
Независимо от источника события, служба агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] обрабатывает его, выполняя задачи, заданные в предупреждении для данного события.  
  
## <a name="see-also"></a>См. также:  
[sp_altermessage](http://msdn.microsoft.com/en-us/1b28f280-8ef9-48e9-bd99-ec14d79abaca)  
  
