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
author: corob-msft
ms.author: corob
ms.workload:
- multiple
ms.openlocfilehash: bfa60ff0f7e4060f5725fe54bd5950d858b86a22
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/18/2020
ms.locfileid: "77272404"
---
# <a name="getoutofdateitems-task"></a>Задача GetOutOfDateItems

Задача вспомогательного приложения, которая считывает старые журналы отслеживания, записывает новые журналы отслеживания и возвращает набор неактуальных элементов.

## <a name="parameters"></a>Параметры

В представленной ниже таблице приводятся параметры задачи **GetOutOfDateItems**.

|Параметр|Description|
|---------------|-----------------|
|**CheckForInterdependencies**|Необязательный параметр типа **bool**.|
|**CommandMetadataName**|Необязательный параметр типа **string**.|
|**DependenciesMetadataName**|Необязательный параметр типа **string**.|
|**HasInterdependencies**|Необязательный параметр вывода типа **bool**.|
|**OutOfDateSources**|Необязательный параметр вывода **ITaskItem[]** .|
|**OutputsMetadataName**|Обязательный параметр **string**.|
|**Источники**|Необязательный параметр **ITaskItem[]** .|
|**TLogDirectory**|Обязательный параметр **string**.|
|**TLogNamePrefix**|Обязательный параметр **string**.|

## <a name="see-also"></a>См. также раздел

[Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)