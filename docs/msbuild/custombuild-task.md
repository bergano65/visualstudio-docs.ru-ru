---
title: Задача CustomBuild | Документация Майкрософт
description: В этой статье описывается задача CustomBuild MSBuild, которая используется в MSBuild для поддержки настройки процесса сборки C++.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 640c1e6ae286b45f8700709829140093452a9491
ms.sourcegitcommit: bd9417123c6ef67aa2215307ba5eeec511e43e02
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/28/2020
ms.locfileid: "92796554"
---
# <a name="custombuild-task"></a>Задача CustomBuild

Создает программу-оболочку для компилятора Microsoft C++ (cmd.exe). Этот класс является производным от [TrackedVCToolTask](../msbuild/trackedvctooltask-base-class.md), но не использует отслеживание файлов для обнаружения зависимостей между файлами. Все зависимости должны быть явно указаны как AdditionalDependencies, чтобы инкрементная сборка работала должным образом.

## <a name="parameters"></a>Параметры

В следующей таблице приводятся параметры задачи **CustomBuild** .

|Параметр|Описание|
|---------------|-----------------|
|**BuildSuffix**|Необязательный параметр типа **string** .|
|**Sources**|Обязательный параметр **ITaskItem[]** .|
|**TrackerLogDirectory**|Необязательный параметр типа **string** .|

## <a name="see-also"></a>См. также

[Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
