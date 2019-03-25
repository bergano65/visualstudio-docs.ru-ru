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
- MSBuild (Visual C++), CustomBuild task
- CustomBuild task (MSBuild (Visual C++))
author: mikeblome
ms.author: Michael.Blome
ms.workload:
- multiple
ms.openlocfilehash: 183cdefbca29db486b84cb61f90501507e298838
ms.sourcegitcommit: 4ffb7be5384ad566ce46538032bf8561754c61a4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2019
ms.locfileid: "58070474"
---
# <a name="custombuild-task"></a>Задача CustomBuild

Создает программу-оболочку для компилятора Visual C++ (cmd.exe).

## <a name="parameters"></a>Параметры

В следующей таблице приводятся параметры задачи **CustomBuild**.

|Параметр|Описание|
|---------------|-----------------|
|**BuildSuffix**|Необязательный параметр типа **string**.|
|**Sources**|Обязательный параметр **ITaskItem[]**.|
|**TrackerLogDirectory**|Необязательный параметр типа **string**.|

## <a name="see-also"></a>См. также

[Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)