---
title: "MSSQLSERVER_8525 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- "8525"
helpviewer_keywords:
- 8525 (Database Engine error)
ms.assetid: 297867c1-691e-4d6b-a3be-a7575015ecfa
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9a573b27b2d0a86a2e6a5d6634005f463b888c59
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver8525"></a>MSSQLSERVER_8525
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|8525|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя||  
|Текст сообщения|Распределенная транзакция завершена. Прикрепите этот сеанс к новой транзакции или транзакции NULL.|  
  
## <a name="explanation"></a>Объяснение  
Модель программирования, применяемая в координаторе распределенных транзакций с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], требует, чтобы приложения явно прикреплялись к распределенным транзакциям и исключались из них.  
  
Это происходит, если выполняются перечисленные ниже условия.  
  
-   Приложение прикреплено к распределенной транзакции.  
  
-   Транзакция завершилась фиксацией или откатом по любой причине.  
  
-   Приложение пользователя не отключилось явным образом от распределенной транзакции, либо не было явно прикреплено к новой.  
  
-   Приложение пытается выполнить транзакционную операцию, которая не является отключением от существующей распределенной транзакции или прикреплением к новой, например выполняет запрос или запускает локальную транзакцию.  
  
Состояние ошибки 1 используется в тех случаях, когда приложение выполняет операцию, создающую локальные транзакции, а состояние 2 — когда приложение пытается прикрепиться к связанному сеансу.  
  
## <a name="user-action"></a>Действие пользователя  
После того как приложение прикрепится к распределенной транзакции, оно должно явным образом отключиться от распределенной транзакции или присоединиться к другой распределенной транзакции. Это приведет к неявному отключению от предыдущей прикрепленной транзакции. Точный синтаксис отключения от распределенной транзакции или прикрепления к ней см. в руководстве по программному интерфейсу для приложения.  
  
