---
title: "Хранимая процедура проверки (службы Master Data Services) | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: non-specific
ms.reviewer: 
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 332d3c86-4440-4f12-a6cb-ffbfbccde52c
caps.latest.revision: 
author: leolimsft
ms.author: lle
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 92ca62e16c4ad20c48ee4cf487e7a2a71e9632ba
ms.sourcegitcommit: 6ac1956307d8255dc544e1063922493b30907b80
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2018
---
# <a name="validation-stored-procedure-master-data-services"></a>Проверка хранимых процедур (службы Master Data Services)
  В среде [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]проверьте версию на применение бизнес-правил ко всем элементам версии модели.  
  
 В этом разделе объясняется, как использовать хранимую процедуру **mdm.udpValidateModel** для проверки данных. Администратор веб-приложения [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] может проводить проверку в пользовательском интерфейсе. Дополнительные сведения см. в разделе [Подтверждение исправления проблемы, обнаруженной при проверке на соответствие бизнес-правилам (службы Master Data Services)](../master-data-services/validate-a-version-against-business-rules-master-data-services.md).  
  
> [!NOTE]  
>  При запуске проверки до завершения промежуточного процесса элементы, для которых этот процесс не был завершен, не будут проверены.  
  
## <a name="example"></a>Пример  
  
```  
DECLARE @ModelName nVarchar(50) = 'Customer'   
DECLARE @Model_id int   
DECLARE @UserName nvarchar(50)= 'DOMAIN\user_name'   
DECLARE @User_ID int   
DECLARE @Version_ID int   
  
SET @User_ID = (SELECT ID    
                 FROM mdm.tblUser u   
                 WHERE u.UserName = @UserName)   
SET @Model_ID = (SELECT Top 1 Model_ID   
                 FROM mdm.viw_SYSTEM_SCHEMA_VERSION   
                 WHERE Model_Name = @ModelName)   
SET @Version_ID = (SELECT MAX(ID)   
                 FROM mdm.viw_SYSTEM_SCHEMA_VERSION   
                 WHERE Model_ID = @Model_ID)  
  
EXECUTE mdm.udpValidateModel @User_ID, @Model_ID, @Version_ID, 1  
  
```  
  
## <a name="parameters"></a>Параметры  
 Параметры данной процедуры имеют следующие значения:  
  
|Параметр|Description|  
|---------------|-----------------|  
|UserID|Идентификатор пользователя.|  
|Model_ID|Идентификатор модели.|  
|Version_ID|Идентификатор версии.|  
  
## <a name="see-also"></a>См. также:  
 [Обзор: импорт данных из таблиц (службы Master Data Services)](../master-data-services/overview-importing-data-from-tables-master-data-services.md)   
 [Подтверждение исправления проблемы, обнаруженной при проверке на соответствие бизнес-правилам (службы Master Data Services)](../master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
  
