---
title: "Параметры проверки подписки (транзакционные подписки) | Документация Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.rep.validate.options.f1
helpviewer_keywords:
- Subscription Validation Options dialog box
ms.assetid: fd66ad1f-df01-4240-9e89-8f41bff12c1e
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 532627ae70927970c21eb69864e9025c384f8145
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/08/2018
---
# <a name="subscription-validation-options-transactional-subscriptions"></a>Параметры проверки подписки (подписки на публикацию транзакций)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Используйте диалоговое окно **Параметры проверки подписки** для определения, должна ли проверка правильности использовать только количество строк или количество строк и двоичную контрольную сумму.  
  
## <a name="options"></a>Параметры  
 **Проверить, совпадают ли числа реплицированных строк данных у подписчика и у издателя**  
 Выберите для выполнения тип проверки количества строк. Для публикаций Oracle единственный доступный параметр — это параметр **Выполнить подсчет действительного числа строк путем непосредственных запросов к таблицам**.  
  
 **Сравнить контрольные суммы для проверки правильности данных в строке**  
 Кроме подсчета количества строк на подписчике и на издателе, вычисляется контрольная сумма всех данных с помощью двоичного алгоритма подсчета контрольной суммы. Если количество строк не совпадает, то контрольная сумма не проверяется.  
  
 **Остановить агент распространителя после завершения проверки**  
 По умолчанию агент распространителя работает постоянно. Выберите этот параметр для остановки агента после выполнения проверки. Это позволяет удостовериться в успешном завершении проверки перед продолжением копирования данных к подписчику.  
  
## <a name="see-also"></a>См. также:  
 [Проверка данных на подписчике](../../relational-databases/replication/validate-data-at-the-subscriber.md)   
 [Проверка реплицированных данных](../../relational-databases/replication/validate-replicated-data.md)  
  
  
