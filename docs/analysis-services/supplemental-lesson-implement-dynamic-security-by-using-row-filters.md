---
title: "Реализация динамической безопасности с помощью фильтров строк | Документы Microsoft"
ms.custom: 
ms.date: 04/10/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to: 
ms.assetid: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 51ffec7f5fc4d5d6d44ff1dbab0e4a20827f6718
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="supplemental-lesson---implement-dynamic-security-by-using-row-filters"></a>Дополнительного занятия - реализация динамической безопасности с помощью фильтров строк
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

На этом дополнительном занятии будет создана дополнительная роль, реализующая динамическую безопасность. Динамическая безопасность позволяет определять защиту на уровне строк с учетом имени или идентификатор входа пользователя, который находится в системе в данный момент. Дополнительные сведения см. в разделе [Роли](../analysis-services/tabular-models/roles-ssas-tabular.md).  
  
Для реализации динамической безопасности необходимо добавить в модель таблицу, содержащую имена тех пользователей, которые могут создавать соединения с моделью как с источником данных и просматривать объекты и данные модели. Модель, которая будет создана на этом занятии, находится в контексте Adventure Works Corp. Но в целях данного занятия добавим таблицу, содержащую пользователей из собственного домена пользователя. Для добавляемых имен пользователей пароли не потребуются. Чтобы создать таблицу EmployeeSecurity с небольшой выборкой пользователей из собственного домена, используется функция вставки данных из электронной таблицы Excel. В реальном сценарии таблица, содержащая добавляемые в модель имена, будет использовать таблицу из фактической базы данных в качестве источника данных — например, реальную таблицу dimEmployee.  
  
