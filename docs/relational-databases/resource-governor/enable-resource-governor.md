---
title: "Включение регулятора ресурсов | Документация Майкрософт"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: resource-governor
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Resource Governor, enabling
ms.assetid: 4d17af53-cf11-4ce4-aab4-deda94a49836
caps.latest.revision: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3f40ebecdafe32b519908c65ce54468858f18df3
ms.sourcegitcommit: 6b4aae3706247ce9b311682774b13ac067f60a79
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2018
---
# <a name="enable-resource-governor"></a>Активация регулятора ресурсов
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Resource Governor отключен по умолчанию. Регулятор ресурсов можно включить с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или Transact-SQL.  
  
-   **Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)  
  
-   **To enable Resource Governorn, using:**  [Object Explorer](#RGOnObjEx), [Resource Governor Properties](#RGOnProp), [Transact-SQL](#RGOnTSQL)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
 В результате включения регулятора ресурсов произойдет следующее.  
  
-   Будет выполнена функция-классификатор для новых соединений, что позволит связать их рабочую нагрузку с определенными группами рабочей нагрузки.  
  
-   Ограничения ресурсов, заданные в конфигурации регулятора ресурсов, будут соблюдены и применены.  
  
-   Запросы, которые существовали до включения регулятора ресурсов, будут испытывать воздействие всех изменений конфигурации, которые были внесены, пока регулятор ресурсов был отключен.  
  
###  <a name="LimitationsRestrictions"></a> ограничения  
 В ходе пользовательской транзакции нельзя использовать инструкцию **ALTER RESOURCE GOVERNOR** для включения регулятора ресурсов.  
  
###  <a name="Permissions"></a> Permissions  
 Для включения регулятора ресурсов требуется разрешение CONTROL SERVER.  
  
##  <a name="RGOnObjEx"></a> Включение регулятора ресурсов с использованием обозревателя объектов  
 **Включение регулятора ресурсов с помощью обозревателя объектов**  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]откройте обозреватель объектов и рекурсивно разверните узел **Управление** вплоть до узла **Регулятор ресурсов**.  
  
2.  Щелкните элемент **Resource Governor**правой кнопкой мыши и выберите команду **Включить**.  
  
##  <a name="RGOnProp"></a> Включение регулятора ресурсов с применением свойств регулятора ресурсов  
 **Включение регулятора ресурсов с использованием страницы свойств регулятора ресурсов**  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]откройте обозреватель объектов и рекурсивно разверните узел **Управление** вплоть до узла **Регулятор ресурсов**.  
  
2.  Щелкните правой кнопкой мыши элемент **Resource Governor** и выберите пункт **Свойства**, после чего откроется страница **Свойства Resource Governor** .  
  
3.  Установите флажок **Включить регулятор ресурсов** и нажмите кнопку **ОК**.  
  
##  <a name="RGOnTSQL"></a> Включение регулятора ресурсов с применением Transact-SQL  
 **Включение регулятора ресурсов с применением Transact-SQL**  
  
1.  Выполните инструкцию **ALTER RESOURCE GOVERNOR RECONFIGURE** .  
  
### <a name="example-transact-sql"></a>Пример (Transact-SQL)  
 В следующем примере показано включение регулятора ресурсов.  
  
```  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Регулятор ресурсов](../../relational-databases/resource-governor/resource-governor.md)   
 [Отключение регулятора ресурсов](../../relational-databases/resource-governor/disable-resource-governor.md)   
 [Пул ресурсов регулятора ресурсов](../../relational-databases/resource-governor/resource-governor-resource-pool.md)   
 [Группа рабочей нагрузки регулятора ресурсов](../../relational-databases/resource-governor/resource-governor-workload-group.md)   
 [Функция-классификатор регулятора ресурсов](../../relational-databases/resource-governor/resource-governor-classifier-function.md)   
 [ALTER RESOURCE GOVERNOR (Transact-SQL)](../../t-sql/statements/alter-resource-governor-transact-sql.md)  
  
  
