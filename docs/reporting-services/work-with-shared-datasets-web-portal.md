---
title: "Работа с общими наборами данных (веб-портал) | Документы Майкрософт"
ms.custom: 
ms.date: 07/02/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.service: 
ms.component: reporting-services
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2641ea84-9343-4e6f-aec1-25339031b163
caps.latest.revision: "7"
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 4e72c48f816752530abddb6246410e4936ac20a6
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/09/2018
---
# <a name="work-with-shared-datasets---web-portal"></a>Работа с общими наборами данных (веб-портал)

[!INCLUDE[ssrs-appliesto](../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../includes/ssrs-appliesto-pbirs.md)]

Общий набор данных позволяет управлять параметрами набора данных независимо от отчетов и других элементов каталога, использующих этот набор. Общие наборы данных можно использовать с разбитыми на страницы и мобильными отчетами, а также с ключевыми показателями эффективности.

Вы можете просматривать свойства общего набора данных и управлять ими в пределах веб-портала. На веб-портале можно запускать построитель отчетов для создания или изменения общих наборов данных.

## <a name="create-a-shared-dataset"></a>Создание общего набора данных
  
Чтобы создать новый общий набор данных, можно сделать следующее.  
  
1.  Выберите команду "Создать" в строке меню.  
  
2.  Выберите **Набор данных**.  
  
    ![ssRSDataset-NewDataset](../reporting-services/media/ssrsdataset-newdataset.png)  
  
3.  При этом либо запустится построитель отчетов, либо появится запрос на его загрузку.  
  
4.  В диалоговом окне **Создание отчета или набора данных** выберите подключение к источнику данных, которое будет использоваться для этого набора данных. Возможно, вам потребуется перейти в расположение общего источника данных.  
  
5.  Выберите **Создать**.  
  
6.  Постройте набор данных, а затем выберите значок **Сохранить** в левом верхнем углу, чтобы сохранить набор данных на сервере отчетов.  
  
## <a name="manage-an-existing-shared-dataset"></a>Управление существующим общим набором данных
  
Для управления существующим общим набором данных можно сделать следующее.  
  
> [!NOTE]
> Если общий набор данных не отображается в папке, убедитесь, что вы просматриваете наборы данных. Выберите **Вид** в строке меню в правом верхнем углу веб-портала. Убедитесь, что установлен флажок **Наборы данных** .  
  
1.  Щелкните **многоточие (…)** рядом с набором данных, которым требуется управлять.  
  
    ![ssRSDataset-Ellipse](../reporting-services/media/ssrsdataset-ellipse.png)  
  
2.  Выберите **Управление**, после чего откроется экран редактирования.  
  
    ![ssRSDataset-Manage](../reporting-services/media/ssrsdataset-manage.png)  
  
## <a name="properties"></a>Свойства
  
На экране свойств можно изменить свойства **Имя** и **Описание** набора данных. Также доступны команды **Удалить**, **Переместить**, **Изменить в построителе отчетов**, **Загрузить** или **Заменить**.  
  
![ssRSdataset-Properties](../reporting-services/media/ssrsdataset-properties.png)  
  
## <a name="caching"></a>Caching
  
Имеются несколько вариантов кэширования данных для набора данных. Начать можно с простого выбора.  
  
1.  Параметр**Всегда запускать этот отчет с самыми последними данными** будет выдавать запросы к источнику данных.  
  
2.  Параметр**Кэшировать копии этого отчета и использовать их в случае доступности** будет помещать временную копию данных в кэш для использования с элементами, которые используют этот набор данных. Как правило, кэширование позволяет повысить производительность, поскольку вместо повторного выполнения запроса к набору данных возвращаются данные из кэша.  
  
![ssRSDataset-Caching1](../reporting-services/media/ssrsdataset-caching1.png)  
  
При выборе параметра **Кэшировать копии этого отчета и использовать их в случае доступности** появятся дополнительные параметры.  
  
![ssRSDataset-Caching2](../reporting-services/media/ssrsdataset-caching2.png)  
  
### <a name="cache-expiration"></a>Срок действия кэша  
  
Вы можете выбирать, должен ли закончиться срок действия кэша для общего набора данных по истечении определенного времени или по расписанию. Возможно использование общего расписания.  
  
![ssRSDataset-Caching3](../reporting-services/media/ssrsdataset-caching3.png)  
  
> [!NOTE]
> Настройка срока действия не обновляет кэш. Без плана обновления кэша данные будут обновляться при следующем выполнении набора данных.  
  
### <a name="cache-refresh-plans"></a>План обновления кэша  
  
Раздел "План обновления кэша" позволяет создавать расписания, предназначенные для предварительной загрузки в кэш временных копий данных для общего набора данных. План обновления включает расписание и параметр, позволяющий указать или переопределить значения для параметров. Нельзя переопределить значения для параметров, которые отмечены как доступные только для чтения. Можно создать и использовать несколько планов обновления.   
  
Назначения ролей по умолчанию, которые позволяют добавлять, удалять и изменять общие наборы данных для планов обновления кэша: "Диспетчер содержимого", "Мои отчеты" и "Издатель".  
  
После применения одного из указанных выше параметров кэширования можно определить план обновления кэша. Для этого выберите ссылку **Управление планами обновления** , которая появится после применения параметров кэша. Откроется страница плана обновления кэша.   
  
Чтобы создать новый план обновления кэша, выберите **Создать план обновления кэша**. Затем можно ввести имя для плана и задать расписание. Если для набора данных определены параметры, они отобразятся в списке и вы сможете указать их значения, если только они не помечены как доступные только для чтения.  
  
После завершения можно нажать кнопку **Создать план обновления кэша**.  
  
![ssRSDataset-Caching4](../reporting-services/media/ssrsdataset-caching4.png)  
  
> [!NOTE]
> Для создания плана обновления кэша должен быть запущен агент SQL Server.  
  
Затем можно **изменить** или **удалить** планы из списка. Параметр **Новый на основе существующего** доступен, когда выбран один и только один план обновления кэша. При выборе этого параметра создаваемый план обновления будет скопирован из исходного плана. Страница плана обновления кэша открывается предварительно заполненная подробными сведениями выбранного плана. Затем можно изменить параметры плана обновления и сохранить план с новым описанием.  

Остались вопросы? [Посетите форум служб Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231).
