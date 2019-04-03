---
title: Задача GetOutputFileName | Документация Майкрософт
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.getoutputfilename
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), GetOutputFileName task
- GetOutputFileName task (MSBuild (Visual C++))
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: c6298a512a1848622bf854d6d9ee9084309a0b4f
ms.sourcegitcommit: d78821f8c353e0102b1554719f549f32dffac71b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58514984"
---
# <a name="getoutputfilename-task"></a>Задача GetOutputFileName

Задача вспомогательного приложения для извлечения имени выходного файла для cl и других средств, которые позволяют указывать только выходной каталог или полное имя файла.

## <a name="parameters"></a>Параметры

В следующей таблице описаны параметры задачи **GetOutputFileName**.

|Параметр|Описание|
|---------------|-----------------|
|**OutputExtension**|Обязательный параметр **string**.|
|**OutputFile**|Необязательный параметр вывода типа **string**.|
|**OutputPath**|Необязательный параметр типа **string**.|
|**SourceFile**|Обязательный параметр **string**.|

## <a name="see-also"></a>См. также

[Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)