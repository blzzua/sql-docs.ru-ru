---
title: "Просмотр отчета о наборе элементов сбора (среда SQL Server Management Studio) | Документация Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: data-collection
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.dc.reporthistory.calendar.f1
helpviewer_keywords:
- collection sets [SQL Server], viewing reports
- reports [SQL Server], viewing collection set
ms.assetid: c3b1e791-9aa1-4bba-9622-4954568e1820
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 537ccf1648d36229ead7680826f63d081663c998
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/12/2018
---
# <a name="view-a-collection-set-report-sql-server-management-studio"></a>Просмотр отчета о наборе элементов сбора (среда SQL Server Management Studio)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
После настройки хранилища данных управления можно просмотреть отчет набора элементов сбора в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Для наборов сбора системных данных, устанавливаемых вместе с SQL Server, предоставляются отчеты. Содержимое этих отчетов:  
  
-   Сводка по использованию дискового пространства.  
  
-   Журнал статистики запросов.  
  
-   Журнал активности сервера.  
  
 Эта процедура отображает отчет для набора элементов сбора **Занято места на диске** . Аналогично можно просматривать отчеты для других наборов элементов сбора системных данных.  
  
### <a name="to-view-a-collection-set-report"></a>Просмотр отчета набора элементов сбора  
  
1.  Таблицы для отчета создаются только при первой передаче собранных данных. При попытке просмотра отчета до первой передачи данных возникнет ошибка и отчет не отобразится. Чтобы передать данные для набора элементов сбора "Занято места на диске", разверните папку **Управление** в обозревателе решений, разверните узлы **Сбор данных**и **Системные наборы сбора**, щелкните правой кнопкой мыши набор сбора **Занято места на диске** и выберите пункт **Собрать и передать**.  
  
2.  Чтобы просмотреть отчет, разверните папку **Управление** в обозревателе объектов, щелкните правой кнопкой мыши **Сбор данных**, выберите **Отчеты**и **Хранилище данных управления**, затем щелкните **Сводка по использованию дискового пространства**.  
  
    > [!NOTE]  
    >  Некоторые отчеты могут отображать кнопку календаря под временной шкалой сбора данных. Нажмите эту кнопку для доступа к **Календарю отчета сбора данных**.  
  
#### <a name="data-collection-report-calendar"></a>Календарю отчета сбора данных  
 В этом диалоговом окне можно указать дату и время начала, а также срок, за который нужно подготовить отчет о данных. Например, можно создать отчет об использовании диска на сервере в течение конкретного 12-часового периода в прошлую среду.  
  
 **Дата начала**  
 Введите начальную дату данных отчета или выберите дату в календаре.  
  
 **Время начала**  
 Введите начальное время данных отчета или укажите его, нажимая стрелки.  
  
 **Длительность**  
 Выберите временной диапазон для включения в отчет. Значение по умолчанию составляет 240 минут. Возможные значения для выбора составляют 15 мин, 60 мин, 240 мин (4 часа), 720 мин (12 часов) и 1440 мин (24 часа).  
  
## <a name="see-also"></a>См. также:  
 [Сбор данных](../../relational-databases/data-collection/data-collection.md)   
 [Пользовательские отчеты в среде Management Studio](http://msdn.microsoft.com/library/1ba3f758-f39b-4f5f-91ca-516cedc78979)   
 [Настройка хранилища данных управления (среда SQL Server Management Studio)](../../relational-databases/data-collection/configure-the-management-data-warehouse-sql-server-management-studio.md)  
  
  
