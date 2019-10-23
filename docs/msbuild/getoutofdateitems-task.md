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
- MSBuild (C++), GetOutOfDateItems task
- GetOutOfDateItems task (MSBuild (C++))
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: d3dc343c595606faf5bd31d7f087f7ba8d95f69e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747309"
---
# <a name="getoutofdateitems-task"></a>Задача GetOutOfDateItems

Задача вспомогательного приложения, которая считывает старые журналы отслеживания, записывает новые журналы отслеживания и возвращает набор неактуальных элементов.

## <a name="parameters"></a>Параметры

В представленной ниже таблице приводятся параметры задачи **GetOutOfDateItems**.

|Параметр|ОПИСАНИЕ|
|---------------|-----------------|
|**CheckForInterdependencies**|Необязательный параметр типа **bool**.|
|**CommandMetadataName**|Необязательный параметр типа **string**.|
|**DependenciesMetadataName**|Необязательный параметр типа **string**.|
|**HasInterdependencies**|Необязательный параметр вывода типа **bool**.|
|**OutOfDateSources**|Необязательный параметр вывода **ITaskItem[]** .|
|**OutputsMetadataName**|Обязательный параметр **string**.|
|**Sources**|Необязательный параметр **ITaskItem[]** .|
|**TLogDirectory**|Обязательный параметр **string**.|
|**TLogNamePrefix**|Обязательный параметр **string**.|

## <a name="see-also"></a>См. также

[Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)