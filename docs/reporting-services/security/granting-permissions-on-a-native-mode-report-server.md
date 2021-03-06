---
title: "Предоставление разрешений на сервер отчетов в собственном режиме | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: security
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- roles [Reporting Services], creating
- authorization [Reporting Services]
- server security [Reporting Services]
- role-based security [Reporting Services]
- items [Reporting Services], security
- permissions [Reporting Services], native mode
- published reports [Reporting Services], security
- reports [Reporting Services], security
- report items [Reporting Services], security
- role-based security [Reporting Services], about role-based security
- security [Reporting Services], role-based
ms.assetid: 260dc2e9-546c-4f04-9fa1-977e23c9d68c
caps.latest.revision: "60"
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: b97ba436eeedf30521b22fb0231ace07cdacbefc
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/09/2018
---
# <a name="granting-permissions-on-a-native-mode-report-server"></a>Предоставление разрешений на сервер отчетов в собственном режиме
  Службы SQL Server [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] используют авторизацию, основанную на ролях, и подсистему проверки подлинности для определения того, кто может выполнять операции и обращаться к элементам на сервере отчетов. Основанная на ролях авторизация разбивает на категории (роли) множество действий, которые может выполнять отдельный пользователь или группа. Проверка подлинности основывается на встроенной проверке подлинности Windows либо в пользовательском модуле проверки подлинности, предоставленном пользователем. Можно использовать стандартные или настраиваемые роли с любым типом проверки подлинности.  
  
## <a name="using-roles-to-grant-report-server-access"></a>Использование ролей для предоставления доступа к серверу отчетов  
 Все пользователи взаимодействуют с сервером отчетов в контексте роли, определяющей конкретный уровень доступа. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] содержат стандартные роли, которые можно присвоить пользователям и группам, чтобы обеспечить немедленный доступ к серверу отчетов. **Диспетчер содержимого**, **Издатель**и **Браузер** — примеры стандартных ролей. Каждой ролью определяется набор взаимосвязанных задач. Например, роль **Издатель** имеет разрешение на добавление отчетов и создание папок для хранения этих отчетов.  
  
 Назначения ролей обычно наследуются от родительского узла, однако можно прервать наследование разрешений, создав новое назначение ролей для конкретного элемента. Пользователь, являющийся членом роли **Диспетчер содержимого** для одного отчета, может быть членом роли **Браузер** для другого отчета.  
  
 Для предоставления доступа к элементам и операциям сервера отчетов следуйте приведенным ниже рекомендациям.  
  
1.  Ознакомьтесь со списком стандартных ролей и определите, допустимо ли использовать их без изменений. Если необходимо изменить набор задач для ролей или определить дополнительные роли, это следует сделать до назначения пользователям каких-либо ролей. Дополнительные сведения о каждой роли см. в разделе [Стандартные роли](../../reporting-services/security/role-definitions-predefined-roles.md).  
  
2.  Выясните, каким пользователям и группам требуется доступ к серверу отчетов и на каком уровне. Большинству пользователей следует назначить роль **Браузер** или роль **Построитель отчетов** . Меньшему числу пользователей следует назначить роль **Издатель** . В роль **Диспетчер содержимого**должно быть включено весьма небольшое число пользователей.  
  
3.  Используйте диспетчер отчетов, чтобы присвоить роли, регламентирующие доступ к папке Home (папке верхнего уровня в иерархии папок сервера отчетов), каждому пользователю или группе, которым необходимо предоставить доступ.  
  
4.  На уровне сайта, с помощью страницы "Настройки сайта" в диспетчере отчетов, создайте назначения ролей системного уровня для каждого пользователя и группы с использованием стандартных ролей **Системный пользователь** и **Системный администратор**.  
  
5.  Если необходимо, создайте дополнительные назначения ролей для конкретных папок, отчетов и других элементов. Избегайте создания большого количества назначений ролей. Если их будет создано слишком много, станет сложно отследить различные уровни доступа для каждого пользователя.  
  
