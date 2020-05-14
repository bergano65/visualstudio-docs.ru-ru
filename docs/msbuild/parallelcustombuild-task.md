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
- MSBuild (C++), ParallelCustomBuild task
- ParallelCustomBuild task (MSBuild (C++))
author: corob-msft
ms.author: corob
ms.workload:
- multiple
ms.openlocfilehash: 0d8a171d393f629d0b6ab3a7fc61ad37862b0da1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/18/2020
ms.locfileid: "77279262"
---
# <a name="parallelcustombuild-task"></a>Задача ParallelCustomBuild

Выполняет параллельные экземпляры [задачи CustomBuild](../msbuild/custombuild-task.md).

## <a name="parameters"></a>Параметры

В следующей таблице описаны параметры задачи **ParallelCustomBuild**.

|Параметр|Description|
|---------------|-----------------|
|**BreakOnFirstFailure**|Необязательный параметр типа **bool**.|
|**MaxItemsInBatch**|Необязательный параметр типа **int**.|
|**MaxProcesses**|Необязательный параметр типа **int**.|
|**Источники**|Обязательный параметр **ITaskItem[]** .|

## <a name="see-also"></a>См. также раздел

[Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)