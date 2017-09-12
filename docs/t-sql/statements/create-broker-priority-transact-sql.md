---
title: "СОЗДАТЬ ПРИОРИТЕТ БРОКЕРА (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE BROKER PRIORITY
- PRIORITY_TSQL
- CREATE_BROKER_PRIORITY_TSQL
- PRIORITY
- CREATE BROKER
- BROKER_TSQL
- BROKER
- CREATE_BROKER_TSQL
- BROKER PRIORITY
- BROKER_PRIORITY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CREATE BROKER PRIORITY statement
ms.assetid: e0bbebfa-b7c3-4825-8169-7281f7e6de98
caps.latest.revision: 40
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c7a1d85cba038eb3f7ef4a4e3198485943e8e194
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="create-broker-priority-transact-sql"></a>CREATE BROKER PRIORITY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Задает уровень приоритета и набор критериев для определения диалогов компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)], которым нужно назначить уровень приоритета. Уровень приоритета назначается любой конечной точке диалога, который использует то же сочетание контрактов и службы, указанные в приоритете диалога. Приоритеты должны находиться в диапазоне от 1 (низкий) до 10 (высокий). Значение по умолчанию — 5.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
CREATE BROKER PRIORITY ConversationPriorityName  
FOR CONVERSATION  
[ SET ( [ CONTRACT_NAME = {ContractName | ANY } ]  
        [ [ , ] LOCAL_SERVICE_NAME = {LocalServiceName | ANY } ]  
        [ [ , ] REMOTE_SERVICE_NAME = {'RemoteServiceName' | ANY } ]  
        [ [ , ] PRIORITY_LEVEL = {PriorityValue | DEFAULT } ]  
       )  
]  
[;]  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *ConversationPriorityName*  
 Задает имя данного приоритета диалога. Имя должно быть уникальным в текущей базе данных и должны соответствовать правилам для [!INCLUDE[ssDE](../../includes/ssde-md.md)] [идентификаторы](../../relational-databases/databases/database-identifiers.md).  
  
 SET  
 Задает критерий для определения применимости приоритета к заданному диалогу. Если указано, НАБОР данных должен содержать хотя бы один критерий: CONTRACT_NAME, LOCAL_SERVICE_NAME, REMOTE_SERVICE_NAME или параметра PRIORITY_LEVEL. Если аргумент SET не указан, устанавливаются значения по умолчанию для всех трех критериев.  
  
 CONTRACT_NAME = {*ContractName* | **ANY**}  
 Указывает имя контракта, который будет использоваться в качестве критерия, определяющего применимость приоритета к диалогу. *ContractName* — [!INCLUDE[ssDE](../../includes/ssde-md.md)] идентификатор и необходимо указать имя контракта в текущей базе данных.  
  
 *ContractName*  
 Указывает, что приоритет диалога может применяться только к диалогам, где в инструкции BEGIN DIALOG, в которой начала диалог параметр ON CONTRACT *ContractName*.  
  
 ANY  
 Указывает, что приоритет может применяться к любому диалогу, независимо от используемого контракта.  
  
 Значение по умолчанию — ANY.  
  
 LOCAL_SERVICE_NAME = {*LocalServiceName* | **ANY**}  
 Указывает имя службы, которая будет использоваться в качестве критерия для определения применимости приоритета к конечной точке диалога.  
  
 *LocalServiceName* — [!INCLUDE[ssDE](../../includes/ssde-md.md)] идентификатор. Должно быть указано имя службы в текущей базе данных.  
  
 *LocalServiceName*  
 Указывает, что объектом применения приоритета диалога может быть:  
  
-   Любая конечная точка диалога инициатора, имя вызывающей службы совпадает *LocalServiceName*.  
  
-   Любой целевой конечной точке диалога, имя целевой службы соответствует *LocalServiceName*.  
  
 ANY  
 -   Указывает, что приоритет может применяться к любой конечной точке диалога, независимо от имени локальной службы, используемой точкой.  
  
 Значение по умолчанию — ANY.  
  
 REMOTE_SERVICE_NAME = {'*RemoteServiceName*"| **ANY**}  
 Указывает имя службы, которая будет использоваться в качестве критерия для определения применимости приоритета к конечной точке диалога.  
  
 *RemoteServiceName* — это литерал типа **nvarchar(256)**. [!INCLUDE[ssSB](../../includes/sssb-md.md)]использует сравнение байт за байтом *RemoteServiceName* строка. При сравнении учитывается регистр и не применяются текущие параметры сортировки. Целевая служба может располагаться в текущем экземпляре компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] или в удаленном экземпляре компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
 "*RemoteServiceName*"  
 Указывает, что объектом применения приоритета диалога может быть:  
  