> [!NOTE]  
>  Если сервер отчетов настроен на работу в объединенном режиме SharePoint, необходимо установить разрешения на сайт SharePoint для предоставления доступа к элементам сервера отчетов. Дополнительные сведения см. в разделе [Предоставление разрешений для элементов сервера отчетов на сайте SharePoint](../../reporting-services/security/granting-permissions-on-report-server-items-on-a-sharepoint-site.md).  
  
## <a name="who-sets-permissions"></a>Кто устанавливает разрешения  
 Первоначально только пользователи, входящие в группу локальных администраторов, имеют доступ к серверу отчетов. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] устанавливаются с двумя назначениями ролей по умолчанию, которые предоставляют доступ на уровне элементов и на уровне системы членам группы локальных администраторов. Эти встроенные назначения ролей наделяют локальных администраторов правом предоставлять доступ к серверу отчетов другим пользователям и правом управлять элементами сервера отчетов. Встроенные назначения ролей нельзя удалить. Локальному администратору всегда предоставлен полный доступ для управления экземпляром сервера отчетов.  
  
 Поскольку полный доступ к серверу отчетов включает разрешения на уровне элементов и на уровне системы, локальному администратору назначаются следующие роли.  
  
 Администрирование экземпляра сервера отчетов на локальном компьютере под управлением операционных систем Windows Vista или Windows Server 2008 требует дополнительной настройки. Дополнительные сведения см. в разделе [Настройка сервера отчетов, работающего в основном режиме, для локального администрирования (службы SSRS)](../../reporting-services/report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).  
  
## <a name="how-permissions-are-stored"></a>Хранение разрешений  
 Назначения ролей и определения ролей хранятся в базе данных сервера отчетов. При использовании различных клиентских средств или программных интерфейсов доступ к серверу обеспечивается разрешениями, определяемыми для экземпляра сервера отчетов в целом. При настройке нескольких серверов отчетов для масштабного развертывания назначения ролей, определенные на одном экземпляре, хранятся в общей базе данных и используются всеми другими экземплярами, задействованными при масштабном развертывании. Поскольку назначения ролей хранятся вместе с элементами, доступ к которым ими определяется, можно переместить базу данных на другой экземпляр сервера отчетов, не потеряв ранее определенные разрешения.  
  
## <a name="tasks-and-tools-for-managing-permissions"></a>Задачи и средства для управления разрешениями  
 Используйте следующие средства для управления определениями ролей и назначениями ролей.  
  
|Инструмент|Задания|  
|----------|-----------|  
|Среда Management Studio — используется для просмотра, изменения, создания и удаления определений ролей.|[Создание, удаление и изменение ролей (среда Management Studio)](../../reporting-services/security/role-definitions-create-delete-or-modify.md)|  
|Диспетчер отчетов — используется для присвоения ролей пользователям и группам.|[Предоставление пользователям доступа к серверу отчетов (диспетчер отчетов)](../../reporting-services/security/grant-user-access-to-a-report-server-report-manager.md)<br /><br /> [Изменение или удаление назначения ролей (диспетчер отчетов)](../../reporting-services/security/role-assignments-modify-or-delete.md)|  
  
## <a name="see-also"></a>См. также:  
 [Стандартные роли](../../reporting-services/security/role-definitions-predefined-roles.md)   
 [Предоставление разрешений для элементов сервера отчетов на сайте SharePoint](../../reporting-services/security/granting-permissions-on-report-server-items-on-a-sharepoint-site.md)   
 [Проверка подлинности с использованием сервера отчетов](../../reporting-services/security/authentication-with-the-report-server.md)   
 [Создание назначений ролей и управление ими](../../reporting-services/security/create-and-manage-role-assignments.md)   
 [Защита и обеспечение безопасности служб Reporting Services](../../reporting-services/security/reporting-services-security-and-protection.md)   
 [Управление содержимым сервера отчетов (службы Reporting Services в собственном режиме)](../../reporting-services/report-server/report-server-content-management-ssrs-native-mode.md)  
  
  
