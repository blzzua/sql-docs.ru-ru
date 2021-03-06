---
title: "Выполнение тестовых случаев (OracleToSQL) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-oracle
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc208cdb-7373-4f6b-8f6c-cdff9d3dcd02
caps.latest.revision: "6"
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.workload: Inactive
ms.openlocfilehash: 6d9e4e71813ff5b092ba1b67db207abd9b1adc44
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="running-test-cases-oracletosql"></a>Выполнение тестовых случаев (OracleToSQL)
Когда SSMA тест-инженер запускает тест, он выполняет объекты, выбранные для тестирования и создает отчет о результатах проверки. Если результаты совпадают на обеих платформах, проверка выполнена успешно. Соответствие объектов между Oracle и [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] определяется в соответствии с параметрами соответствие схемы для текущего проекта SSMA.  
  
Необходимые требования для успешного завершения проверки — преобразуются и загружаются в целевой базе данных все объекты Oracle. Кроме того данные таблицы следует перенести, чтобы синхронизировать содержимое таблиц на обеих платформах.  
  
## <a name="run-test-case"></a>Выполнение тестового случая  
Чтобы запустить подготовленный тестового случая:  
  
1.  Нажмите кнопку **запуска** кнопки.  
  
2.  В **подключение к Oracle** диалоговое окно, введите сведения о соединении и нажмите кнопку **Connect**.  
  
После завершения теста создается отчет тестовых случаев. Нажмите кнопку **отчетов** кнопку, чтобы просмотреть [отчет тестовых случаев](http://msdn.microsoft.com/en-us/8da14323-9dd6-4019-bf79-3e8b972a9bc0). Результат теста (тестовый случай отчет), автоматически сохраняются в [хранилище результатов тестов](http://msdn.microsoft.com/en-us/f941cce4-d3e3-4aeb-a88a-4f101a97a9f4) для последующего использования.  
  
## <a name="test-case-execution-steps"></a>Шаги выполнения тестового случая  
  
### <a name="prerequisites"></a>предварительные требования  
SSMA тест-инженер проверяет, если выполнены все предварительные требования для выполнения тестов перед запуском теста. Если некоторые условия не соблюдены, появится сообщение об ошибке.  
  
### <a name="initialization"></a>Инициализация  
На этом этапе SSMA инженер-испытатель создает вспомогательные объекты (таблицы, триггеры и представления) в схеме SSMATESTER_ORACLE сервера Oracle. Они позволяют трассировки изменений, внесенных в затронутые объекты, выбранные для проверки.  
  
Предположим, что проверенных таблица называется USER_TABLE. Для такой таблицы из базы данных Oracle создаются следующие вспомогательные объекты.  
  
||||  
|-|-|-|  
|Имя|Тип|Description|  
|USER_TABLE$ Trg|триггер|Аудит изменений в таблице проверенных триггер.|  
|USER_TABLE$ AUD|table|Таблица сохранения строки удаляются и перезаписаны.|  
|USER_TABLE$ AUDID|table|Таблица сохранения новых и измененных строк.|  
|USER_TABLE|представление|Упрощенное представление изменения таблиц.|  
|USER_TABLE$ NEW|представление|Упрощенное представление вставленные и перезаписать строки.|  
|USER_TABLE$ NEW_ID|представление|Идентификация вставленные и измененные строки.|  
|USER_TABLE$ СТАРЫЕ|представление|Упрощенное представление строки удаляются и перезаписаны.|  
  
Следующий объект создается в схеме таблицы, проверенных на [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
||||  
|-|-|-|  
|Имя|Тип|Description|  
|USER_TABLE$ Trg|триггер|Аудит изменений в таблице проверенных триггер.|  
  
И следующие объекты создаются в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]ssmatesterdb базы данных.  
  
||||  
|-|-|-|  
|Имя|Тип|Description|  
|USER_TABLE$ Aud|table|Таблица сохранения строки удаляются и перезаписаны.|  
|USER_TABLE$ AudID|table|Таблица сохранения новых и измененных строк.|  
|USER_TABLE|представление|Упрощенное представление изменения таблиц.|  
|$ USER_TABLE новые|представление|Упрощенное представление вставленные и перезаписать строки.|  
|USER_TABLE$ new_id|представление|Идентификация вставленные и измененные строки.|  
|$ USER_TABLE старые|представление|Упрощенное представление строки удаляются и перезаписаны.|  
  
### <a name="test-object-calls"></a>Тест вызывает объект  
На этом этапе тест-инженер SSMA вызывает каждому объекту, выбранному для тестирования, сравниваются результаты и показывает отчет.  
  
### <a name="finalization"></a>Завершение  
Во время завершения инженер-испытатель SSMA очищает вспомогательные объекты, созданные в **инициализации** шаг.  
  
## <a name="next-step"></a>Следующий шаг  
[Просмотр отчетов тестовый случай &#40; OracleToSQL &#41;](../../ssma/oracle/viewing-test-case-reports-oracletosql.md)  
  
## <a name="see-also"></a>См. также:  
[Выбор и настройка объектов для тестирования &#40; OracleToSQL &#41;](../../ssma/oracle/selecting-and-configuring-objects-to-test-oracletosql.md)  
[Выбор и настройка затронутые объекты &#40; OracleToSQL &#41;](../../ssma/oracle/selecting-and-configuring-affected-objects-oracletosql.md)  
[Тестирование миграции объектов базы данных &#40; OracleToSQL &#41;](../../ssma/oracle/testing-migrated-database-objects-oracletosql.md)  
  
