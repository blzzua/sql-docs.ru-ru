---
title: "MSSQL_ENG021331 | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSSQL_ENG021331 error
ms.assetid: 9acd75d9-fda1-44cd-ba17-20295ad53ea0
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6e0cf9ca23205a55e9a708f7d224cbb838dbf0c3
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/08/2018
---
# <a name="mssqleng021331"></a>MSSQL_ENG021331
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="message-details"></a>Сведения о сообщении  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|21331|  
|Источник события|MSSQLSERVER|  
|Компонент|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Символическое имя||  
|Текст сообщения|Не удалось скопировать файл пользовательского скрипта на распространитель.(%ls)|  
  
## <a name="explanation"></a>Объяснение  
 Данная ошибка может возникнуть, когда подписка инициализирована вручную, и скрипты, сформированные репликацией или заданные в команде репликации, не могут быть сохранены в указанный каталог. Ошибка может быть вызвана недостатком разрешений: если инициализация подписки выполняется без применения моментального снимка, то учетная запись, от имени которой выполняется служба [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на издателе, должна обладать разрешением на запись в папку моментальных снимков распространителя.  
  
## <a name="user-action"></a>Действие пользователя  
 Проверьте правильность указанного пути к папке моментальных снимков, а также убедитесь, что учетная запись, под которой работает служба [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя, обладает всеми необходимыми разрешениями.  
  
## <a name="see-also"></a>См. также:  
 [Указание расположения моментальных снимков по умолчанию (SQL Server Management Studio)](../../relational-databases/replication/specify-the-default-snapshot-location-sql-server-management-studio.md)   
 [Справочник по ошибкам и событиям (репликация)](../../relational-databases/replication/errors-and-events-reference-replication.md)   
 [Инициализация транзакционной подписки без моментального снимка](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md)  
  
  
