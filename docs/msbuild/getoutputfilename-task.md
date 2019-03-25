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
ms.author: Michael.Blome
ms.workload:
- multiple
ms.openlocfilehash: ee44e891c8c5f6a95971cade0536b2a5ec5b4688
ms.sourcegitcommit: 4ffb7be5384ad566ce46538032bf8561754c61a4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2019
ms.locfileid: "58070492"
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