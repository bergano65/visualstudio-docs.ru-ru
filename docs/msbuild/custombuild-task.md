---
title: Задача CustomBuild | Документация Майкрософт
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.custombuild
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), CustomBuild task
- CustomBuild task (MSBuild (C++))
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: 678068d1b6acc055fa65e6d0305b07152ed28695
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748101"
---
# <a name="custombuild-task"></a>Задача CustomBuild

Создает программу-оболочку для компилятора Microsoft C++ (cmd.exe). Этот класс является производным от [TrackedVCToolTask](../msbuild/trackedvctooltask-base-class.md), но не использует отслеживание файлов для обнаружения зависимостей между файлами. Все зависимости должны быть явно указаны как AdditionalDependencies, чтобы инкрементная сборка работала должным образом.

## <a name="parameters"></a>Параметры

В следующей таблице приводятся параметры задачи **CustomBuild**.

|Параметр|ОПИСАНИЕ|
|---------------|-----------------|
|**BuildSuffix**|Необязательный параметр типа **string**.|
|**Sources**|Обязательный параметр **ITaskItem[]** .|
|**TrackerLogDirectory**|Необязательный параметр типа **string**.|

## <a name="see-also"></a>См. также

[Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
