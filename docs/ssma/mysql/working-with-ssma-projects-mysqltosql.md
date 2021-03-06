---
title: Работа с проектами SSMA (MySQLToSQL) | Документы Microsoft
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-mysql
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
helpviewer_keywords:
- Working with SSMA projects, create new project
- Working with SSMA projects, customize settings
- Working with SSMA projects, Open project
- Working with SSMA projects, Save project
ms.assetid: 9e4394e9-f177-41d9-839e-5d53a9c9b840
caps.latest.revision: 20
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 04c7be6a8dd46d0f35b14eb66eb1c244a5abe5cc
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2018
---
# <a name="working-with-ssma-projects-mysqltosql"></a>Работа с проектами SSMA (MySQLToSQL)
Чтобы выполнить миграцию баз данных MySQL в SQL Server или SQL Azure, сначала необходимо создать проект SSMA. Проект является файл, содержащий следующие сведения:  
  
-   Метаданные базы данных MySQL, которые требуется перенести в SQL Server или SQL Azure.  
  
-   Метаданные о целевом экземпляре SQL Server или SQL Azure, который получит перенесенные объекты и данные.  
  
-   SQL Server или SQL Azure сведения о соединении.  
  
-   Параметры проекта.  
  
При открытии проекта, он отключается от MySQL и SQL Server или SQL Azure. Позволяет работать в автономном режиме. Дополнительные сведения о подключении к SQL Server см. в разделе [подключение к SQL Server &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-sql-server-mysqltosql.md)  
  
## <a name="reviewing-default-project-settings"></a>Просмотреть параметры проекта по умолчанию  
SSMA содержит несколько параметров для преобразования и загрузки базы данных, перенос данных и синхронизации SSMA с MySQL и SQL Server или SQL Azure. Параметры по умолчанию подходят для многих пользователей. Тем не менее перед созданием нового проекта SSMA рекомендуется проверить параметры. При необходимости можно изменить параметры по умолчанию, которые будут использоваться для новых проектов.  
  
##### <a name="to-review-default-project-settings"></a>Чтобы просмотреть параметры проекта по умолчанию  
  
1.  Выберите **параметры проекта по умолчанию** из **средства** меню.  
  
2.  Выберите тип проекта в **миграции целевой версии** раскрывающийся список, какие параметры должны быть просмотреть или изменить, а затем нажмите кнопку **Общие** вкладки.  
  
3.  В левой области щелкните **преобразование**.  
  
