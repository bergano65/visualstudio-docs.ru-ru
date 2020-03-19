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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595349"
---
# <a name="custombuild-task"></a>Задача CustomBuild

Создает программу-оболочку для компилятора Microsoft C++ (cmd.exe). Этот класс является производным от [TrackedVCToolTask](../msbuild/trackedvctooltask-base-class.md), но не использует отслеживание файлов для обнаружения зависимостей между файлами. Все зависимости должны быть явно указаны как AdditionalDependencies, чтобы инкрементная сборка работала должным образом.

## <a name="parameters"></a>Параметры

В следующей таблице приводятся параметры задачи **CustomBuild**.

|Параметр|Description|
|---------------|-----------------|
|**BuildSuffix**|Необязательный параметр типа **string**.|
|**Источники**|Обязательный параметр **ITaskItem[]** .|
|**TrackerLogDirectory**|Необязательный параметр типа **string**.|

## <a name="see-also"></a>См. также раздел

[Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
