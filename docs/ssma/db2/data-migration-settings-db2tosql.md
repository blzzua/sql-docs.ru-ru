---
title: Параметры переноса данных (DB2ToSQL) | Документы Microsoft
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-db2
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 573e673e-a194-4cb2-9aba-aaac6e1a225c
caps.latest.revision: 4
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 538e2ea7527ee6507a3f25333daf4ee889fd8a6d
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2018
---
# <a name="data-migration-settings-db2tosql"></a>Параметры переноса данных (DB2ToSQL)
  
## <a name="data-migration-settings"></a>Параметры миграции данных  
**Параметры миграции данных** позволяет пользователю создавать пользовательские запросы для переноса данных.  
  
-   Эта вкладка доступна, когда **расширенные параметры миграции данных** равно **Показать** и будет скрыт, если задано значение **скрыть** в параметрах проекта. Дополнительные сведения о миграции параметров проекта см. в разделе [параметры проекта (миграция)](http://msdn.microsoft.com/en-us/48aaa8e6-a9cb-487d-9ba5-fc3f1c4786ae) .  
  
-   Синтаксический анализ инструкций SQL настраиваемый будут реализованы в **параметры миграции данных** вкладку таблицы узла.  
  
-   Ниже приведены два флажка, доступных в **параметры миграции данных** viz.:  
  
    1.  Усечение таблицы SQL Server  
  
    2.  Используйте настраиваемые выберите  
  
1.  **Усечение таблицы SQL Server:**  
     Этот параметр позволяет пользователю иметь четкое представление перенесенные данные в целевой базе данных.  
  
    -   По умолчанию проверяется этим текстовым полем.  
  
    -   Если это поле не установлен, данные, которые переносятся добавляется на существующие данные в целевой базе данных.  
  
2.  **Используйте настраиваемые выберите:**  
     Этот параметр позволяет пользователю изменить **выберите** присутствует инструкция (**выберите** инструкции позволяет пользователям выбирать данные, отображаемые в целевой базе данных).  
  
    1.  По умолчанию флажок снят этим текстовым полем.  
  
    2.  Если установлен флажок этим текстовым полем, то пользователи могут изменять **выберите** присутствует инструкция.  
  
Существуют две кнопки присутствует viz.:  
  
-   **Применить:** щелкните **применить** для применения параметров, которые были изменены.  
  
-   **Отмена:** щелкните **отменить** для восстановления параметров присутствует, прежде чем были внесены изменения.  
  
## <a name="see-also"></a>См. также  
[Перенос данных DB2 в SQL Server](http://msdn.microsoft.com/en-us/86cbd39f-6dac-409a-9ce1-7dd54403f84b)  
  
