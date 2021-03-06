---
title: "Соединение компонентов в потоке данных | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: data-flow
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- components [Integration Services], connections
- connections [Integration Services], data flow components
ms.assetid: 70616a58-8921-4218-85bf-f3e90c5a9dbf
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 676aa85a4a8b5fcf39f198fe1b70b5b1b9f7fbfe
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="connect-components-in-a-data-flow"></a>Соединение компонентов в потоке данных
  Эта процедура описывает способ соединения выхода компонентов в потоке данных с другими компонентами того же потока.  
Поток данных пакета проектируется в области конструктора на вкладке **Поток данных** конструктора служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] . Если поток данных содержит два компонента потока данных, можно соединить их, подключив выход источника или преобразования ко входу преобразования или назначения. Соединитель компонентов потока данных называется путем.  
  
 На следующей диаграмме показан простой поток данных с компонентом источника, двумя преобразованиями, целевым компонентом и путями, которые их соединяют.  
  
 ![Data flow](../../integration-services/data-flow/media/mw-dts-08.gif "Data flow")  
  
 После соединения двух компонентов можно просматривать метаданные тех данных, которые перемещаются по пути, и свойства пути в **Редакторе пути потока данных**. Дополнительные сведения см. в статье [Integration Services Paths](../../integration-services/data-flow/integration-services-paths.md).  
  
 Также можно добавлять к путям средства просмотра данных. Средство просмотра данных дает возможность просматривать данные, перемещающиеся между компонентами потока данных во время выполнения пакета.  
  
### <a name="connect-components-in-a-data-flow"></a>Соединение компонентов в потоке данных  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]откройте проект служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , содержащий необходимый пакет.  
  
2.  Чтобы открыть пакет, дважды щелкните его в обозревателе решений.  
  
3.  Перейдите на вкладку **Поток управления** , затем дважды щелкните задачу потока данных, содержащую поток данных, в котором требуется соединить компоненты.  
  
4.  В области конструктора на вкладке **Поток данных** выберите преобразование или источник, который необходимо соединить.  
  
5.  Перетащите зеленую стрелку выхода преобразования или источника на преобразование или целевой объект. Некоторые компоненты потока данных могут иметь вывод ошибок, который можно соединять аналогичным образом.  
  
    > [!NOTE]  
    >  Некоторые компоненты могут иметь несколько выходов; следовательно, можно подключить каждый выход к отдельному преобразованию или целевому объекту.  
  
6.  Чтобы сохранить обновленный пакет, выберите пункт **Сохранить выбранные элементы** в меню **Файл** .  
  
## <a name="see-also"></a>См. также:  
 [Добавление или удаление компонента в потоке данных](../../integration-services/data-flow/add-or-delete-a-component-in-a-data-flow.md)   
 [Отладка потока данных](../../integration-services/troubleshooting/debugging-data-flow.md) [Отладка потока данных](../../integration-services/data-flow/data-flow.md)  
  
  
