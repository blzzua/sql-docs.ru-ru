---
title: PDOStatement::closeCursor | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8997ab61-e948-4d54-8d32-fc080d55525c
caps.latest.revision: ''
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 46f2ec56126f4c0ed03a2928671f3b32bfd4270c
ms.sourcegitcommit: 2e130e9f3ce8a7ffe373d7fba8b09e937c216386
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2018
---
# <a name="pdostatementclosecursor"></a>PDOStatement::closeCursor
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Закрывает курсор, делая возможным повторное выполнение инструкции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
bool PDOStatement::closeCursor();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
Значение true в случае успеха, в противном случае — значение false.  
  
## <a name="remarks"></a>Remarks  
closeCursor применяется, когда для параметра соединения MultipleActiveResultSets задано значение false.  Дополнительные сведения о параметре подключения MultipleActiveResultSets см. в разделе [как: отключить несколько активных результирующих наборов (MARS)](../../connect/php/how-to-disable-multiple-active-resultsets-mars.md).  
  
Вместо вызова closeCursor можно просто задать для дескриптора инструкции значение NULL.  
  
Поддержка PDO была добавлена в версии 2.0 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
## <a name="example"></a>Пример  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "", array('MultipleActiveResultSets' => false ) );  
  
$stmt = $conn->prepare('SELECT * FROM Person.ContactType');  
  
$stmt2 = $conn->prepare('SELECT * FROM HumanResources.Department');  
  
$stmt->execute();  
  
$result = $stmt->fetch();  
print_r($result);  
  
$stmt->closeCursor();  
  
$stmt2->execute();  
$result = $stmt2->fetch();  
print_r($result);  
?>  
```  
  
## <a name="see-also"></a>См. также  
[Класс PDOStatement](../../connect/php/pdostatement-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