4.  В правой области просмотрите и при необходимости измените параметры. Дополнительные сведения об этих параметрах см. в разделе [параметры проекта &#40;преобразования&#41; &#40;MySQLToSQL&#41; ](../../ssma/mysql/project-settings-conversion-mysqltosql.md) .  
  
5.  Повторите шаги 1 – 3 для миграции, синхронизации, SQL Azure, графического пользовательского интерфейса и сопоставление типов страниц.  
  
-   Сведения о миграции параметров см. в разделе [параметры проекта &#40;миграции&#41; &#40;MySQLToSQL&#41;](../../ssma/mysql/project-settings-migration-mysqltosql.md).  
  
-   Сведения о параметрах для синхронизации с SQL Server см. в разделе [параметры проекта &#40;синхронизации&#41; &#40;MySQLToSQL&#41;](../../ssma/mysql/project-settings-synchronization-mysqltosql.md).  
  
-   Сведения о параметрах графического пользовательского интерфейса см. в разделе [параметры проекта (GUI) (SSMA Common)](http://msdn.microsoft.com/en-us/cf06baf1-8714-48a3-95dc-781f6ca53693).  
  
-   Сведения о параметрах сопоставление типов данных см. в разделе [параметры проекта &#40;сопоставление типов&#41; &#40;MySQLToSQL&#41;](../../ssma/mysql/project-settings-type-mapping-mysqltosql.md).  
  
-   Сведения о параметрах SQL Azure см. в разделе [параметры проекта &#40;базу данных SQL Azure&#41; &#40;MySQLToSQL&#41;](../../ssma/mysql/project-settings-azure-sql-db-mysqltosql.md).  
  
> [!NOTE]  
> Параметры SQL Azure будет отображаться только при выборе **миграцию в SQL Azure** при создании проекта.  
  
## <a name="creating-new-projects"></a>Создание новых проектов  
Для переноса данных из базы данных MySQL в SQL Server или SQL Azure, необходимо создать проект.  
  
##### <a name="to-create-a-new-project"></a>Для создания нового проекта  
  
1.  Выберите **новый проект** из **файл** меню. Откроется диалоговое окно **Создание проекта** . В меню **Файл** выберите пункт **Создать проект**. Откроется диалоговое окно **Создание проекта** .  
  
2.  В поле **Name** введите имя проекта.  
  
3.  В **расположение** введите или выберите папку для проекта.  
  
4.  В **миграции для** раскрывающийся список, выберите версию целевой [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] используется для миграции. Доступны следующие варианты:  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014  
  
    -   База данных Azure SQL  
  
И нажмите кнопку **ОК**  
  
SSMA создает файл проекта.  
  
## <a name="customizing-project-settings"></a>Настройка параметров проекта  
Кроме определения по умолчанию параметры проекта, которые применяются ко всем новым проектам SSMA также можно настроить параметры для каждого проекта. Дополнительные сведения см. в разделе [задание параметров проекта &#40;MySQLToSQL&#41;](../../ssma/mysql/setting-project-options-mysqltosql.md).  
  
При настройке сопоставления типов данных между исходной и целевой баз данных, можно определить сопоставления на уровне объектов, базы данных или проекта. Дополнительные сведения см. в разделе [сопоставление MySQL и типов данных SQL Server &#40;MySQLToSQL&#41;](../../ssma/mysql/mapping-mysql-and-sql-server-data-types-mysqltosql.md).  
  
## <a name="saving-projects"></a>Сохранение проектов  
Сохранение проектов позволяет пользователю по существу сохранить параметры проекта и, возможно, метаданные базы данных в файл проекта SSMA.  
  
##### <a name="to-save-a-project"></a>Сохранение проекта  
  
-   На **файл** последовательно выберите пункты **Сохранить** проекта.  
  
Если базы данных в проекте, были изменены или не был преобразован, SSMA предложит для загрузки и сохранения метаданных. Загрузки и сохранения метаданных позволяет работать в автономном режиме. Он также позволяет отправить файл проекта для других пользователей, таких как сотрудники службы технической поддержки. Если будет предложено сохранить метаданные, выполните следующие действия.  
  
1.  Для каждой базы данных, который показывает состояние **отсутствует метаданных**, установите флажок рядом с именем базы данных. Сохранение метаданных может занять несколько минут. Если вы не хотите сохранить метаданные на этом этапе, не устанавливайте флажки.  
  
2.  Нажмите кнопку **Сохранить**.  
  
SSMA проанализирует MySQL схем и сохранения этих метаданных в файле проекта.  
  
## <a name="opening-projects"></a>Открытие проектов  
При открытии проекта, он отключается от MySQL и от SQL Server или SQL Azure. Это позволяет работать в автономном режиме. Чтобы обновить метаданные, загрузка объектов базы данных в SQL Server или SQL Azure. Для переноса данных, должны повторно подключиться к SQL Server или SQL Azure.  
  
##### <a name="to-open-a-project"></a>Чтобы открыть проект  
  
1.  Используйте один из следующих процедур:  
  
    1.  На **файл** последовательно выберите пункты **последние проекты**.  
  
    2.  Выберите проект, который требуется открыть.  
  
    3.  На **файл** последовательно выберите пункты **Открытие проекта**, найдите файл проекта .m2ssproj, выберите файл и нажмите кнопку **откройте**.  
  
2.  Повторное подключение к MySQL, на **файл** последовательно выберите пункты **повторное подключение к MySQL**.  
  
3.  Чтобы повторно подключиться к SQL Server на **файл** последовательно выберите пункты **повторно подключиться к SQL Server**.  
  
4.  Чтобы повторно подключиться к SQL Azure на **файл** последовательно выберите пункты **повторно подключиться к SQL Azure.**  
  
## <a name="next-step"></a>Следующий шаг  
Следующим шагом в процессе миграции является [подключение к MySQL &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-mysql-mysqltosql.md)  
  
## <a name="see-also"></a>См. также  
[Подключение к MySQL &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-mysql-mysqltosql.md)  
[Миграция MySQL баз данных SQL Server — Azure SQL DB &#40;MySQLToSql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
[Подключение к SQL Server &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-sql-server-mysqltosql.md)  
[Подключение к базе данных Azure SQL &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-azure-sql-db-mysqltosql.md)  
  
