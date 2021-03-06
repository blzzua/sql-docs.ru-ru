---
title: "Задача \"Отправка почты\" | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: control-flow
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.sendmailtask.f1
- sql13.dts.designer.sendmailtask.general.f1
- sql13.dts.designer.sendmailtask.mail.f1
helpviewer_keywords:
- mail [Integration Services]
- Send Mail task
- e-mail [Integration Services]
- messages [Integration Services]
- sending messages
ms.assetid: fe0b7cbc-fe8e-4fe2-95b4-2953efff5869
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 6d3cacac1c13700c1416b6365ec6bb03f650fa31
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="send-mail-task"></a>Задача «Отправка почты»
  Задача «Отправка почты» производит отправку сообщения электронной почты. Эта задача позволяет пакету отправлять сообщения при успешном или неуспешном завершении задач в рабочем процессе пакета либо в ответ на события, инициируемые при выполнении пакета. Например, задача может уведомить администратора базы данных об успешном или неуспешном завершении задачи резервного копирования базы данных.  
  
 Задачу «Отправка почты» можно настроить следующими способами:  
  
-   Укажите текст сообщения электронной почты.  
  
-   Укажите строку темы сообщения электронной почты.  
  
-   Установите уровень приоритета сообщения. Задача поддерживает три уровня приоритета: обычный, низкий и высокий.  
  
-   Укажите получателей в строках «Кому», «Копия» и «Резервная копия». Если указываются несколько получателей, они должны быть разделены точками с запятой.  
  
    > [!NOTE]  
    >  Строки «Кому», «Копия» и «СК» ограничены длиной в 256 символов в соответствии со стандартами Интернета.  
  
-   Добавьте вложения. Если указываются несколько вложений, они должны быть разделены вертикальной чертой (|).  
  
    > [!NOTE]  
    >  Если файл вложения на момент выполнения пакета отсутствует, произойдет ошибка.  
  
-   Укажите используемый диспетчер соединений SMTP.  
  
    > [!IMPORTANT]  
    >  Диспетчер SMTP-соединений поддерживает только анонимную проверку подлинности и проверку подлинности Windows. Обычная проверка подлинности не поддерживается.  
  
 В качестве текста сообщения может быть указана строка, соединение с файлом, содержащим текст, либо имя переменной, в которой содержится текст. Подключение к файлу производится задачей при помощи диспетчера подключения файлов. Дополнительные сведения см. в статье [Flat File Connection Manager](../../integration-services/connection-manager/flat-file-connection-manager.md).  
  
 Задача производит подключение к почтовому серверу при помощи диспетчера соединений SMTP. Дополнительные сведения см. в статье [SMTP Connection Manager](../../integration-services/connection-manager/smtp-connection-manager.md).  
  
## <a name="custom-logging-messages-available-on-the-send-mail-task"></a>Пользовательские сообщения для ведения журнала, доступные в задаче «Отправка почты»  
 В следующей таблице перечислены пользовательские записи в журнале для задачи «Отправка почты». Дополнительные сведения см. в разделе [Ведение журналов в службах Integration Services (SSIS)](../../integration-services/performance/integration-services-ssis-logging.md).  
  
|Запись журнала|Description|  
|---------------|-----------------|  
|**SendMailTaskBegin**|Указывает, что задача приступила к отправке сообщения электронной почты.|  
|**SendMailTaskEnd**|Указывает, что задача завершила отправку сообщения электронной почты.|  
|**SendMailTaskInfo**|Выводит описательные сведения об этой задаче.|  
  
## <a name="configuring-the-send-mail-task"></a>Настройка задачи «Отправка почты»  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами.  
  
 Дополнительные сведения о свойствах, которые можно задать в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , см. в следующих разделах:  
  
-   [Страница «Выражения»](../../integration-services/expressions/expressions-page.md)  
  
 Сведения о задании этих свойств программными средствами см. в следующем разделе:  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.SendMailTask.SendMailTask>  
  
