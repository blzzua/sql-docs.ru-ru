---
title: "Объекты, создаваемые в издателе Oracle | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
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
- Oracle publishing [SQL Server replication], objects created
ms.assetid: c58a124b-4da7-46e2-9292-af8ce9e6664b
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 56222d5ef294a5515563a441819b5bd63b09e2ef
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/08/2018
---
# <a name="objects-created-on-the-oracle-publisher"></a>Objects Created on the Oracle Publisher
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Репликация[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] устанавливает объекты базы данных на издателе Oracle для включения отслеживания и перенаправления изменений ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] не устанавливает никаких двоичных файлов на издателе Oracle). В следующей таблице перечисляются объекты, которые создаются на издателе Oracle, если он определяется на распространителе [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] как издатель. Описания объектов предоставляются только в информационных целях. Не следует изменять эти объекты.  
  
|Имени объекта|Тип объекта|Description|  
|-----------------|-----------------|-----------------|  
|HREPL_ArticleNlog_V|Table|Таблица отслеживания изменений, используемая для хранения данных об изменениях, выполненных в опубликованной таблице. Таблица отслеживания изменений создается для каждой опубликованной таблицы.|  
|HREPL_Changes|Table|Внутренняя таблица, используемая заданием «Набор транзакций» для определения количества изменений, ожидающих назначения в набор транзакций. Дополнительные сведения об этом задании см. в статье [Настройка производительности для издателей Oracle](../../../relational-databases/replication/non-sql/performance-tuning-for-oracle-publishers.md).|  
|HREPL_Distributor|Table|Таблица состояния распространителя, используемая для сохранения данных о распространителе [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , связанном с издателем Oracle.|  
|HREPL_Event|Table|Таблица событий, используемая для синхронизации моментальных снимков и запросов количества строк.|  
|HREPL_Mutex|Table|Таблица, используемая для обеспечения того, чтобы пакетная процедура PopulatePollTable не выполнялась одновременно агентом чтения журнала и заданием базы данных.|  
|HREPL_Poll|Table|Таблица, используемая для идентификации записей таблицы журнала, связанных с наборами изменений опубликованных таблиц.|  
|HREPL_PublishedTables|Table|Таблица, содержащая по одной записи для каждой статьи в публикации транзакций.|  
|HREPL_Publisher|Table|Таблица состояния издателя, используемая для хранения специальных данных издателя.|  
|HREPL_SchemaFilter|Table|Таблица, содержащая схемы, не отображаемые при публикации при помощи мастера создания публикаций.|  
|HREPL_XactsetCreateTimes|Table|Таблица, содержащая значения времени создания, связанные с каждым набором транзакций.|  
|HREPL_XactsetJob|Table|Таблица с текущими установками параметров для задания Xactset.|  
|HREPL_Poll|Последовательность|Последовательность, используемая для создания идентификаторов опроса.|  
|HREPL_Seq|Последовательность|Последовательность, используемая для упорядочивания команд изменений.|  
|HREPL_Stmt|Последовательность|Последовательность, используемая для создания идентификаторов инструкций.|  
|HREPL|Пакет и тело пакета|Пакет издателя поддерживает код, созданный на издателе.|  
|MSSQLSERVERDISTRIBUTOR|Открытый синоним|Открытый синоним для таблицы HREPL_Distributor. Если распространитель настраивается для использования с издателем Oracle и этот синоним уже существует в базе данных, то этот синоним удаляется и создается повторно.<br /><br /> При удалении открытого синонима и пользователя настроенной репликации Oracle с параметром CASCADE удаляются все объекты репликации из издателя Oracle.|  
|HREPL_Len_I_J_K|Компонент|Функция, определяемая вне кода пакета публикации Oracle и используемая для запроса длины столбца LONG (этот запрос используется при создании параметризованных команд для таблиц с опубликованными столбцами LONG). Функция создается для каждой опубликованной таблицы со столбцом LONG.|  
|HREPL_DropPublisher|Процедура|Процедура, определяемая вне кода пакета публикации Oracle и используемая для удаления издателя Oracle.|  
|HREPL_ExecuteCommand|Процедура|Процедура, определяемая вне кода пакета публикации Oracle и используемая для выполнения команды на издателе.|  
|HREPL_ArticleN_Trigger_Row|Триггер|Триггер, создаваемый для каждой опубликованной таблицы и используемый для отслеживания изменений строк.|  
|HREPL_ArticleN_Trigger_Stmt|Триггер|Триггер, создаваемый для каждой опубликованной таблицы и используемый для отслеживания изменений на уровне инструкций.|  
|HREPL_Article_I_J|Просмотр|Представление, создаваемое для каждой опубликованной таблицы и используемое для запроса опубликованной таблицы.|  
|HREPL_Log_I_J_K|Просмотр|Представление, создаваемое для каждой опубликованной таблицы и используемое для запроса таблицы отслеживания изменений.|  
  
## <a name="see-also"></a>См. также:  
 [Настройка издателя Oracle](../../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)   
 [Глоссарий терминов по публикации Oracle](../../../relational-databases/replication/non-sql/glossary-of-terms-for-oracle-publishing.md)   
 [Обзор публикации Oracle](../../../relational-databases/replication/non-sql/oracle-publishing-overview.md)  
  
  
