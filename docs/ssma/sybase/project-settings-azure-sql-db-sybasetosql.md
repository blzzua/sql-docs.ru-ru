---
title: Параметры (базы данных Azure SQL) проекта (SybaseToSQL) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-sybase
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 57002374-0d4d-43c1-b4e9-cbec02355a9c
caps.latest.revision: 4
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: cb155079bc318e9b23944fb2830a64454d3a76de
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2018
---
# <a name="project-settings-azure-sql-db--sybasetosql"></a>Параметры (базы данных Azure SQL) проекта (SybaseToSQL)
Параметры проекта базы данных SQL Azure позволяют настраивать суффикс базы данных база данных SQL Azure, добавляется в диалоговом окне соединения, а также позволяют реализовывать механизм пульса в подключении базы данных SQL Azure.  
  
В области базы данных SQL Azure доступна в **параметры проекта** и **параметры проекта по умолчанию** диалоговым окнам.  
  
-   Используйте диалоговое окно параметров проекта, чтобы задать параметры конфигурации для текущего проекта. Чтобы получить доступ к базе данных SQL Azure, на **средства** последовательно выберите пункты **параметры проекта**, нажмите кнопку **Общие** в нижней части левой панели, а затем выберите **базу данных SQL Azure**.  
  
-   Используйте диалоговое окно Параметры проекта по умолчанию, чтобы задать параметры конфигурации для всех проектов. Чтобы получить доступ к базе данных SQL Azure, на **средства** последовательно выберите пункты **параметры DefaultProject**, нажмите кнопку **Общие** в нижней части левой панели, а затем выберите **базу данных SQL Azure**.  
  
## <a name="connectivity"></a>Соединение  
**Интервал подтверждения соединения**  
  
Задает интервал времени, используемый для периодического сигнала механизм для сохранения соединения с базой данных SQL Azure в "минуты: секунды формат.  
  
**Значение по умолчанию**: "4:45 '  
  
Значение должно быть указано в am: формата ss (например, "4:45 ' или ' 0:50 ').  
  
**Azure SQL DB Server Suffix**  
  
Задает суффикс сервера базы данных SQL Azure  
  
**Значение по умолчанию**: «database.windows.net».  
  