## <a name="related-tasks"></a>Related Tasks  
 Дополнительные сведения о настройке свойств этих свойств в конструкторе [!INCLUDE[ssIS](../../includes/ssis-md.md)] см. в разделе [Задание свойств задач или контейнеров](http://msdn.microsoft.com/library/52d47ca4-fb8c-493d-8b2b-48bb269f859b).  
  
## <a name="related-content"></a>См. также  
  
-   Техническая статья [How to send email with delivery notification in C#](http://go.microsoft.com/fwlink/?LinkId=237625)на сайте shareourideas.com  
  
## <a name="send-mail-task-editor-general-page"></a>Редактор задачи «Отправка почты» (страница «Общие»)
  Используйте страницу **Общие** диалогового окна **Редактор задачи «Отправка почты»** , чтобы задать имя и описание для задачи «Отправка почты».  
  
### <a name="options"></a>Параметры  
 **Название**  
 Укажите уникальное имя для задачи «Отправка почты». Это имя используется в качестве метки для значка задачи.  
  
 **Примечание.** Имена задач должны быть уникальными в пределах пакета.  
  
 **Описание**  
 Введите описание задачи «Отправка почты».  
  
## <a name="send-mail-task-editor-mail-page"></a>Редактор задачи «Отправка почты» (страница «Почта»)
  Страница **Почта** диалогового окна **Редактор задачи «Отправка почты»** служит для определения получателей, типа и приоритета сообщения. К сообщению можно также прикрепить файлы. Текстом сообщения может быть введенная строка, соединение с файлом, содержащим текст, или имя переменной, содержащей текст.  
  
### <a name="options"></a>Параметры  
 **SMTPConnection**  
 Выберите диспетчер подключений SMTP из списка или щелкните **\<Создать соединение…>**, чтобы создать его.  
  
> [!IMPORTANT]  
>  Диспетчер SMTP-соединений поддерживает только анонимную проверку подлинности и проверку подлинности Windows. Обычная проверка подлинности не поддерживается.  
  
 **См. также:** [Диспетчер соединений SMTP](../../integration-services/connection-manager/smtp-connection-manager.md)  
  
 **От**  
 Задайте адрес электронной почты отправителя.  
  
 **Чтобы**  
 Укажите адреса электронной почты получателей, разделенные точкой с запятой.  
  
 **Копия**  
 Задайте адреса электронной почты получателей, которые также получают копии сообщения. Разделяйте адреса точками с запятой.  
  
 **Скрытая копия**  
 Задайте адреса электронной почты получателей, которые получают скрытые копии сообщения. Разделяйте адреса точками с запятой.  
  
 **Тема**  
 Укажите тему электронного сообщения.  
  
 **MessageSourceType**  
 Выберите тип источника сообщения. Это свойство имеет параметры, указанные в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|**Прямой ввод**|Задание источника текста сообщения. При выборе этого значения отображается динамический параметр **MessageSource**.|  
|**Соединение с файлом**|Задание в качестве источника файла, содержащего текст сообщения. При выборе этого значения отображается динамический параметр **MessageSource**.|  
|**Переменная**|В качестве источника указывается переменная, содержащая текст сообщения. При выборе этого значения отображается динамический параметр **MessageSource**.|  
  
 **Приоритет**  
 Задается приоритет сообщения.  
  
 **Вложения**  
 Укажите имена вложений для электронного сообщения, разделенные символом вертикальной черты (|).  
  
> [!NOTE]  
>  Длина строк «Кому», «Копия» и «СК» ограничена 256 символами в соответствии со стандартами Интернета.  
  
### <a name="messagesourcetype-dynamic-options"></a>Динамические параметры MessageSourceType  
  
#### <a name="messagesourcetype--direct-input"></a>MessageSourceType = Прямой ввод  
 **MessageSource**  
 Введите текст сообщения или нажмите кнопку обзора (…), а затем введите сообщение в диалоговом окне **Источник сообщения** .  
  
#### <a name="messagesourcetype--file-connection"></a>MessageSourceType = Соединение с файлом  
 **MessageSource**  
 Выберите диспетчер подключений файлов из списка или щелкните \<**Создать соединение…**>, чтобы создать его.  
  
 **См. также:** [File Connection Manager](../../integration-services/connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../integration-services/connection-manager/file-connection-manager-editor.md)  
  
#### <a name="messagesourcetype--variable"></a>MessageSourceType = Переменная  
 **MessageSource**  
 Выберите переменную из списка или нажмите кнопку \<**Создать переменную…**>, чтобы создать переменную.  
  
 **См. также:** [Переменные в службах Integration Services (SSIS)](../../integration-services/integration-services-ssis-variables.md), [Добавление переменной](http://msdn.microsoft.com/library/d09b5d31-433f-4f7c-8c68-9df3a97785d5)  
  
## <a name="see-also"></a>См. также:  
 [Задачи служб Integration Services](../../integration-services/control-flow/integration-services-tasks.md)   
 [Поток управления](../../integration-services/control-flow/control-flow.md)  
  
  
