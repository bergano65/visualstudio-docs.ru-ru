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
- MSBuild (C++), GetOutputFileName task
- GetOutputFileName task (MSBuild (C++))
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: 9733aae5e53948cdf07d62f62cd7ca5f930d08a3
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747299"
---
# <a name="getoutputfilename-task"></a>Задача GetOutputFileName

Задача вспомогательного приложения для извлечения имени выходного файла для cl и других средств, которые позволяют указывать только выходной каталог или полное имя файла.

## <a name="parameters"></a>Параметры

В следующей таблице описаны параметры задачи **GetOutputFileName**.

|Параметр|ОПИСАНИЕ|
|---------------|-----------------|
|**OutputExtension**|Обязательный параметр **string**.|
|**OutputFile**|Необязательный параметр вывода типа **string**.|
|**OutputPath**|Необязательный параметр типа **string**.|
|**SourceFile**|Обязательный параметр **string**.|

## <a name="see-also"></a>См. также

[Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)