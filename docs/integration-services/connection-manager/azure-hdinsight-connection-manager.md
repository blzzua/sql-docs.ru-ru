---
title: "Диспетчер подключений Azure HDInsight | Документы Майкрософт"
ms.custom: 
ms.date: 02/28/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: connection-manager
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SQL13.DTS.DESIGNER.AFPHDICM.F1
- SQL14.DTS.DESIGNER.AFPHDICM.F1
ms.assetid: 29d01bd9-8b38-43b1-b937-67f8aea57c0f
caps.latest.revision: 
author: Lingxi-Li
ms.author: lingxl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3ead8a391d34f3d679beee4e85aed5bacd0e1334
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="azure-hdinsight-connection-manager"></a>Диспетчер подключений Azure HDInsight
**Диспетчер подключений Azure HDInsight** позволяет пакету служб SSIS подключаться к кластеру Azure HDInsight.

**Диспетчер подключений Azure HDInsight** входит в состав [пакета дополнительных компонентов SQL Server Integration Services (SSIS) для Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).

Чтобы создать и настроить **диспетчер подключений Azure HDInsight**, выполните указанные ниже действия.

1. В диалоговом окне **Добавление диспетчера соединений со службами SSIS** выберите **AzureHDInsight** и щелкните **Добавить**.
2. В диалоговом окне **Редактор диспетчера подключений Azure HDInsight** укажите **DNS-имя кластера** (без префикса протокола), **имя пользователя** и **пароль** для кластера HDInsight, к которому необходимо подключиться.
3. Чтобы закрыть диалоговое окно, нажмите кнопку **ОК** .
4. Свойства созданного диспетчера соединений можно просмотреть в окне **Свойства** .
