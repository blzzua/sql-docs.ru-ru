---
title: Включение параметра "Блокировка страниц в памяти" (Windows) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: ''
ms.component: configure-windows
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Lock Pages in Memory option
ms.assetid: cd581fbc-4747-439e-87f9-2f18e39c5bb9
caps.latest.revision: 35
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Active
ms.openlocfilehash: ad766a982b180e6fad72ec0ca3314648be81315f
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2018
---
# <a name="enable-the-lock-pages-in-memory-option-windows"></a>Включение параметра «Блокировка страниц в памяти» (Windows)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Эта политика Windows определяет, какие учетные записи могут использовать процесс для сохранения данных в физической памяти, чтобы система не отправляла страницы данных в виртуальную память на диске.  
  
> [!NOTE]  
>  Блокировка страниц в памяти может повысить производительность, если требуется подкачка памяти на диск.  
  
 Для включения этой политики для учетной записи, используемой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], воспользуйтесь средством «Групповая политика Windows» (gpedit.msc). Чтобы изменить эту политику, необходимо быть системным администратором.  
  
### <a name="to-enable-the-lock-pages-in-memory-option"></a>Включение параметра «Блокировка страниц в памяти»  
  
1.  В меню **Пуск** выберите команду **Выполнить**. В окне **Открыть** введите **gpedit.msc**.  
  
2.  В консоли **Редактор локальных групповых политик** разверните узел **Конфигурация компьютера**, затем узел **Конфигурация Windows**.  
  
3.  Разверните узлы **Настройки безопасности**и **Локальные политики**.  
  
4.  Выберите папку **Назначение прав пользователя** .  
  
     Политики будут показаны на панели подробностей.  
  
5.  На этой панели дважды щелкните параметр **Блокировка страниц в памяти**.  
  
6.  В диалоговом окне **Параметр локальной безопасности — блокировка страниц в памяти** щелкните **Добавить пользователя или группу**.  
  
7.  В диалоговом окне **Выбор: пользователи, учетные записи служб или группы** добавьте учетную запись, обладающую правами доступа для запуска sqlservr.exe.  
  
8.  Чтобы этот параметр вступил в силу, перезагрузите службу ядра СУБД SQL Server.
  
## <a name="see-also"></a>См. также:  
 [Параметры конфигурации сервера «Server Memory»](../../database-engine/configure-windows/server-memory-server-configuration-options.md)  
  
  
