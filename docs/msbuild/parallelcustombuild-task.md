---
title: Задача ParallelCustomBuild | Документация Майкрософт
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.parallelcustombuild
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), ParallelCustomBuild task
- ParallelCustomBuild task (MSBuild (Visual C++))
author: mikeblome
ms.author: Michael.Blome
ms.workload:
- multiple
ms.openlocfilehash: 506ead6680bd9a0aaaf38d6959da02a14dfee337
ms.sourcegitcommit: 4ffb7be5384ad566ce46538032bf8561754c61a4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2019
ms.locfileid: "58070468"
---
# <a name="parallelcustombuild-task"></a>Задача ParallelCustomBuild

Выполняет параллельные экземпляры [задачи CustomBuild](../msbuild/custombuild-task.md).

## <a name="parameters"></a>Параметры

В следующей таблице описаны параметры задачи **ParallelCustomBuild**.

|Параметр|Описание|
|---------------|-----------------|
|**BreakOnFirstFailure**|Необязательный параметр типа **bool**.|
|**MaxItemsInBatch**|Необязательный параметр типа **int**.|
|**MaxProcesses**|Необязательный параметр типа **int**.|
|**Sources**|Обязательный параметр **ITaskItem[]**.|

## <a name="see-also"></a>См. также

[Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)