Для реализации динамической безопасности будут использованы две новые функции DAX: [функция USERNAME (DAX)](http://msdn.microsoft.com/en-us/22dddc4b-1648-4c89-8c93-f1151162b93f) и [функция LOOKUPVALUE (DAX)](http://msdn.microsoft.com/en-us/73a51c4d-131c-4c33-a139-b1342d10caab). Эти функции, примененные к формуле фильтра строк, определяются в новой роли. Функция lookupvalue ПОЛУЧАЕТ формула указывает значение из таблицы EmployeeSecurity и затем передает значение его функции USERNAME, который указывает имя пользователя, выполнившего вход пользователя принадлежит этой роли. После этого пользователь может просматривать только те данные, которые пропускает фильтр строк роли. В этом сценарии нужно будет указать, что сотрудники отдела продаж могут просматривать только те данные интернет-продаж, которые относятся к их региону.  
  
Во время выполнения этого дополнительного занятия нужно будет выполнить ряд заданий. Эти задачи являются уникальными для сценария табличной модели Adventure Works, но они не могут иметь прямого отношения к реальному сценарию. Каждое задание включает дополнительные сведения, описывающие цель задания.  
  
Предполагаемое время выполнения данного занятия: **30 минут**  
  
## <a name="prerequisites"></a>предварительные требования  
Это дополнительное занятие является частью учебника по табличному моделированию, который необходимо изучать по порядку. Прежде чем выполнять задания в этом дополнительном занятии, необходимо завершить все предыдущие занятия.  
  
## <a name="add-the-dimsalesterritory-table-to-the-aw-internet-sales-tabular-model-project"></a>Добавление таблицы dimSalesTerritory в проект табличной модели интернет-продаж AW  
Чтобы реализовать динамическую безопасность для этого сценария Adventure Works, необходимо добавить в модель две дополнительные таблицы. Первая таблица, которая будет добавлена, называется dimSalesTerritory (т. е. территория продаж) из той же базы данных AdventureWorksDW. Будет применен фильтр строк в таблице SalesTerritory, определяющий данные, которые можно просматривать вошедшего в систему пользователя.  
  
#### <a name="to-add-the-dimsalesterritory-table"></a>Добавление таблицы dimSalesTerritory  
  
1.  В SSDT выберите **модель** меню, а затем нажмите **существующие соединения**.  
  
2.  Убедитесь в том, что в диалоговом окне **Существующие соединения** выбрано соединение с источником данных **База данных Adventure Works из SQL** , и нажмите кнопку **Открыть**.  
  
    Если открылось диалоговое окно "Учетные данные олицетворения", введите учетные данные олицетворения, использованные на занятии 2.  
  
3.  Убедитесь в том, что на странице **Выбор способа импорта данных** выбран пункт **Выбрать из списка таблиц и представлений, чтобы определить данные для импорта** , и нажмите кнопку **Далее**.  
  
4.  На странице **Выбор таблиц и представлений** выберите таблицу **DimSalesTerritory** .  
  
5.  Нажмите кнопку **Просмотр и применение фильтра**.  
  
6.  Снимите выделение со столбца **SalesTerritoryAlternateKey** и нажмите кнопку **ОК**.  
  
7.  На странице **Выбор таблиц и представлений** нажмите кнопку **Готово**.  
  
    Новая таблица будет добавлена в рабочую область модели. Объекты и данные из исходной таблицы DimSalesTerritory будут импортированы в табличной модели AW Internet Sales.  
  
9. После импорта таблицы нажмите кнопку **Закрыть**.  

## <a name="add-a-table-with-user-name-data"></a>Добавление таблицы с именами пользователей  
Поскольку таблица dimEmployee в образце базы данных AdventureWorksDW содержит пользователей из домена AdventureWorks и эти имена пользователей не существуют в текущей среде, необходимо создать таблицу в модели, содержащей небольшую выборку (дерево) фактических пользователей из организации. После этого нужно добавить этих пользователей как членов в новую роль. Для выборки имен пользователей пароли не требуются, однако нужны имена реальных пользователей Windows из домена.  
  
#### <a name="to-add-an-employeesecurity-table"></a>Чтобы добавить таблицу EmployeeSecurity  
  
1.  Откройте Microsoft Excel и создайте новую электронную таблицу.  
  
2.  Скопируйте следующую таблицу, включая строку заголовка, и вставьте ее в электронную таблицу.  

    ```
      |EmployeeId|SalesTerritoryId|FirstName|LastName|LoginId|  
      |---------------|----------------------|--------------|-------------|------------|  
      |1|2|<user first name>|<user last name>|\<domain\username>|  
      |1|3|<user first name>|<user last name>|\<domain\username>|  
      |2|4|<user first name>|<user last name>|\<domain\username>|  
      |3|5|<user first name>|<user last name>|\<domain\username>|  
    ```

3.  Замените имя, фамилию и домен\имя_пользователя имена и идентификаторы входа трех пользователей в вашей организации. Поместите того же пользователя на первые две строки для EmployeeId 1. Это означает, что пользователь относится к более чем одной территории продаж. Изменяйте поля EmployeeId и SalesTerritoryId.  
  
4.  Сохранить журнал как **SampleEmployee**.  
  
5.  На листе выберите все ячейки с данными о сотрудниках, включая заголовки, а затем щелкните правой кнопкой мыши выбранные данные и нажмите кнопку **копирования**.  
  
6.  В SSDT выберите **изменить** меню, а затем нажмите **вставить**.  
  
    Если вставить неактивен, щелкните любой столбец в любой таблице в окне конструктора моделей и повторите попытку.  
  
7.  В **Просмотр вставки** диалогового **имя таблицы**, тип **EmployeeSecurity**.  
  
8.  В **данные для вставки**, проверьте данные включают все данные пользователя и заголовки из SampleEmployee листа.  
  
9. Убедитесь в том, что установлен флажок **Использовать первую строку в качестве заголовков столбцов** , и нажмите кнопку **ОК**.  
  
    Создается новую таблицу с именем EmployeeSecurity с данными о сотрудниках копируются SampleEmployee листа.  
  
## <a name="create-relationships-between-factinternetsales-dimgeography-and-dimsalesterritory-table"></a>Создание связей между таблицами FactInternetSales DimGeography и DimSalesTerritory  
Все таблицы FactInternetSales DimGeography и DimSalesTerritory содержат общий столбец SalesTerritoryId. Столбец SalesTerritoryId таблицы DimSalesTerritory содержит значения с другим идентификатором для каждой территории продаж.  
  
#### <a name="to-create-relationships-between-the-factinternetsales-dimgeography-and-the-dimsalesterritory-table"></a>Для создания связей между FactInternetSales DimGeography и таблицы DimSalesTerritory  
  
1.  В конструкторе моделей в представлении диаграммы в **DimGeography** щелкните и удерживайте **SalesTerritoryId** столбец, затем перетащите курсор в **SalesTerritoryId** столбец в **DimSalesTerritory** таблицы, а затем отпустите.  
  
2.  В **FactInternetSales** щелкните и удерживайте **SalesTerritoryId** столбец, затем перетащите курсор в **SalesTerritoryId** столбца в  **DimSalesTerritory** таблицы, а затем отпустите.  
  
    Обратите внимание, что свойство «активный» для этого отношения значение False, то есть оно неактивно. Это так, как таблицы FactInternetSales уже имеет другую активную связь, используемую в мерах.  
  
## <a name="hide-the-employeesecurity-table-from-client-applications"></a>Скрыть таблицу EmployeeSecurity из клиентских приложений  
В этой задаче предстоит скрыть таблицы EmployeeSecurity, поддерживая ее появления в списке полей клиентского приложения. Помните, что скрытие таблицы не обеспечивает ее безопасность. Пользователи могут запрашивать по-прежнему EmployeeSecurity таблицу данных, если они знают, как. Чтобы защитить данные таблицы EmployeeSecurity, препятствующие пользователям запрашивать любые данные, будет применен фильтр в одной из следующих задач.  
  
#### <a name="to-hide-the-employeesecurity-table-from-client-applications"></a>Чтобы скрыть таблицу EmployeeSecurity из клиентских приложений  
  
-   В конструкторе моделей в представлении диаграммы щелкните правой кнопкой мыши заголовок таблицы **Сотрудник** и выберите команду **Скрыть из набора клиентских средств**.  
  
## <a name="create-a-sales-employees-by-territory-user-role"></a>Создание пользовательской роли «Сотрудники отдела продаж по территории»  
На этом занятии будет создана новая пользовательская роль. Эта роль будет включать фильтр строк, определяющий, какие строки таблицы DimSalesTerritory отображаются для пользователей. В направлении один ко многим на другие таблицы, связанные с DimSalesTerritory применяется фильтр. Будет также применен простой фильтр, обеспечивающий безопасность всей таблицы EmployeeSecurity могли направлять к любой пользователь, который является членом роли.  
  
> [!NOTE]  
> Роль «Сотрудники отдела продаж по территории», создаваемая на этом занятии, ограничивает возможность членов, просматривающих данные продаж, территорией, к которой они относятся. При добавлении пользователя как члена сотрудники отдела продаж по территории, также существует как в роли для создания в [занятие 11: Создание ролей](../analysis-services/lesson-11-create-roles.md), вы получите сочетание разрешений. Когда пользователь является членом нескольких ролей, он обладает всеми разрешениями, определенными для каждой из них. Это означает, что пользователь будет иметь больше разрешений, определяемых сочетанием ролей.  
  
#### <a name="to-create-a-sales-employees-by-territory-user-role"></a>Создание пользовательской роли «Сотрудники отдела продаж по территории»  
  
1.  В SSDT выберите **модель** меню, а затем нажмите **ролей**.  
  
2.  В **диспетчер ролей**, нажмите кнопку **New**.  
  
    В список будет добавлена новая роль с разрешением «Нет».  
  
3.  Щелкните новую роль, а затем столбец **Имя** , после чего переименуйте роль в **Сотрудники отдела продаж по территории**.  
  
4.  В столбце **Разрешения** щелкните раскрывающийся список и выберите разрешение **Чтение**.  
  
5.  Перейдите на вкладку **Члены** и выберите команду **Добавить**.  
  
6.  В **Выбор пользователя или группы** диалогового **введите выбираемого объекта**, введите имя пользователя первый пример, используемый при создании таблицы EmployeeSecurity. Щелкните **Проверить имена** , чтобы убедиться в том, что имя является действительным, и нажмите кнопку **ОК**.  
  
    Повторите этот шаг, добавляя другие выборки имен пользователей, используемые при создании таблицы EmployeeSecurity.  
  
7.  Откройте вкладку **Фильтры строк** .  
  
8.  Для **EmployeeSecurity** таблице в **фильтр DAX** столбца, введите следующую формулу.  
  
    ```
      =FALSE()  
    ```
  
    Эта формула указывает, что все столбцы решаются в false логическое условие. Таким образом не указаны столбцы в таблице EmployeeSecurity могут запрашиваться членом сотрудники отдела продаж по территории роли пользователя.  
  
9. Для таблицы **DimSalesTerritory** введите следующую формулу:  

    ```  
    ='Sales Territory'[Sales Territory Id]=LOOKUPVALUE('Employee Security'[Sales Territory Id], 
      'Employee Security'[Login Id], USERNAME(), 
      'Employee Security'[Sales Territory Id], 
      'Sales Territory'[Sales Territory Id]) 
    ```
  
    В этой формуле функция LOOKUPVALUE возвращает все значения для столбца DimEmployeeSecurity [SalesTerritoryId], где EmployeeSecurity [LoginId] совпадает с именем текущего пользователя имя пользователя Windows, а EmployeeSecurity [SalesTerritoryId] совпадает с DimSalesTerritory [SalesTerritoryId].  
  
    Набор идентификаторов, возвращенные функцией LOOKUPVALUE территории продаж затем используется для ограничения строк, отображаемых в таблице DimSalesTerritory. Отображаются только строки, где SalesTerritoryID для строки в набор идентификаторов, возвращенных функцией LOOKUPVALUE.  
  
10. В диспетчере роли щелкните **ОК**.  
  
## <a name="test-the-sales-employees-by-territory-user-role"></a>Тестирование пользовательской роли «Сотрудники отдела продаж по территории»  
В этой задаче будет использовать функции анализа в Excel в SSDT можно протестировать эффективность сотрудники отдела продаж по территории роли пользователя. Будет указано одно из имен пользователей, добавленный в таблицу EmployeeSecurity и в качестве члена роли. Это имя пользователя будет затем использовано как имя реального пользователя для соединения, установленного между Excel и моделью.  
  
#### <a name="to-test-the-sales-employees-by-territory-user-role"></a>Тестирование пользовательской роли «Сотрудники отдела продаж по территории»  
  
1.  В SSDT выберите **модель** меню, а затем нажмите **анализ в Excel**.  
  
2.  В диалоговом окне **Анализ в Excel** в поле **Укажите имя пользователя или роль для подключения к модели**выберите вариант **Другой пользователь Windows**и нажмите кнопку **Обзор**.  
  
3.  В **Выбор пользователя или группы** диалогового **введите имена выбираемых объектов**, введите одно из имен пользователей, которые добавляются в таблицу EmployeeSecurity и нажмите кнопку **проверить имена**.  
  
4.  Нажмите кнопку **ОК** , чтобы закрыть диалоговое окно **Выбор пользователя или группы** , а затем кнопку **ОК** , чтобы закрыть диалоговое окно **Анализ в Excel** .  
  
    Excel откроет новую книгу. Сводная таблица создается автоматически. Список полей сводной таблицы включает большинство полей данных, доступных в новой модели.  
  
    Обратите внимание, что в таблице EmployeeSecurity не отображается в списке полей сводной таблицы. Это происходит потому, что эта таблица была скрыта от клиентских средств в предыдущем задании.  
  
5.  В **поля** в списке **∑ Интернет-продаж** (меры) выберите **InternetTotalSales** мер. Мера будет указана в полях **Значения** .  
  
6.  Выберите **SalesTerritoryId** столбец из **DimSalesTerritory** таблицы. Столбец будет введен в поля **Метки строк** .  
  
    Обратите внимание, что цифры продаж появятся только для того региона, к которому относится имя пользователя. Если выбрать другой столбец; например города, из таблицы DimGeography как поле метки строки, только города территории продаж, к которой относится пользователь, отображаются.  
  
    Этот пользователь не может просматривать или отправлять запросы для получения данных Интернет-продаж для других территорий, к которым он не относится, поскольку фильтр строк, определенный для таблицы «Территория продаж» в пользовательской роли «Сотрудники отдела продаж по территории», надежно защищает все данные, связанные с другими территориями продаж.  
  
## <a name="see-also"></a>См. также:  
[функция USERNAME (DAX)](http://msdn.microsoft.com/en-us/22dddc4b-1648-4c89-8c93-f1151162b93f)  
[функция LOOKUPVALUE (DAX)](http://msdn.microsoft.com/en-us/73a51c4d-131c-4c33-a139-b1342d10caab)  
[CUSTOMDATA, функция (DAX)](http://msdn.microsoft.com/en-us/58235ad8-226c-43cc-8a69-5a52ac19dd4e)  
