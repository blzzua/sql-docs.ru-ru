---
title: Установка времени и длительности простоя ЦП (среда SQL Server Management Studio) | Документация Майкрософт
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
- CPU [SQL Server], idle conditions
- time [SQL Server], CPU idle and duration
- duration of CPU idle [SQL Server]
- SQL Server Agent, CPU idle conditions
- idle time [SQL Server]
ms.assetid: 8647b465-d899-4cc7-9640-134a506d0a2e
caps.latest.revision: ''
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 220e70233e7e1fd4ee2dc6e8ffa502e1fc6ca9d9
ms.sourcegitcommit: 34766933e3832ca36181641db4493a0d2f4d05c6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2018
---
# <a name="set-cpu-idle-time-and-duration-sql-server-management-studio"></a>Установка времени и длительности простоя ЦП (среда SQL Server Management Studio)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

В этом разделе рассказывается о том, как задать условие простоя ЦП для сервера в [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]. Определение простоя ЦП влияет на то, как агент [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] реагирует на события. Например, предположим, определены такие условия простоя ЦП, что средняя загрузка ЦП не превышает 10% и остается на этом уровне в течение 10 минут. Тогда, если определены задания, которые должны выполняться при достижении ЦП сервера условий простоя, выполнение задания начнется, как только загрузка ЦП упадет ниже 10% и пробудет на этом уровне 10 минут. Если это задание существенно влияет на производительность сервера, определение условий простоя ЦП имеет очень большое значение.  
  
## <a name="SSMSProcedure"></a>Использование среды SQL Server Management Studio  
  
#### <a name="to-set-cpu-idle-time-and-duration"></a>Задание времени и продолжительности простоя ЦП  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]и разверните его.  
  
2.  Щелкните правой кнопкой мыши **Агент SQL Server**, выберите **Свойства**и перейдите на страницу **Дополнительно** .  
  
3.  В области **Условие бездействия ЦП**выполните следующие действия.  
  
    -   Установите флажок **Определите условие бездействия ЦП**.  
  
    -   Укажите процент загрузки ЦП в поле **Среднее время использования ЦП сократилось до** (для всех процессоров). Так задается максимальный уровень загрузки для времени простоя ЦП.  
  
    -   Укажите количество секунд в поле **И остается ниже этого уровня в течение** . Так задается промежуток времени, в течение которого должен сохраняться минимальный уровень загрузки ЦП, чтобы считать это простоем.  
  
