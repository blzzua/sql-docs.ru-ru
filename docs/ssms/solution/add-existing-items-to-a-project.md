---
title: "Добавление существующих элементов в проект | Документация Майкрософт"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-solutions
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [SQL Server Management Studio], item additions
- adding project items
ms.assetid: 084b3879-e96b-45a7-b421-6a4b0db2b92b
caps.latest.revision: "5"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 35155a319dfe1e1565a7e6b1c0ac435b952bd7de
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/17/2018
---
# <a name="add-existing-items-to-a-project"></a>Добавление существующих элементов в проект
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] Добавление новых элементов в проект с целью расширения функциональности приложений. Существующий элемент может быть запросом или произвольным файлом. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] имеет два типа проектов: проект скрипта [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] и проект скрипта служб Analysis Services. Тип проекта определяет типы файлов запросов, которые могут быть добавлены в проект. Например, запрос [!INCLUDE[tsql](../../includes/tsql_md.md)] (SQL-файл) можно добавить в проект скрипта [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] , но нельзя добавить в проект скрипта служб Analysis Services. О том, как связать расширения файлов с типами проектов, см. в разделе [Практическое руководство. Связывание расширения файла с редактором кода](http://msdn.microsoft.com/en-us/193630f4-93de-4950-8f36-68702531f925).  
  
### <a name="to-add-an-existing-query-or-a-miscellaneous-file-to-a-project"></a>Добавление существующего запроса или произвольного файла в проект  
  
1.  Выберите целевой проект в обозревателе решений.  
  
2.  В меню **Проект** выберите пункт **Добавить существующий элемент**.  
  
    **Look in**  
    Определите расположение файлов или папок, которые будут добавлены в проект из этого списка. Для веб-служб XML и веб-приложений ASP.NET файлы размещаются на веб-сервере.  
  
    **Рабочий стол**  
    Отображает файлы и папки, находящиеся на рабочем столе.  
  
    **Мои проекты**  
    Отображает файлы и папки, размещенные в каталоге по умолчанию **Мои проекты** .  
  
    **Мой компьютер**  
    Отображает содержимое папки **Мой компьютер** .  
  
    **Имя файла**  
    Используйте этот параметр для фильтрации отображаемых файлов и папок. Введите полное или частичное имя файла для фильтра. Используйте знак звездочки (`*`) в шаблоне имени.  
  
    > [!NOTE]  
    > Просмотрите сетевые и веб-узлы, вводя сетевой путь или URL-адрес в поле **Имя файла** . Например, при вводе **http://mywebsite** отобразятся файлы, доступные на веб-сайте "mywebsite", а при вводе **\\\myserver\myshare** — файлы, расположенные в папке "myshare" на сервере "myserver".  
  
    **Тип файлов**  
    Используйте этот параметра для фильтрации файлов по расширению. Предлагается список из наиболее употребляемых типов файлов.  
  
    **Добавить**  
    Используйте эту кнопку, чтобы добавить элемент в проект и открыть его в редакторе по умолчанию.  
  
    -   **Добавить**  
  
        Происходит копирование существующего элемента в каталог проекта на диске и добавление элемента в выбранный проект в обозревателе решений. Все изменения, выполняемые над элементом, не отражаются на элементе в исходном расположении. Это редактор, используемый по умолчанию для заданного типа файлов.  
  
    -   **Добавить как ссылку**  
  
        Добавляет выбранный файл в проект и открывает его в редакторе, используемом по умолчанию для заданного типа файлов. Этот параметр открывает первоначально выбранный файл и не копирует файл в папку проекта.  
  
3.  При добавлении файла запроса в диалоговом окне соединения будет предложено указать соединение для данного запроса. Нажмите кнопку **Отмена** , если не нужно связывать запрос с соединением.  
  
4.  Файл будет добавлен в папку **Запросы** или **Прочие файлы** проекта.  
  
## <a name="see-also"></a>См. также:  
[Обозреватель решений](../../ssms/solution/solution-explorer.md)  
[Добавление в проект новые элементы](../../ssms/solution/add-new-items-to-a-project.md)  
[Перемещение или удаление элемента или проекта](../../ssms/solution/remove-or-delete-an-item-or-project.md)  
  
