---
title: Просмотр отчетов тестовый случай (SybaseToSQL) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-sybase
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
- Tester Component,Test Case Reports
ms.assetid: cb75d281-43ef-4f4a-b754-2c4ee3b62ae7
caps.latest.revision: 5
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: fe87892c50992968da7ada9b5a3b33a34442fbe6
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2018
---
# <a name="viewing-test-case-reports-sybasetosql"></a>Просмотр отчетов тестовый случай (SybaseToSQL)
В отчете тестовый случай отображаются результаты проверки и тестирования Общие сведения. В случае сбоя теста также отображаются сведения об все несоответствующие данные в проверенный объектов.  
  
## <a name="report-structure"></a>Структура отчета  
Верхней части отчета показаны эти статистические данные:  
  
-   Общее число объектов протестированных и количество объектов, для которых проверка выполнена успешно.  
  
-   Общее число проверенных таблиц и внешних ключей и количество таблиц и внешние ключи, которые успешно совпадают.  
  
-   Время начала, время окончания тестового случая и общее время, затраченное на выполнение.  
  
Оставшаяся часть отчета показывает сведения в четырех категорий:  
  
**Необходимые условия ошибок**  
Показывает все ошибки, появившиеся в **необходимые компоненты** шаг. Как правило он пропускается.  
  
**Инициализация**  
Показывает состояние выполнения как **успех** или **сбоя**.  
  
**Объекты результатов теста**  
Сравнение результатов (успех или сбой) и несоответствий, которые SSMA тестировщик обнаружил в случае сбоя.  
  
**Завершение**  
Показывает состояние выполнения как **успех** или **сбоя**.  
  
## <a name="see-also"></a>См. также  
[Выполнение тестовых случаев &#40;SybaseToSQL&#41;](../../ssma/sybase/running-test-cases-sybasetosql.md)  
[Тестирование перенесенные объекты базы данных &#40;SybaseToSQL&#41;](../../ssma/sybase/testing-migrated-database-objects-sybasetosql.md)  
  
