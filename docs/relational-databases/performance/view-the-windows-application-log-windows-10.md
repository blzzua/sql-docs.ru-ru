---
title: "Просмотр журнала приложений Windows (Windows) | Документы Майкрософт"
ms.custom: 
ms.date: 02/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- viewing logs
- application logs [SQL Server]
- logs [SQL Server], application
- monitoring Windows NT application log [SQL Server]
- Windows NT application logs [SQL Server]
- displaying logs
- monitoring [SQL Server], events
- logs [SQL Server], viewing
ms.assetid: 168a6c6e-12df-46a9-9904-55d63ca8fe14
caps.latest.revision: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 206304441aa399e25c6f63c502e4ebfe98972829
ms.sourcegitcommit: d8ab09ad99e9ec30875076acee2ed303d61049b7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/23/2018
---
# <a name="view-the-windows-application-log-windows-10"></a>Просмотр журнала приложений Windows (Windows 10)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
Когда [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] настроен на использование журнала приложений Windows, каждый сеанс [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] записывает новые события в этот журнал. В отличие от журнала ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , новый журнал приложений не создается заново каждый раз при запуске экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="view-the-windows-application-log"></a>Просмотр журнала приложений Windows  
  
1. На **панели поиска** введите **средство просмотра событий**, а затем выберите классическое приложение **Просмотр событий**.
  
2. В **средстве просмотра событий** откройте **журналы приложений и служб**.

3. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] события идентифицируются с помощью записи **MSSQLSERVER** в столбце **Источник** (именованные экземпляры обозначаются как **MSSQL$***<имя_экземпляра>*). События агента SQL Server идентифицируются записью SQLSERVERAGENT (для именованных экземпляров сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], события агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] идентифицируются с помощью **SQLAgent$**\<*имя_экземпляра*>). События службы Microsoft Search идентифицируются записью **Microsoft Search**.  
  
4. Чтобы просмотреть журнал с другого компьютера, щелкните правой кнопкой мыши элемент **Просмотр событий (локальных)**. Выберите пункт **Подключение к другому компьютеру** и заполните поля в диалоговом окне **Выбор компьютера**.  
  
5. Чтобы отображались только события [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], в меню **Вид** выберите пункт **Фильтр**. В списке **Источник событий** выберите **MSSQLSERVER**. Чтобы просмотреть только события агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , в списке **Источник события** вместо этого выберите **SQLSERVERAGENT** .  
  
6. Чтобы просмотреть дополнительные сведения о событии, дважды щелкните событие.  
  
## <a name="see-also"></a>См. также раздел  
 [Просмотр журнала ошибок SQL Server (среда SQL Server Management Studio)](../../relational-databases/performance/view-the-sql-server-error-log-sql-server-management-studio.md)  
  
  
