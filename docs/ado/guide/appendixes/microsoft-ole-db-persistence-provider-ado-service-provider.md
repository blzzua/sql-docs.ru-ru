---
title: "Поставщик Microsoft OLE DB сохраняемости (поставщик службы ADO) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- providers [ADO], OLE DB persistence provider
- persistence provider [ADO]
- OLE DB persistence provider [ADO]
ms.assetid: e75ef0dc-2016-4fcc-8918-23311c0d4e02
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 30df806429167550cdf39f064e349e46dd692502
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="microsoft-ole-db-persistence-provider-overview"></a>Общие сведения о поставщике Microsoft OLE DB сохраняемости
Поставщик сохраняемости Microsoft OLE DB позволяет сохранить [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта в файл и последующее восстановление, **записей** объекта из файла. Сведения о схеме, данные, а отложенные изменения сохраняются.

 Можно сохранить **записей** в собственный формат дополнительные данные таблицы граммы (ADTG) или откройте формате расширяемого языка разметки (XML).

## <a name="provider-keyword"></a>Ключевое слово поставщика
 Для вызова этого поставщика, укажите следующие ключевое слово и значение в строке подключения.

```
"Provider=MSPersist"
```

## <a name="errors"></a>ошибки
 В приложении могут быть обнаружены следующие ошибки, выданные этим поставщиком.

|Константа|Описание|
|--------------|-----------------|
|E_BADSTREAM|Открыть файл имеет недопустимый формат (то есть, формат не ADTG или XML).|
|E_CANTPERSISTROWSET|**Записей** сохранен объект имеет характеристики, которые запретить сохранение.|

## <a name="remarks"></a>Remarks
 Поставщик сохраняемости Microsoft OLE DB предоставляет нет динамических свойств.

 В настоящее время только параметризованные иерархические **записей** невозможно сохранить объекты.

 Дополнительные сведения о хранении постоянно **записей** см [записей сохраняемости](../../../ado/guide/data/more-about-recordset-persistence.md).

 При использовании потока для открытия **набор записей,** должно быть параметры не указаны, отличной от *источника* параметр **откройте** метод.

## <a name="see-also"></a>См. также
[Поставщик Microsoft OLE DB сохраняемости (поставщик службы ADO)](../../../ado/guide/appendixes/microsoft-ole-db-persistence-provider-ado-service-provider.md)
