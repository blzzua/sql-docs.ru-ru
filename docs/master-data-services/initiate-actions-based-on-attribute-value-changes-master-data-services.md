---
title: "Инициирование действия на основе изменений значения атрибута (службы Master Data Services) | Документы Майкрософт"
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
helpviewer_keywords:
- business rules [Master Data Services], tracking attribute changes
- change tracking groups [Master Data Services], initiating actions
ms.assetid: 5e4402ce-31db-4774-a2a1-552335f87693
caps.latest.revision: 
author: leolimsft
ms.author: lle
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f231263874e7ca54b1cb5677464e3b9a96b85190
ms.sourcegitcommit: 6ac1956307d8255dc544e1063922493b30907b80
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2018
---
# <a name="initiate-actions-based-on-attribute-value-changes-master-data-services"></a>Инициирование действия на основе значения атрибута (службы Master Data Services)
  В среде [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]для инициации действий на основе значения атрибута создаются бизнес-правила. Например, когда значение определенного атрибута изменяется, может потребоваться изменить значение, отправить уведомление или запустить внешний рабочий процесс.  
  
## <a name="prerequisites"></a>предварительные требования  
 Для выполнения этой процедуры:  
  
-   необходимо иметь разрешение на доступ к функциональной области **Администрирование системы** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](../master-data-services/administrators-master-data-services.md).  
  
-   Атрибуты должны быть в группе отслеживания изменений. Дополнительные сведения см. в разделе [Добавление атрибутов в группу отслеживания изменений (службы Master Data Services)](../master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md) .  
  
### <a name="to-create-a-business-rule-to-initiate-actions-based-on-attribute-value-changes"></a>Создание бизнес-правила для инициации действий на основе значения атрибута  
  
1.  В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Администрирование системы**.  
  
2.  В строке меню выберите **Управление** и щелкните **Бизнес-правила**.  
  
3.  На странице **Обслуживание бизнес-правил** выберите модель из списка **Модель** .  
  
4.  Выберите сущность из списка **Сущность** .  
  
5.  В списке **Тип элемента** выберите тип элемента, к которому будет применяться бизнес-правило.  
  
6.  Выберите из списка **Атрибут** атрибут или оставьте **Все**по умолчанию.  
  
7.  Нажмите **Добавить бизнес-правило**.  
  
8.  Нажмите **Изменить выбранное бизнес-правило**.  
  
9. На панели **Компоненты** разверните узел **Условия** .  
  
10. В узле **Сравнение значений** перетащите **изменено** на значок **Условия** панели **IF** .  
  
11. На панели **Изменение условия** в поле **Группа отслеживания изменений** введите номер группы отслеживания изменений, назначенный в рамках предварительных условий.  
  
12. На панели **Изменение условия** нажмите кнопку **Сохранить элемент**.  
  
13. На панели **Компоненты** разверните узел **Действия** .  
  
14. Перетащите действие на значок **Действие** панели **THEN** .  
  
15. На панели **Атрибуты** щелкните атрибут и перетащите его на значок **Выбор атрибута** панели **Изменение действия** .  
  
16. На панели **Изменение действия** заполните все необходимые поля.  
  
17. На панели **Изменение действия** нажмите кнопку **Сохранить элемент**.  
  
18. Нажмите кнопку **Назад**.  
  
19. По желанию на странице **Обслуживание бизнес-правил** дважды щелкните ячейку столбца **Имя**, **Описание**или **Уведомление** , чтобы обновить значение.  
  
    > [!NOTE]  
    >  Уведомления отправляются только для правил, включающих действие по проверке.  
  
20. Нажмите кнопку **Опубликовать бизнес-правила**.  
  
21. В диалоговом окне подтверждения нажмите кнопку **ОК**. Состояние правила изменится на **Активно**.  
  
## <a name="next-steps"></a>Next Steps  
  
-   Примените бизнес-правила к данным с помощью одной из следующих процедур:  
  
    -   [Подтверждение конкретных членов, обнаруженных при проверке на соответствие бизнес-правилам (службы Master Data Services)](../master-data-services/validate-specific-members-against-business-rules-master-data-services.md)  
  
    -   [Подтверждение исправления проблемы, обнаруженной при проверке на соответствие бизнес-правилам (службы Master Data Services)](../master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
## <a name="see-also"></a>См. также:  
 [Добавление атрибутов в группу отслеживания изменений (службы Master Data Services)](../master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md)   
 [Бизнес-правила (службы Master Data Services)](../master-data-services/business-rules-master-data-services.md)  
  
  
