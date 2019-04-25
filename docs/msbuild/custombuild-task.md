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
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: 197128fadb660ab06686d13ec304a5d9d1698070
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62778141"
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