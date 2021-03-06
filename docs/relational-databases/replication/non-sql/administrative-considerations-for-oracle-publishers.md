---
title: "Вопросы управления издателями Oracle | Документация Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Oracle publishing [SQL Server replication], administrative considerations
- administering replication, Oracle publishing
ms.assetid: cfd81fb5-419b-4a1b-97c4-be7c9d4ee289
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3ad357077cc60441ce91a0b4c265a7a31d051243
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/08/2018
---
# <a name="administrative-considerations-for-oracle-publishers"></a>Вопросы управления издателями Oracle
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  После завершения настройки издателя Oracle и установки механизмов отслеживания изменения репликаций администраторы систем баз данных Oracle могут использовать стандартные служебные программы Oracle и выполнять типичные задачи системного администратора. Однако необходимо знать о влиянии некоторых административных задач на публикуемые данные.  
  
 За исключением удаления или изменения столбца, публикуемого для репликации, либо удаления или изменения любого объекта репликации, эти вопросы не относятся к публикациям моментальных снимков.  
  
## <a name="importing-and-loading-data"></a>Импорт и загрузка данных  
 Триггеры используются для отслеживания изменений публикаций транзакций в Oracle. Изменения опубликованных таблиц можно реплицировать на подписчики, только если триггеры репликации запускаются, когда происходит обновление, вставка или удаление. В служебных программах Oracle Import и SQL*Loader имеются параметры, которые влияют на запуск триггеров при вставке строк в реплицированные таблицы с помощью этих программ.  
  
### <a name="oracle-import"></a>Служебная программа Oracle Import  
 С помощью программы Oracle Import можно присвоить параметру **ignore** значение 'y' или 'n' (по умолчанию 'n'). Если параметр **ignore** имеет значение 'n', таблица во время импорта удаляется и создается заново. Таким образом удаляются триггеры репликации и отключается репликация. Если параметр **ignore** имеет значение 'y', операция импорта попытается загрузить строки в существующую таблицу, что запускает триггеры репликации. Поэтому при импорте реплицированной таблицы с помощью инструмента Import убедитесь, что параметру **ignore** присвоено значение 'y'.  
  
### <a name="sqlloader"></a>Служебная программа SQL*Loader  
 С помощью программы SQL\*Loader можно присвоить параметру **direct** значение true или false (по умолчанию — false). Если параметр **direct** имеет значение 'false', строки вставляются с использованием обычных инструкций INSERT, что запускает триггеры репликации. Если параметр **direct** имеет значение 'true', загрузка оптимизируется, а триггеры не запускаются. Поэтому при загрузке реплицированной таблицы с помощью инструмента SQL*Loader убедитесь, что параметру **direct** присвоено значение 'false'.  
  
## <a name="making-changes-to-published-objects"></a>Внесение изменений в опубликованные объекты  
 Для следующих действий не требуются особые соображения:  
  
-   Перестроение индексов в опубликованных таблицах.  
  
-   Добавление пользовательских триггеров у опубликованную таблицу.  
  
 Следующее действие требует остановки всех операций в опубликованных таблицах:  
  
-   Перемещение опубликованной таблицы.  
  
 Для следующих действий требуется удалить публикацию, выполнить нужное действие, а затем заново создать эту публикацию:  
  
-   Усечение опубликованной таблицы.  
  
-   Переименование опубликованной таблицы.  
  
-   Добавление столбца в опубликованную таблицу.  
  
-   Удаление или изменение столбца, опубликованного для репликации.  
  
-   Выполнение операций, не регистрируемых в журналах.  
  
## <a name="dropping-or-modifying-replication-objects"></a>Удаление или изменение объектов репликации  
 Необходимо удалить и заново сконфигурировать издателя, если удаляются или изменяются любые таблицы отслеживания, триггеры, последовательности или хранимые процедуры. Неполный список этих объектов собран в статье [Объекты, создаваемые на издателе Oracle](../../../relational-databases/replication/non-sql/objects-created-on-the-oracle-publisher.md).  
  
 Сведения об удалении и повторной настройке издателя см. в подразделе «Изменения, требующие повторной настройки издателя» раздела [Troubleshooting Oracle Publishers](../../../relational-databases/replication/non-sql/troubleshooting-oracle-publishers.md).  
  
## <a name="see-also"></a>См. также:  
 [Настройка издателя Oracle](../../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)   
 [Рекомендации по структуре и ограничения для издателей Oracle](../../../relational-databases/replication/non-sql/design-considerations-and-limitations-for-oracle-publishers.md)   
 [Обзор публикации Oracle](../../../relational-databases/replication/non-sql/oracle-publishing-overview.md)  
  
  
