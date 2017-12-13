---
title: "Массовое копирование данных Text и Image | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-bulk-copy-operations
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- bulk copy [ODBC], text data
- SQL Server Native Client ODBC driver, bulk copy
- bulk copy [ODBC], image data
- ODBC, bulk copy operations
ms.assetid: 87155bfa-3a73-4158-9d4d-cb7435dac201
caps.latest.revision: "28"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0e9e9a39634c28ea9948d2f34b08cd7401048b04
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="bulk-copying-text-and-image-data"></a>Массовое копирование данных text и image
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Большие **текст**, **ntext**, и **изображения** значения выполняются операции массового копирования с помощью [bcp_moretext](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md) функции. Кода [bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) для **текст**, **ntext**, или **изображения** столбец с *pData* значение указателя Значение NULL, показывающее, будут предоставлены данные **bcp_moretext**. Важно указать точную длину данных, предоставленных для каждого **текст**, **ntext**, или **изображения** столбца в каждой строке операции массового копирования. Если длина данных для столбца отличается от длины столбца, указанного в [bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md), используйте [bcp_collen](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-collen.md) длина присваивается соответствующее значение. A [bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md) отправляет все отличного**текст**, не являющихся-**ntext**и не-**изображения** данных; можно затем вызвать **bcp_moretext** для отправки **текст**, **ntext**, или **изображения** данные в отдельных единиц. Функции массового копирования определяют, что все данные были переданы для текущего **текст**, **ntext**, или **изображения** столбца при отправке сумма длин данных через **bcp_moretext** равняется длине, указанной при последнем **bcp_collen** или **bcp_bind**.  
  
 **bcp_moretext** не имеет параметра для определения столбца. Если существует несколько **текст**, **ntext**, или **изображения** столбцов в строке, **bcp_moretext** оперирует **текста**, **ntext**, или **изображения** столбцов, начиная со столбца с наименьшим числом порядковый номер и Далее к столбцу с наибольшим порядковым номером. **bcp_moretext** переходит от одного столбца к другому, если сумма длин переданных данных равняется длине, указанной при последнем **bcp_collen** или **bcp_bind** для текущего столбца.  
  
## <a name="see-also"></a>См. также:  
 [Выполнение операций массового копирования &#40; ODBC &#41;](../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)  
  
  