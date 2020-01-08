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
author: ghogen
ms.author: ghogen
ms.workload:
- multiple
ms.openlocfilehash: d95b6e7d4197487adc13050572ac31310701c759
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595349"
---
# <a name="custombuild-task"></a>Задача CustomBuild

Создает программу-оболочку для компилятора Microsoft C++ (cmd.exe). Этот класс является производным от [TrackedVCToolTask](../msbuild/trackedvctooltask-base-class.md), но не использует отслеживание файлов для обнаружения зависимостей между файлами. Все зависимости должны быть явно указаны как AdditionalDependencies, чтобы инкрементная сборка работала должным образом.

## <a name="parameters"></a>Параметры

В следующей таблице приводятся параметры задачи **CustomBuild**.

|Параметр|Описание|
|---------------|-----------------|
|**BuildSuffix**|Необязательный параметр типа **string**.|
|**Sources**|Обязательный параметр **ITaskItem[]** .|
|**TrackerLogDirectory**|Необязательный параметр типа **string**.|

## <a name="see-also"></a>См. также

[Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
