---
title: Задача GetOutOfDateItems | Документация Майкрософт
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.getoutofdateitems
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), GetOutOfDateItems task
- GetOutOfDateItems task (MSBuild (Visual C++))
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: e3393dd7e81fa98c49dd09a32457171286f88f18
ms.sourcegitcommit: d78821f8c353e0102b1554719f549f32dffac71b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58514980"
---
# <a name="getoutofdateitems-task"></a>Задача GetOutOfDateItems

Задача вспомогательного приложения, которая считывает старые журналы отслеживания, записывает новые журналы отслеживания и возвращает набор неактуальных элементов.

## <a name="parameters"></a>Параметры

В представленной ниже таблице приводятся параметры задачи **GetOutOfDateItems**.

|Параметр|Описание|
|---------------|-----------------|
|**CheckForInterdependencies**|Необязательный параметр типа **bool**.|
|**CommandMetadataName**|Необязательный параметр типа **string**.|
|**DependenciesMetadataName**|Необязательный параметр типа **string**.|
|**HasInterdependencies**|Необязательный параметр вывода типа **bool**.|
|**OutOfDateSources**|Необязательный параметр вывода **ITaskItem[]**.|
|**OutputsMetadataName**|Обязательный параметр **string**.|
|**Sources**|Необязательный параметр **ITaskItem[]**.|
|**TLogDirectory**|Обязательный параметр **string**.|
|**TLogNamePrefix**|Обязательный параметр **string**.|

## <a name="see-also"></a>См. также

[Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)