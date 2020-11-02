---
title: Задача GetOutputFileName | Документация Майкрософт
description: Используйте вспомогательную задачу GetOutputFileName MSBuild, чтобы указать параметры имени выходного файла для cl.exe и других средств.
ms.custom: SEO-VS-2020
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
author: ghogen
ms.author: ghogen
ms.workload:
- multiple
ms.openlocfilehash: cb4670bb84b151332951608f7b20ef5ea44e59a3
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436787"
---
# <a name="getoutputfilename-task"></a>Задача GetOutputFileName

Задача вспомогательного приложения для извлечения имени выходного файла для cl и других средств, которые позволяют указывать только выходной каталог или полное имя файла.

## <a name="parameters"></a>Параметры

В следующей таблице описаны параметры задачи **GetOutputFileName** .

|Параметр|Описание|
|---------------|-----------------|
|**OutputExtension**|Обязательный параметр **string** .|
|**OutputFile**|Необязательный параметр вывода типа **string** .|
|**OutputPath**|Необязательный параметр типа **string** .|
|**SourceFile**|Обязательный параметр **string** .|

## <a name="see-also"></a>См. также

[Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
