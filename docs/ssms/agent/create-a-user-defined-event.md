---
title: "Создание пользовательского события | Документация Майкрософт"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Agent alerts, user-defined events
- user-defined events [SQL Server]
- multiple language support [SQL Server], alerts
- languages [SQL Server], alerts
- severity levels [SQL Server]
- global considerations [SQL Server], alerts
- events [SQL Server], user-defined
- SQL Server Agent alerts, multiple-language environments
- alerts [SQL Server], user-defined events
- alerts [SQL Server], multiple-language environments
- custom events [SQL Server Agent]
- international considerations [SQL Server], alerts
ms.assetid: 03d71a35-97fa-4bba-aa9a-23ac9c9cf879
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 0f5aea958032436b1d9f168dafb0ad24712d0931
ms.lasthandoff: 04/11/2017

---
# <a name="create-a-user-defined-event"></a>Создание пользовательского события
Можно создать пользовательское событие, если нужно производить мониторинг событий, отличных от предопределенных системой [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Можно назначить уровень серьезности для каждого пользовательского события.  
  
> [!NOTE]  
> При использовании среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]выберите параметр **Записать журнал событий приложений Windows** для каждого сообщения определяемого пользователем события, чтобы регистрировать данные сообщения. По умолчанию после возникновения определяемые пользователем сообщения с уровнем серьезности, меньшим 19, не отправляются в журнал приложений [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows. Определяемые пользователем сообщения с уровнем серьезности, меньшим 19, не приводят к возникновению предупреждения агента SQL Server.  
  
Определяемые пользователем события должны обладать уникальными номерами сообщений. Номера сообщений для определяемых пользователем событий должны превышать 50 000. Можно определить сообщения для событий на нескольких языках. Однако перед добавлением сообщений на других языках должно быть создано сообщение об ошибке **En-US** .  
  
При управлении многоязыковым окружением [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] необходимо создать пользовательские сообщения на всех поддерживаемых языках. Например, если создается новое сообщение события, которое будет использоваться и на английском, и на немецком сервере, то необходимо использовать один и тот же номер сообщения и один и тот же уровень серьезности для обоих серверов, но на каждый из них назначить сообщение на соответствующем языке.  
  
В следующих задачах приводятся сведения о том, как создавать пользовательские события и реагирующие на них предупреждения.  
  
**Создание предупреждения по номеру сообщения**  
  
-   [Среда Среда SQL Server Management Studio](../../ssms/agent/create-an-alert-using-an-error-number.md)  
  
-   [Transact-SQL](http://msdn.microsoft.com/en-us/d9b41853-e22d-4813-a79f-57efb4511f09)  
  
**Создание предупреждения по уровню серьезности**  
  
-   [Среда Среда SQL Server Management Studio](../../ssms/agent/create-an-alert-using-severity-level.md)  
  
-   [Transact-SQL](http://msdn.microsoft.com/en-us/d9b41853-e22d-4813-a79f-57efb4511f09)  
  
**Определение ответа на предупреждение**  
  
-   [SQL Server Management Studio](../../ssms/agent/define-the-response-to-an-alert-sql-server-management-studio.md)  
  
-   [Transact-SQL](http://msdn.microsoft.com/en-us/0525e0a2-ed0b-4e69-8a4c-a9e3e3622fbd)  
  
**Создание сообщения об ошибке пользовательского события**  
  
-   [Transact-SQL](http://msdn.microsoft.com/en-us/54746d30-f944-40e5-a707-f2d9be0fb9eb)  
  
**Изменение сообщения об ошибке пользовательского события**  
  
-   [Transact-SQL](http://msdn.microsoft.com/en-us/1b28f280-8ef9-48e9-bd99-ec14d79abaca)  
  
**Удаление сообщения об ошибке пользовательского события**  
  
-   [Transact-SQL](http://msdn.microsoft.com/en-us/17287a15-cdde-43d1-bb18-9f920bc15db8)  
  
**Отключение или повторное включение предупреждения**  
  
-   [Среда Среда SQL Server Management Studio](../../ssms/agent/disable-or-reactivate-an-alert.md)  
  
-   [Transact-SQL](http://msdn.microsoft.com/en-us/4bbaeaab-8aca-4c9e-abc1-82ce73090bd3)  
  
## <a name="see-also"></a>См. также:  
[Хранимая процедура Хранимая процедура sp_update_alert (Transact-SQL)](http://msdn.microsoft.com/en-us/4bbaeaab-8aca-4c9e-abc1-82ce73090bd3)  
  
