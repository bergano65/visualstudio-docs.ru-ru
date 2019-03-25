---
title: Задача MultiToolTask | Документация Майкрософт
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.multitooltask
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), MultiToolTask task
- MultiToolTask task (MSBuild (Visual C++))
author: mikeblome
ms.author: Michael.Blome
ms.workload:
- multiple
ms.openlocfilehash: bd0c5510c754043a0a55b305c671ce9487cabb49
ms.sourcegitcommit: 4ffb7be5384ad566ce46538032bf8561754c61a4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2019
ms.locfileid: "58070495"
---
# <a name="multitooltask-task"></a>Задача MultiToolTask

Нет описания.

## <a name="parameters"></a>Параметры

В представленной ниже таблице приводятся параметры задачи **MultiToolTask**.

|Параметр|Описание|
|---------------|-----------------|
|**EnvironmentVariablesToSet**|Необязательный параметр типа **string[]**.|
|**SemaphoreProcCount**|Необязательный параметр типа **string**.|
|**SchedulerFunction**|Необязательный параметр типа **string**.|
|**SchedulerVerbose**|Необязательный параметр типа **bool**.|
|**Sources**|Обязательный параметр **ITaskItem[]**.|
|**TaskAssemblyName**|Необязательный параметр типа **string**.|
|**TaskName**|Обязательный параметр **string**.|
|**TrackerLogDirectory**|Обязательный параметр **string**.|

## <a name="see-also"></a>См. также

[Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)