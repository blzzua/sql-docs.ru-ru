---
title: "Запуск SQL Server Management Studio | Документы Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
ms.assetid: 25ffaea6-0eee-4169-8dd0-1da417c28fc6
caps.latest.revision: 45
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 5db067d5a2fe5bbf9953484c9a999ed7b1fcddae
ms.openlocfilehash: c472ec73a5b0b24f47b5bc59121eda206e285ac9
ms.contentlocale: ru-ru
ms.lasthandoff: 06/23/2017

---
# <a name="lesson-1-1---start-sql-server-management-studio"></a>Занятие 1–1. Запуск SQL Server Management Studio
В начале этого учебника кратко рассмотрим среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
## <a name="opening-sql-server-management-studio"></a>Открытие среды SQL Server Management Studio  
  
#### <a name="to-open-sql-server-management-studio"></a>Открытие среды SQL Server Management Studio  
  
1.  Способ запуска среды [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] (SSMS) зависит от операционной системы.  
* В новых версиях Windows, в которых есть **начальная страница**, на **начальной странице**введите **[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]** , и появится программа. Щелкните программу, чтобы открыть среду SSMS. Вы можете щелкнуть программу правой кнопкой мыши и закрепить ее на **начальной странице**.   
* В более старых версиях Windows в меню **Пуск** наведите указатель на пункт **Все программы**, затем на пункт [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]и выберите **SQL Server Management Studio**. Кроме того, в диалоговом окне **Выполнить** можно ввести **SSMS.exe** и нажать кнопку **ОК**.  
  
    > [!NOTE]  
    >  Если среда SSMS не открывается, возможно, она не была успешно установлена. Установите среду SSMS из [Центра загрузки](https://msdn.microsoft.com/library/mt238290.aspx). Среда SSMS не устанавливается автоматически вместе с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016. Чтобы получить доступ ко всем возможностям, используйте последнюю версию.  
  
2.  В следующем шаге вы подключитесь к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью компонента **Обозреватель объектов** среды SSMS. Если панель "Обозреватель объектов" не отображается, в меню **Вид** выберите пункт **Обозреватель объектов**. В меню обозревателя объектов нажмите кнопку **Подключиться** и выберите пункт **Ядро СУБД**. Должно открыться диалоговое окно **Соединение с сервером** . (Если вы ранее устанавливали среду SSMS, пользовательские параметры могут быть настроены так, что диалоговое окно **Соединение с сервером** появляется автоматически.)  
  
3.  В диалоговом окне **Соединение с сервером** заполните поле **Имя сервера** . Подключиться можно к одному из трех типов серверов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Для каждого типа формат значения в поле **Имя сервера** будет немного разным. Выберите один из следующих форматов:  
--  **Экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] по умолчанию.** При установке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на компьютере можно указать, что экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] будет экземпляром по умолчанию (неименованным) или именованным экземпляром. Если вы подключаетесь к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]по умолчанию, вставьте имя компьютера. Например, если среда SSMS выполняется на компьютере с именем "Бухгалтерия" и вы подключаетесь к установленному на этом компьютере экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  по умолчанию, введите **Бухгалтерия** в поле **Имя сервера** .  
--  **Именованный экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].** Во время установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно указать имя экземпляра. Например, на компьютере с именем "Бухгалтерия" можно указать имя экземпляра **Поступления**. Чтобы подключиться к именованному экземпляру, в поле **Имя сервера** введите имя компьютера, обратную косую черту и имя экземпляра, например **Бухгалтерия\Поступления**.  
--  **База данных SQL Azure** . Формат имени сервера для базы данных SQL следующий: Имя_SQL_Server.database.windows.net, например **mydb2.database.windows.net**. Если у вас возникают проблемы с определением имени сервера, посетите портал Azure, чтобы получить помощь в создании строки подключения.  
  
4. В области **Проверка подлинности**  
  
## <a name="management-studio-components"></a>Компоненты среды Management Studio  
[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] представляет данные в виде окон, выделенных для отдельных типов данных. Сведения о базе данных отображаются в обозревателе объектов и окнах документов.  
  
-   Обозреватель объектов является представлением в виде дерева, в котором отображаются все объекты базы данных на сервере. Он может содержать базы данных компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]и служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Обозреватель объектов включает сведения по всем серверам, к которым он подключен. При открытии среды [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]пользователю предлагается применить при подключении обозревателя объектов параметры, которые использовались в прошлый раз. Чтобы подключиться к любому из серверов, следует дважды щелкнуть его в компоненте «Зарегистрированные серверы», однако регистрировать его не обязательно.  
  
-   Окно документов представляет собой наиболее крупную часть среды [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. В окнах документов могут размещаться редакторы запросов и окна браузера. По умолчанию отображается страница «Сводка», подключенная к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] на текущем компьютере.  
  
## <a name="showing-additional-windows"></a>Отображение дополнительных окон  
  
#### <a name="to-show-the-registered-servers-window"></a>Отображение окна «Зарегистрированные серверы»  
  
1.  В меню **Вид** выберите пункт **Зарегистрированные серверы**.  
  
    Сверху от обозревателя объектов или рядом с ним появится окно "Зарегистрированные серверы". Его можно перетаскивать и закреплять в разных местах. В списке зарегистрированных серверов указаны серверы, работу которых приходится часто регулировать. В этом списке можно добавлять и удалять серверы. В этом списке указываются только экземпляры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на компьютере, где запущена среда [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
2.  Если нужный сервер не отображается, щелкните правой кнопкой мыши в списке зарегистрированных серверов пункт **Ядро СУБД**, выберите пункт **Задачи**, а затем щелкните **Обновить регистрацию локального сервера**. Чтобы добавить дополнительные серверы SQL Server или базы данных SQL, щелкните правой кнопкой мыши место в списке "Зарегистрированные серверы" и выберите пункт **Регистрация нового сервера**. Заполните данные в области **Имя входа** так же, как вы заполняли диалоговое окно **Соединение с сервером** .  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
[Подключение к зарегистрированным серверам и к обозревателю объектов](../../tools/sql-server-management-studio/lesson-1-2-connect-with-registered-servers-and-object-explorer.md)  
  
