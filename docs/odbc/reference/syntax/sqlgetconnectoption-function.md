---
title: Функция SQLGetConnectOption | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
apiname:
- SQLGetConnectOption
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetConnectOption
helpviewer_keywords:
- SQLGetConnectOption function [ODBC]
ms.assetid: 59cde899-7957-4b5e-8677-f34d3b859bfd
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4a2c04b150f642ff456e6dc814fb7f8a2eca9c1a
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="sqlgetconnectoption-function"></a>Функция SQLGetConnectOption
**Соответствия**  
 Появился в версии: Полное соответствие стандартам 1.0 ODBC: рекомендуется к использованию  
  
 **Сводка**  
 В ODBC 3*.x*, ODBC 2*.x* функция **SQLGetConnectOption** будет заменен **SQLGetConnectAttr**. Дополнительные сведения см. в разделе [SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md).  
  
> [!NOTE]  
>  Дополнительные сведения о том, что диспетчер драйверов преобразует эту функцию для при ODBC 2*.x* при работе с ODBC 3*.x* драйвера, в разделе [сопоставление устаревшие функции](../../../odbc/reference/appendixes/mapping-deprecated-functions.md)в приложении G: драйвер рекомендации для обеспечения обратной совместимости.  
  
> [!NOTE]  
>  Атрибут SQL_ASYNC_DBC_FUNCTION_ENABLE появились в ODBC 3.8 не поддерживается в **SQLGetConnectOption**. Приложения, использующие асинхронной операции на дескрипторе соединений необходимо использовать **SQLGetConnectAttr**.  
  
## <a name="see-also"></a>См. также:  
 [Справочник по API-интерфейса ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
