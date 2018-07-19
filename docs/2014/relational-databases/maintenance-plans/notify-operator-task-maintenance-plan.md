---
title: Задача уведомления оператора (план обслуживания) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.notifyoperator.f1
helpviewer_keywords:
- Notify Operator Task dialog box
ms.assetid: 39c0797c-ad2b-4591-85c9-a23a7f902895
caps.latest.revision: 32
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 323a22356efbdc63ea92e001f201e1553e82c93a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37211164"
---
# <a name="notify-operator-task-maintenance-plan"></a>Задача уведомления оператора (план обслуживания)
  Диалоговое окно **Задача уведомления оператора** используется для добавления автоматического уведомления к данному плану обслуживания. Для использования этой задачи необходимо включить и надлежащим образом настроить компонент Database Mail в MSDB в качестве базы данных обслуживания почты, а также иметь оператора агента [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с действующим адресом электронной почты.  
  
 Данная задача использует хранимую процедуру sp_notify_operator.  
  
## <a name="options"></a>Параметры  
 **Соединение**  
 Выберите соединение с сервером, которое будет использоваться для выполнения этой задачи.  
  
 **Создать**  
 Создать новое соединение с сервером для его использования при выполнении этой задачи. Диалоговое окно **Создание соединения** описано ниже.  
  
 **Уведомить операторов**  
 Указать получателя электронного письма.  
  
 **Тема сообщения уведомления**  
 Укажите текст для строки темы в сообщении уведомления.  
  
 **Текст сообщения уведомления**  
 Укажите текст сообщения уведомления.  
  
 **Просмотр T-SQL**  
 Просмотрите инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] , выполняемые для данной задачи по отношению к серверу, на основе выбранных параметров.  
  
> [!NOTE]  
>  Если количество затронутых объектов велико, построение этого отображения может занять значительное время.  
  
## <a name="new-connection-dialog-box"></a>Диалоговое окно «Создание соединения»  
 **Имя соединения**  
 Введите имя нового соединения.  
  
 **Выберите или введите имя сервера**  
 Выберите сервер для подключения при выполнении этой задачи.  
  
 **Обновить**  
 Обновите список доступных серверов.  
  
 **Введите данные для входа на сервер**  
 Укажите способ проверки подлинности на сервере.  
  
 **Использовать встроенную безопасность Windows**  
 Подключиться к экземпляру компонента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] c проверкой подлинности [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.  
  
 **Использовать указанные имя пользователя и пароль**  
 Подключиться к экземпляру компонента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] с использованием проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Этот параметр недоступен.  
  
 **Имя пользователя**  
 Укажите имя входа, используемое при проверке подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Этот параметр недоступен.  
  
 **Пароль**  
 Укажите используемый при проверке подлинности пароль. Этот параметр недоступен.  
  
## <a name="see-also"></a>См. также  
 [Database Mail](../database-mail/database-mail.md)   
 [sp_notify_operator (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-notify-operator-transact-sql)  
  
  