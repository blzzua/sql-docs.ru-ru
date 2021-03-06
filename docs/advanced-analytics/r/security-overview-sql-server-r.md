---
title: Безопасность SQL Server машинного обучения и R | Документы Microsoft
ms.custom: ''
ms.date: 11/03/2017
ms.reviewer: ''
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.author: heidist
author: HeidiSteen
manager: cgronlun
ms.workload: Inactive
ms.openlocfilehash: 00f5572c5885fe53df8f050e1cbe8320c1256087
ms.sourcegitcommit: 059fc64ba858ea2adaad2db39f306a8bff9649c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/04/2018
---
# <a name="security-for-sql-server-machine-learning-and-r"></a>Безопасность SQL Server машинного обучения и R
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье описывается общая архитектура безопасности, используемый для подключения [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] ядра и связанных компонентов среды выполнения R базы данных. Примеры процесс обеспечения безопасности, предоставляемые для этих общих сценариев для использования R в среде предприятия:

+ выполнение функций RevoScaleR в [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] из клиента обработки и анализа данных;
+ выполнение R прямо из [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] с помощью хранимых процедур.

## <a name="security-overview"></a>Общие сведения о безопасности

Объект [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] для запуска сценариев R, которые используют данные SQL Server или выполняющихся с SQL Server в контексте требуется имя входа или учетная запись пользователя Windows. Это требование применяется к обоим [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)] и 2017 г. SQL Server [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)].

Определяет имя входа или учетной записи пользователя *субъекта безопасности*, кто может потребоваться несколько уровней доступа, в зависимости от требований сценария R:

+ Разрешение на доступ к базе данных, где включена R
+ Разрешения на чтение данных из защищенных объектов, таких как таблицы
+ Разрешение на запись новых данных в таблице, например модели или оценки результатов
+ Возможность создания новых объектов, таких как таблицы, хранимые процедуры, которые использовать R-сценарий, или пользовательские функции этого задания используйте R
+ Право, чтобы установить новые пакеты на компьютере SQL Server, то пакеты используйте R, предоставляемые группе пользователей. 

Таким образом, каждый пользователь, запустивший R с помощью кода [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] как выполнение контекста должно быть сопоставлено имя входа в базу данных. В группе безопасности SQL Server обычно проще создавать роли для управления наборами разрешений и назначить пользователей для этих ролей, а не по отдельности настроить разрешения. 

Например, предположим, что созданный код R, который выполняется на вашем ноутбуке и требуется для выполнения этого кода [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. Это можно сделать только в том случае, если выполняются следующие условия:

+ База данных должна разрешать удаленные подключения.
+ Имя входа SQL с именем и паролем, которые вы использовали в коде R, должны быть добавлены на [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] на уровне экземпляра. Если же вы используете встроенную проверку подлинности Windows, пользователь Windows, указанный в строке подключения, должен быть добавлен в качестве пользователя в экземпляр.
+ Имя входа SQL или пользователя Windows должна иметь разрешение на выполнение внешних скриптов. Обычно это разрешение может добавить только администратор базы данных.
+ Имя входа SQL или пользователь Windows должны быть добавлены в качестве пользователя с соответствующими разрешениями в каждую базу данных, где задание R выполняет одно из следующих действий:
    + извлечение данных;
    + запись или обновление данных; 
    + создание новых объектов, например таблиц или хранимых процедур.

После имени входа или учетной записи пользователя Windows были подготовлены и предоставлены необходимые разрешения, можно запустить код R на [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] , используя объект источника данных R или путем вызова хранимой процедуры. При каждом запуске R из [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], безопасность ядра базы данных возвращает контекст безопасности пользователя, запустившего задание R или выполнена хранимая процедура и управляет сопоставлениями пользователя или имени входа к защищаемым объектам. 

Таким образом все задания R, инициированные с удаленного клиента необходимо указать сведения о имени входа или пользователя в строке подключения.

## <a name="interaction-of-includessnoversionmdincludesssnoversion-mdmd-security-and-launchpad-security"></a>Взаимодействие [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] и безопасности на панели запуска

Когда скрипт R выполняется в контексте компьютера [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], служба [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] получает доступную рабочую учетную запись (учетную запись локального пользователя) из пула рабочих учетных записей, установленных для внешних процессов, и использует ее для выполнения связанных задач. 

Например, если вы запустите задание R с помощью своих учетных данных пользователя Windows, ваша учетная запись будет сопоставлена с рабочей учетной записью панели запуска *SQLRUser01*.

После сопоставления с рабочей учетной записью [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] создаст токен пользователя, который будет использоваться для запуска процессов. 

Когда все операции [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] будут завершены, рабочая учетная запись пользователя будет помечена как свободная и вернется в пул.

Дополнительные сведения о [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)], в разделе [компоненты SQL Server для поддержки интеграции R](../../advanced-analytics/r/new-components-in-sql-server-to-support-r.md).

