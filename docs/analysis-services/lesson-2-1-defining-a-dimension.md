---
title: "Определение измерения | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 112696db-3838-4b50-91bd-d2ce5fa04ee5
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 0a6a1056c4b778dbc4cb71faa4e7b05111512285
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2018
---
# <a name="lesson-2-1---defining-a-dimension"></a>Занятие 2-1-Определение измерения
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

В следующей задаче с помощью мастера измерений создается измерение Date.  
  
> [!NOTE]  
> Приступать к этому занятию нужно только после завершения всех процедур из занятия 1.  
  
### <a name="to-define-a-dimension"></a>Определение измерения  
  
1.  В обозревателе решений (справа в Microsoft Visual Studio) щелкните правой кнопкой мыши узел **Измерения**и выберите пункт **Создать измерение**. Появится мастер измерений.  
  
2.  На странице **Вас приветствует мастер измерений** нажмите кнопку **Далее**.  
  
3.  На странице **Выбор метода создания** выберите параметр **Использовать существующую таблицу** и нажмите кнопку **Далее**.  
  
4.  Убедитесь в том, что на странице **Определение исходных сведений** выбрано представление источника данных **Adventure Works DW 2012** .  
  
5.  В списке **Основная таблица** выберите таблицу **Date**.  
  
6.  Нажмите кнопку **Далее**.  
  
7.  На странице **Выбор атрибутов измерения** установите флажки для перечисленных ниже атрибутов:  
  
    -   **Ключ даты**  
  
    -   **Full Date Alternate Key**  
  
    -   **English Month Name**  
  
    -   **Calendar Quarter**  
  
    -   **Calendar Year**  
  
    -   **Calendar Semester**  
  
8.  Для атрибута **Резервный ключ полной даты** в столбце **Тип атрибута** вместо значения **Обычный** выберите **Дата**. Для этого щелкните значение **Обычный** в столбце **Тип атрибута** . Щелкните стрелку, чтобы раскрыть список параметров. Далее щелкните **Дата** > **Календарь** > **Дата**. Нажмите кнопку **ОК**. Повторите эти действия, чтобы изменить тип атрибута в других атрибутах следующим образом:  
  
    -   **English Month Name** to **Month**  
  
    -   **Calendar Quarter** to **Quarter**  
  
    -   **Calendar Year** to **Year**  
  
    -   **Calendar Semester** to **Half Year**  
  
9. Нажмите кнопку **Далее**.  
  
10. На странице **Завершение работы мастера** на панели просмотра будет отображено измерение **Date** и его атрибуты.  
  
11. Чтобы завершить работу мастера, нажмите кнопку **Готово** .  
  
    В обозревателе решений в проекте "Учебник по службам [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] " в папке **Измерения** появится измерение Date. В центральной части окна среды разработки это измерение отображается в конструкторе измерений.  
  
12. В меню **Файл** выберите команду **Сохранить все**.  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
[Определение куба](../analysis-services/lesson-2-2-defining-a-cube.md)  
  
## <a name="see-also"></a>См. также  
[Измерения в многомерных моделях](../analysis-services/multidimensional-models/dimensions-in-multidimensional-models.md)  
[Создание измерения с помощью существующей таблицы](../analysis-services/multidimensional-models/create-a-dimension-by-using-an-existing-table.md)  
[Создание измерения с помощью мастера измерений](../analysis-services/multidimensional-models/create-a-dimension-using-the-dimension-wizard.md)  
  
  
  
