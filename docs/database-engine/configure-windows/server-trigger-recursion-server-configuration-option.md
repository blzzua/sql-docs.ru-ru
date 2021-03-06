---
title: "Параметр конфигурации сервера \"server trigger recursion\" | Документы Майкрософт"
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: configure-windows
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- recursive triggers [SQL Server]
- triggers [SQL Server], recursive
- server trigger recursion option
ms.assetid: da4c25f5-d04c-4951-a3db-409e71a1b468
caps.latest.revision: "24"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f22eab2dd49dc6d77d67e0ad4f4baf9d63769fa6
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2018
---
# <a name="server-trigger-recursion-server-configuration-option"></a>Параметр конфигурации сервера «server trigger recursion»
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Параметр **server trigger recursion** предназначен для указания того, допускается ли рекурсивное срабатывание триггеров уровня сервера. Если этот параметр установлен в значение 1 (включено), рекурсивное срабатывание триггеров уровня сервера разрешено. Если он установлен в значение 0 (выключено), рекурсивное срабатывание триггеров уровня сервера не допускается. Установка этого параметра в 0 (выключено) предотвращает только прямую рекурсию при срабатывании триггеров  (Чтобы отключить косвенную рекурсию, установите в значение 0 параметр **nested triggers**.) Значение по умолчанию для данного параметра равно 1 (включено). Параметр вступает в силу немедленно, без перезапуска сервера.  
  
 Дополнительные сведения см. в разделе [Создание вложенных триггеров](../../relational-databases/triggers/create-nested-triggers.md).  
  
## <a name="see-also"></a>См. также:  
 [RECONFIGURE (Transact-SQL)](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
