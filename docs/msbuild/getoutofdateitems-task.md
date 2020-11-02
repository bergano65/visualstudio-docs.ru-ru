---
title: Задача GetOutOfDateItems | Документация Майкрософт
description: Используйте вспомогательную задачу GetOutOfDateItems MSBuild для чтения и записи журналов транзакций (TLOG) и возврата неактуальных наборов элементов.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 6cc80d4e1aa3580e0185460d19f78e9737b73220
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436820"
---
# <a name="getoutofdateitems-task"></a>Задача GetOutOfDateItems

Задача вспомогательного приложения, которая считывает старые журналы отслеживания, записывает новые журналы отслеживания и возвращает набор неактуальных элементов.

## <a name="parameters"></a>Параметры

В представленной ниже таблице приводятся параметры задачи **GetOutOfDateItems** .

|Параметр|Описание|
|---------------|-----------------|
|**CheckForInterdependencies**|Необязательный параметр типа **bool** .|
|**CommandMetadataName**|Необязательный параметр типа **string** .|
|**DependenciesMetadataName**|Необязательный параметр типа **string** .|
|**HasInterdependencies**|Необязательный параметр вывода типа **bool** .|
|**OutOfDateSources**|Необязательный параметр вывода **ITaskItem[]** .|
|**OutputsMetadataName**|Обязательный параметр **string** .|
|**Источники**|Необязательный параметр **ITaskItem[]** .|
|**TLogDirectory**|Обязательный параметр **string** .|
|**TLogNamePrefix**|Обязательный параметр **string** .|

## <a name="see-also"></a>См. также

[Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)