---
title: "sp_helparticle (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_helparticle_TSQL
- sp_helparticle
helpviewer_keywords:
- sp_helparticle
ms.assetid: 9c4a1a88-56f1-45a0-890c-941b8e0f0799
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 823862d782cafd605dd7f4686dcdb3b4baa6a0b8
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="sphelparticle-transact-sql"></a>sp_helparticle (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Отображает сведения о статье. Эта хранимая процедура выполняется на издателе в базе данных публикации. Для издателей Oracle данная хранимая процедура выполняется распространителем для любой базы данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helparticle [ @publication = ] 'publication'   
    [ , [ @article = ] 'article' ]  
    [ , [ @returnfilter = ] returnfilter ]  
    [ , [ @publisher = ] 'publisher' ]  
    [ , [ @found = ] found OUTPUT ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@publication =**] **"***публикации***"**  
 Имя публикации. *Публикация* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@article=**] **"***статьи***"**  
 Имя статьи в публикации. *статья* — **sysname**, значение по умолчанию  **%** . Если *статьи* — не указан, возвращаются сведения по всем статьям публикации.  
  
 [  **@returnfilter=**] *returnfilter*  
 Указывает, должен ли происходить возврат предложения фильтра. *returnfilter* — **бит**, значение по умолчанию **1**, возвращающий предложение фильтра.  
  
 [  **@publisher** =] **"***издатель***"**  
 Указывает значение, отличное от[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя. *издатель* — **sysname**, значение по умолчанию NULL.  
  
> [!NOTE]  
>  *издатель* не следует указывать при требуемые данные по статье были опубликованы по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя.  
  
 [  **@found=** ] *найти* выходных данных  
 Только для внутреннего применения.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**Идентификатор статьи**|**int**|Идентификатор статьи.|  
|**Имя статьи**|**sysname**|Имя статьи.|  
|**базовый объект**|**nvarchar(257)**|Имя базовой таблицы, заданной в статье или в хранимой процедуре.|  
|**целевой объект**|**sysname**|Имя целевой таблицы (таблицы подписки).|  
|**объект синхронизации**|**nvarchar(257)**|Имя представления, определяющего опубликованную статью.|  
|**type**|**smallint**|Тип статьи:<br /><br /> **1** = на основе журнала.<br /><br /> **3** = на основе журнала с ручным фильтром.<br /><br /> **5** = на основе журнала с ручным просмотром.<br /><br /> **7** = на основе журнала с ручным фильтром и ручным просмотром.<br /><br /> **8** = выполнение хранимой процедуры.<br /><br /> **24** = Выполнение сериализуемой хранимой процедуры.<br /><br /> **32** = хранимая процедура (только схема).<br /><br /> **64** = представление (только схема).<br /><br /> **96** = Агрегатная функция (только схема).<br /><br /> **128** = функция (только схема).<br /><br /> **257** = индексированное представление на основе журнала.<br /><br /> **259** = индексированное представление на основе журнала с ручным фильтром.<br /><br /> **261** = основанных на журнале индексированного представления с представлением вручную.<br /><br /> **263** = основанных на журнале индексированного представления с фильтрацией вручную и представлением вручную.<br /><br /> **320** = индексированное представление (только схема).<br /><br />|  
|**status**|**tinyint**|Может быть [& (побитовое и)](../../t-sql/language-elements/bitwise-and-transact-sql.md) результат одного или более свойств статьи:<br /><br /> **0x00** = [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]<br /><br /> **0x01** = статья активна.<br /><br /> **0x08** = включить имя столбца в инструкции insert.<br /><br /> **0x16** = использовать параметризованные инструкции.<br /><br /> **0x32** = использовать параметризованные инструкции и включить имя столбца в инструкции insert.|  
|**фильтр**|**nvarchar(257)**|Хранимая процедура, используемая для горизонтальной фильтрации таблиц. Данная хранимая процедура должна быть создана с помощью предложения FOR REPLICATION.|  
|**Описание**|**nvarchar(255)**|Описание статьи.|  
|**insert_command**|**nvarchar(255)**|Тип команды репликации, используемый при репликационной вставке в статьи таблицы. Дополнительные сведения см. в статье [Указание способа распространения изменений для статей транзакций](../../relational-databases/replication/transactional/transactional-articles-specify-how-changes-are-propagated.md).|  
|**update_command**|**nvarchar(255)**|Тип команды репликации, используемый при репликационном обновлении статей таблицы. Дополнительные сведения см. в статье [Указание способа распространения изменений для статей транзакций](../../relational-databases/replication/transactional/transactional-articles-specify-how-changes-are-propagated.md).|  
|**delete_command**|**nvarchar(255)**|Тип команды репликации, используемый при репликационном удалении в статьях таблицы. Дополнительные сведения см. в статье [Указание способа распространения изменений для статей транзакций](../../relational-databases/replication/transactional/transactional-articles-specify-how-changes-are-propagated.md).|  
|**Путь скрипта создания**|**nvarchar(255)**|Путь и имя скрипта схемы статьи, используемого для создания целевых таблиц.|  
|**вертикальной секции**|**bit**|Является ли вертикальное секционирование включено для данной статьи; При задании значения **1** означает, что вертикальное секционирование включено.|  
|**pre_creation_cmd**|**tinyint**|Команда, выполняемая перед инструкциями DROP TABLE, DELETE TABLE и TRUNCATE.|  
|**filter_clause**|**ntext**|Предложение WHERE задает горизонтальную фильтрацию.|  
|**schema_option**|**binary(8)**|Битовая карта параметра создания схемы для заданной статьи. Полный список **schema_option** значения, в разделе [sp_addarticle &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md).|  
|**dest_owner**|**sysname**|Имя владельца целевого объекта.|  
|**Этот аргумент**|**sysname**|Владелец исходного объекта.|  
|**unqua_source_object**|**sysname**|Имя исходного объекта без учета имени его владельца.|  
|**sync_object_owner**|**sysname**|Владелец представления, определяющего опубликованную статью. .|  
|**unqualified_sync_object**|**sysname**|Имя представления, определяющего опубликованную статью, без учета имени владельца.|  
|**filter_owner**|**sysname**|Владелец фильтра.|  
|**unqua_filter**|**sysname**|Имя фильтра без учета имени его владельца.|  
|**Аргумент auto_identity_range**|**int**|Флаг, показывающий включение автоматической обработки диапазонов идентификаторов для публикации при ее создании. **1** означает, что включен автоматический диапазон идентификаторов; **0** означает она будет отключена.|  
|**publisher_identity_range**|**int**|Диапазон размер диапазона идентификаторов на издателе, если аргументу статьи *identityrangemanagementoption* значение **автоматически** или **auto_identity_range** значение  **значение true,**.|  
|**Аргумент identity_range**|**bigint**|Диапазон размер диапазона идентификаторов на подписчике, если аргументу статьи *identityrangemanagementoption* значение **автоматически** или **auto_identity_range** значение  **значение true,**.|  
|**Пороговое значение**|**bigint**|Процентное значение, показывающее момент, когда агент распространителя выделяет новый диапазон идентификаторов.|  
|**identityrangemanagementoption**|**int**|Указывает способ управления диапазоном идентификаторов для статьи.|  
|**fire_triggers_on_snapshot**|**bit**|Используется в случае, когда реплицированные пользовательские триггеры срабатывают при применении исходного моментального снимка:<br /><br /> **1** = триггеры выполняются.<br /><br /> **0** = триггеры не выполняются.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_helparticle** используется в репликации моментальных снимков и репликации транзакций.  
  
## <a name="permissions"></a>Permissions  
 Только члены **sysadmin** предопределенной роли сервера **db_owner** предопределенной роли базы данных или для текущей публикации списка доступа публикации могут выполнять процедуру **sp_helparticle**.  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_helptranarticle](../../relational-databases/replication/codesnippet/tsql/sp-helparticle-transact-_1.sql)]  
  
## <a name="see-also"></a>См. также:  
 [Просмотр и изменение свойств статьи](../../relational-databases/replication/publish/view-and-modify-article-properties.md)   
 [sp_addarticle &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)   
 [sp_articlecolumn (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md)   
 [sp_changearticle (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md)   
 [sp_droparticle (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-droparticle-transact-sql.md)   
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
