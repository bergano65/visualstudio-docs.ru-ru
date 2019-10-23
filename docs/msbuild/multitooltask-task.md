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
- MSBuild (C++), MultiToolTask task
- MultiToolTask task (MSBuild (C++))
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: 137fb53a46c3fa31a69602906ef53d2f65e25c4b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747234"
---
# <a name="multitooltask-task"></a>Задача MultiToolTask

Нет описания.

## <a name="parameters"></a>Параметры

В представленной ниже таблице приводятся параметры задачи **MultiToolTask**.

|Параметр|ОПИСАНИЕ|
|---------------|-----------------|
|**EnvironmentVariablesToSet**|Необязательный параметр типа **string[]** .|
|**SemaphoreProcCount**|Необязательный параметр типа **string**.|
|**SchedulerFunction**|Необязательный параметр типа **string**.|
|**SchedulerVerbose**|Необязательный параметр типа **bool**.|
|**Sources**|Обязательный параметр **ITaskItem[]** .|
|**TaskAssemblyName**|Необязательный параметр типа **string**.|
|**TaskName**|Обязательный параметр **string**.|
|**TrackerLogDirectory**|Обязательный параметр **string**.|

## <a name="see-also"></a>См. также

[Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)