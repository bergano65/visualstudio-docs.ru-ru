---
title: Сохранение данных | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DataRow.RowState
- DataSet.GetChanges
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- DBDirect methods
- updating data
- data [Visual Studio], saving
- TableAdapter DBDirect methods
- databases, updating
- TableAdapter.Update method
- data [Visual Studio], updating
- saving data
- updating databases
ms.assetid: 21d2b115-62e4-4ac9-a873-dcbb535b8af8
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 14ff0e62608c3e2ab0c72366d9544f1d1309737a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47571895"
---
# <a name="saving-data"></a>Сохранение данных
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Сохранение данных — процесс переноса измененных данных в модели данных приложения обратно в исходное хранилище данных, обычно реляционной базы данных SQL Server.  
  
 Обновление источника данных посредством модели данных — обычно это двухэтапный процесс. Первым шагом является обновление модели данных новыми данными — новых записей, измененных или удаленных записей. Второй шаг — чтобы сохранить изменения в модели данных в базе данных.  
  
 Ниже описываются основные понятия и задачи, связанные с сохранением данных.  
  
## <a name="related-topics"></a>См. также  
 [Сохранение данных обратно в базу данных](../data-tools/save-data-back-to-the-database.md)  
 Описывается порядок изменения в наборе данных и как набор данных отслеживает сведения об изменениях, чтобы сохранить эти изменения в базу данных.  
  
 [Сохранение данных сущностей](../data-tools/saving-entity-data.md)  
 Описывает, как сохранить изменения в [ADO.NET Entity Framework](http://msdn.microsoft.com/library/a437041f-6899-4ae7-96ce-aabf528d7205) и [служб данных WCF 4.5](http://msdn.microsoft.com/library/73d2bec3-7c92-4110-b905-11bb0462357a) приложений.