-   Любая конечная точка диалога инициатора, имя целевой службы соответствует *RemoteServiceName*.  
  
-   Любой целевой конечной точки диалога, имя которого вызывающей службы совпадает *RemoteServiceName*.  
  
 ANY  
 Указывает, что приоритет диалога может быть применен к любой конечной точке диалога, независимо от имени удаленной службы, связанной с конечной точкой.  
  
 Значение по умолчанию — ANY.  
  
 Параметра PRIORITY_LEVEL = { *PriorityValue* | **по умолчанию** }  
 Указывает приоритет, который назначается любой конечной точке диалога, использующей контракты и службы, указанные в приоритете диалога. *PriorityValue* должно быть целым литералом в диапазоне от 1 (наименьший приоритет) до 10 (наибольший приоритет). Значение по умолчанию — 5.  
  
## <a name="remarks"></a>Замечания  
 Компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] назначает уровни приоритета конечным точкам диалога. Уровни приоритета управляют приоритетом операций, связанных с конечной точкой. У каждого диалога есть две конечные точки:  
  
-   Конечная точка — инициатор диалога связывает одну сторону диалога со службой и очередью инициатора. Конечная — точка-инициатор диалога создается во время выполнения инструкции BEGIN DIALOG. С конечной точкой — инициатором диалога связаны следующие операции:  
  
    -   отправка сообщений вызывающей службой;  
  
    -   получение сообщений из очереди инициатора;  
  
    -   получение следующей группы сообщений из очереди инициатора.  
  
-   Целевая конечная точка диалога связывает противоположную сторону диалога с целевой службой и очередью. Целевая конечная точка диалога создается, когда диалог используется для отправки сообщения в очередь цели. С целевой конечной точкой диалога связаны следующие операции:  
  
    -   получение сообщений из очереди цели;  
  
    -   отправка сообщений целевой службы;  
  
    -   получение следующей группы сообщений из очереди целевой стороны.  
  
 Во время создания конечных точек диалога компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] назначает уровни приоритета диалога. Конечная точка диалога поддерживает уровень приоритета до окончания диалога. К незавершенным диалогам не применяются новые приоритеты и изменения в текущих приоритетах.  
  
 [!INCLUDE[ssSB](../../includes/sssb-md.md)]назначает конечной точке диалога уровень приоритета приоритет диалога, контракт и критерии служб наиболее соответствуют свойствам конечной точки. В следующей таблице показан порядок соответствия.  
  
|Контракт операции|Локальная служба операции|Удаленная служба операции|  
|------------------------|-----------------------------|------------------------------|  
|*ContractName*|*LocalServiceName*|*RemoteServiceName*|  
|*ContractName*|*LocalServiceName*|ANY|  
|*ContractName*|ANY|*RemoteServiceName*|  
|*ContractName*|ANY|ANY|  
|ANY|*LocalServiceName*|*RemoteServiceName*|  
|ANY|*LocalServiceName*|ANY|  
|ANY|ANY|*RemoteServiceName*|  
|ANY|ANY|ANY|  
  
 Компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] в первую очередь ищет приоритет, в котором указаны контракт, локальная служба и удаленная служба, совпадающие с используемыми операцией. Если такой приоритет не найден, компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] ищет приоритет, в котором контракт и локальная служба совпадают с используемыми операцией, а удаленная служба указана как ANY. Процесс продолжается для всех вариантов, перечисленных в таблице порядка соответствия. Если совпадения не обнаружено, операции назначается приоритет по умолчанию — 5.  
  
 Компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] независимо назначает уровни приоритета каждой конечной точке диалога. Чтобы компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] назначал уровни приоритета и для конечной точки вызывающей стороны, и для целевой конечной точки диалога, необходимо, чтобы приоритеты диалога распространялись на обе конечные точки. Если конечная точка-инициатор диалога и целевая конечная точка диалога расположены в разных базах данных, необходимо создать приоритеты диалога в каждой базе данных. Обычно обеим конечным точкам диалога назначается одинаковый уровень приоритета, но можно указать и различные уровни приоритета.  
  
 Уровни приоритетов всегда применяются к операциям, получающим из очереди сообщения или идентификаторы групп сообщений. Уровни приоритета также применяются при передаче сообщений от одного экземпляра компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] другому.  
  
 Уровни приоритета не используются при передаче сообщений:  
  