### <a name="implied-authentication"></a>Неявная проверка подлинности

**Неявной проверки подлинности** является термин, используемый для процесса, в которой SQL Server возвращает пользователя, учетные данные, а затем выполняет все задачи внешний скрипт от имени пользователей, при условии, что пользователь имеет необходимые разрешения в базе данных. Неявной проверки подлинности особенно важно в тех случаях, если необходимо произвести вызов ODBC вне базы данных SQL Server R-скрипта. Например код может получить более короткому списку факторов из электронной таблицы или другого источника.

Такие вызовы замыкания на себя для успешного выполнения группу, содержащую рабочих учетных записей, SQLRUserGroup, необходимо иметь разрешения «Локальный вход в систему». По умолчанию это право предоставляется для всех новых локальных пользователей, но в некоторых организациях могут применяться более строгие политики группы.

![Неявной проверки подлинности для R](media/implied-auth-rsql.png)

## <a name="security-of-worker-accounts"></a>Безопасность рабочих учетных записей

Сопоставление внешнего пользователя Windows или рабочей учетной записи входа SQL является допустимым только в течение времени существования SQL-запроса, который запускает сценарий R.

Параллельные запросы, выполняемые с тем же именем входа, сопоставляются с той же рабочей учетной записью пользователя.

Каталогами, используемыми для этих процессов, управляет [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] с помощью RLauncher, и доступ к ним ограничен. У рабочей учетной записи нет доступа к каким-либо файлам в папках (за исключением своих), но есть возможность чтения, записи или удаления дочерних элементов в сеансе рабочей папки, созданной для SQL-запроса с помощью скрипта R.

Дополнительные сведения о том, как изменить количество рабочих учетных записей, имена учетных записей или паролей учетных записей см. в разделе [изменение пула учетных записей пользователей для SQL Server машинного обучения](../../advanced-analytics/r/modify-the-user-account-pool-for-sql-server-r-services.md).

## <a name="security-isolation-for-multiple-external-scripts"></a>Изоляция безопасности для нескольких внешних скриптов

Механизм изоляции основан на учетных записях физических пользователей. Так как вспомогательные процессы запускаются для определенной языковой среды выполнения, каждая вспомогательная задача использует рабочую учетную запись, которую указала [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)]. Если для выполнения задачи требуется несколько вспомогательных процессов, как в случае параллельных запросов, то для всех связанных задач будет использоваться одна рабочая учетная запись.

При этом доступ к файлам, используемым другими рабочими учетными записями, отсутствует.
 
Если вы являетесь администратором компьютера, вы можете просмотреть каталоги, созданные для каждого процесса. Каждый каталог определяется собственным идентификатором GUID сеанса.

## <a name="see-also"></a>См. также:

[Обзор архитектуры для SQL Server машинного обучения](../../advanced-analytics/r/architecture-overview-sql-server-r.md)