-   из базы данных, в которой параметр базы данных HONOR_BROKER_PRIORITY установлен в значение OFF. Дополнительные сведения см. в разделе [Параметры ALTER DATABASE SET (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-set-options.md).  
  
-   между службами в одном экземпляре компонента Database Engine.  
  
-   Все [!INCLUDE[ssSB](../../includes/sssb-md.md)] операций в базе данных назначаются приоритеты по умолчанию 5, если были созданы приоритеты диалога в базе данных.  
  
## <a name="permissions"></a>Permissions  
 Разрешение на создание приоритета диалога по умолчанию предоставляется членам предопределенных ролей базы данных db_ddladmin и db_owner, а также членам предопределенной роли сервера sysadmin. Необходимо разрешение ALTER на базу данных.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-assigning-a-priority-level-to-both-directions-of-a-conversation"></a>A. Назначение уровня приоритета обоим направлениям диалога.  
 Эти два приоритета диалога обеспечивают назначение всем операциям, в которых используется контракт `SimpleContract` между службами `TargetService` и `InitiatorAService`, уровня приоритета 3.  
  
```  
CREATE BROKER PRIORITY InitiatorAToTargetPriority  
    FOR CONVERSATION  
    SET (CONTRACT_NAME = SimpleContract,  
         LOCAL_SERVICE_NAME = InitiatorServiceA,  
         REMOTE_SERVICE_NAME = N'TargetService',  
         PRIORITY_LEVEL = 3);  
CREATE BROKER PRIORITY TargetToInitiatorAPriority  
    FOR CONVERSATION  
    SET (CONTRACT_NAME = SimpleContract,  
         LOCAL_SERVICE_NAME = TargetService,  
         REMOTE_SERVICE_NAME = N'InitiatorServiceA',  
         PRIORITY_LEVEL = 3);  
```  
  
### <a name="b-setting-the-priority-level-for-all-conversations-that-use-a-contract"></a>Б. Назначение уровня приоритета всем диалогам, которые используют контракт  
 Назначает уровень приоритета `7` всем операциям, которые используют контракт с именем `SimpleContract`. Предполагается, что не существует других приоритетов, которые в которых указаны одновременно контракт `SimpleContract` и локальная или удаленная служба.  
  
```  
CREATE BROKER PRIORITY SimpleContractDefaultPriority  
    FOR CONVERSATION  
    SET (CONTRACT_NAME = SimpleContract,  
         LOCAL_SERVICE_NAME = ANY,  
         REMOTE_SERVICE_NAME = ANY,  
         PRIORITY_LEVEL = 7);  
```  
  
### <a name="c-setting-a-base-priority-level-for-a-database"></a>В. Установка базового уровня приоритета для базы данных.  
 Определяет приоритеты диалога для двух конкретных служб, а затем определяет приоритет диалога, который будет соответствовать всем другим конечным точкам диалога. Это не заменяет приоритет по умолчанию, который всегда имеет значение 5, но уменьшает число элементов, которые назначаются по умолчанию.  
  
```  
CREATE BROKER PRIORITY [//Adventure-Works.com/Expenses/ClaimPriority]  
    FOR CONVERSATION  
    SET (CONTRACT_NAME = ANY,  
         LOCAL_SERVICE_NAME = //Adventure-Works.com/Expenses/ClaimService,  
         REMOTE_SERVICE_NAME = ANY,  
         PRIORITY_LEVEL = 9);  
CREATE BROKER PRIORITY [//Adventure-Works.com/Expenses/ApprovalPriority]  
    FOR CONVERSATION  
    SET (CONTRACT_NAME = ANY,  
         LOCAL_SERVICE_NAME = //Adventure-Works.com/Expenses/ClaimService,  
         REMOTE_SERVICE_NAME = ANY,  
         PRIORITY_LEVEL = 6);  
CREATE BROKER PRIORITY [//Adventure-Works.com/Expenses/BasePriority]  
    FOR CONVERSATION  
    SET (CONTRACT_NAME = ANY,  
         LOCAL_SERVICE_NAME = ANY,  
         REMOTE_SERVICE_NAME = ANY,  
         PRIORITY_LEVEL = 3);  
```  
  
### <a name="d-creating-three-priority-levels-for-a-target-service-by-using-services"></a>Г. Создание трех уровней приоритета для целевой службы с использованием служб  
 Поддерживает системы, который предоставляет три уровня производительности: золотой (высокий), серебряный (средний) и бронзовый (низкий). Имеется один контракт, но каждый уровень располагает отдельной вызывающей службой. Все вызывающие службы связываются с центральной целевой службой.  
  
```  
CREATE BROKER PRIORITY GoldInitToTargetPriority  
    FOR CONVERSATION  
    SET (CONTRACT_NAME = SimpleContract,  
         LOCAL_SERVICE_NAME = GoldInitiatorService,  
         REMOTE_SERVICE_NAME = N'TargetService',  
         PRIORITY_LEVEL = 6);  
CREATE BROKER PRIORITY GoldTargetToInitPriority  
    FOR CONVERSATION  
    SET (CONTRACT_NAME = SimpleContract,  
         LOCAL_SERVICE_NAME = TargetService,  
         REMOTE_SERVICE_NAME = N'GoldInitiatorService',  
         PRIORITY_LEVEL = 6);  
CREATE BROKER PRIORITY SilverInitToTargetPriority  
    FOR CONVERSATION  
    SET (CONTRACT_NAME = SimpleContract,  
         LOCAL_SERVICE_NAME = SilverInitiatorService,  
         REMOTE_SERVICE_NAME = N'TargetService',  
         PRIORITY_LEVEL = 4);  
CREATE BROKER PRIORITY SilverTargetToInitPriority  
    FOR CONVERSATION  
    SET (CONTRACT_NAME = SimpleContract,  
         LOCAL_SERVICE_NAME = TargetService,  
         REMOTE_SERVICE_NAME = N'SilverInitiatorService',  
         PRIORITY_LEVEL = 4);  
CREATE BROKER PRIORITY BronzeInitToTargetPriority  
    FOR CONVERSATION  
    SET (CONTRACT_NAME = SimpleContract,  
         LOCAL_SERVICE_NAME = BronzeInitiatorService,  
         REMOTE_SERVICE_NAME = N'TargetService',  
         PRIORITY_LEVEL = 2);  
CREATE BROKER PRIORITY BronzeTargetToInitPriority  
    FOR CONVERSATION  
    SET (CONTRACT_NAME = SimpleContract,  
         LOCAL_SERVICE_NAME = TargetService,  
         REMOTE_SERVICE_NAME = N'BronzeInitiatorService',  
         PRIORITY_LEVEL = 2);  
```  
  
### <a name="e-creating-three-priority-levels-for-multiple-services-using-contracts"></a>Д. Создание трех уровней приоритета для нескольких служб с использованием контрактов  
 Поддерживает системы, который предоставляет три уровня производительности: золотой (высокий), серебряный (средний) и бронзовый (низкий). У каждого уровня имеется отдельный контракт. Эти приоритеты применяются к любым службам, на которые ссылаются диалоги, использующие контракты.  
  
```  
CREATE BROKER PRIORITY GoldPriority  
    FOR CONVERSATION  
    SET (CONTRACT_NAME = GoldContract,  
         LOCAL_SERVICE_NAME = ANY,  
         REMOTE_SERVICE_NAME = ANY,  
         PRIORITY_LEVEL = 6);  
CREATE BROKER PRIORITY SilverPriority  
    FOR CONVERSATION  
    SET (CONTRACT_NAME = SilverContract,  
         LOCAL_SERVICE_NAME = ANY,  
         REMOTE_SERVICE_NAME = ANY,  
         PRIORITY_LEVEL = 4);  
CREATE BROKER PRIORITY BronzePriority  
    FOR CONVERSATION  
    SET (CONTRACT_NAME = BronzeContract,  
         LOCAL_SERVICE_NAME = ANY,  
         REMOTE_SERVICE_NAME = ANY,  
         PRIORITY_LEVEL = 2);  
```  
  
## <a name="see-also"></a>См. также:  
 [Инструкция ALTER BROKER PRIORITY &#40; Transact-SQL &#41;](../../t-sql/statements/alter-broker-priority-transact-sql.md)   
 [BEGIN DIALOG CONVERSATION &#40; Transact-SQL &#41;](../../t-sql/statements/begin-dialog-conversation-transact-sql.md)   
 [Создание КОНТРАКТА &#40; Transact-SQL &#41;](../../t-sql/statements/create-contract-transact-sql.md)   
 [CREATE QUEUE (Transact-SQL)](../../t-sql/statements/create-queue-transact-sql.md)   
 [CREATE SERVICE (Transact-SQL)](../../t-sql/statements/create-service-transact-sql.md)   
 [DROP BROKER PRIORITY &#40; Transact-SQL &#41;](../../t-sql/statements/drop-broker-priority-transact-sql.md)   
 [GET CONVERSATION GROUP &#40; Transact-SQL &#41;](../../t-sql/statements/get-conversation-group-transact-sql.md)   
 [ПОЛУЧИТЬ &#40; Transact-SQL &#41;](../../t-sql/statements/receive-transact-sql.md)   
 [Отправить &#40; Transact-SQL &#41;](../../t-sql/statements/send-transact-sql.md)   
 [sys.conversation_priorities &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-conversation-priorities-transact-sql.md)  
  
  