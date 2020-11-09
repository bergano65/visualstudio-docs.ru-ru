---
title: Класс VCToolTask | Документация Майкрософт
description: Сведения о нескольких параметрах, которые базовый класс VCToolTask добавляет к производным от него задачам.
ms.custom: SEO-VS-2020
ms.date: 03/10/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
author: ghogen
ms.author: ghogen
ms.workload:
- multiple
ms.openlocfilehash: b2e45d7c672ebc2177c2bb197399133e7b077a5c
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/30/2020
ms.locfileid: "93046736"
---
# <a name="vctooltask-base-class"></a>Базовый класс VCToolTask

В конечном счете многие задачи наследуются от класса <xref:Microsoft.Build.Utilities.Task> и класса [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask). Этот класс добавляет несколько параметров в задачи, производные от него. Эти параметры перечислены в настоящем документе.

## <a name="parameters"></a>Параметры

В следующей таблице описываются параметры базового класса **VCToolTask**.

|Параметр|Description|
|---------------|-----------------|
|**ActiveToolSwitchesValues**|Необязательный параметр **Dictionary\<string, ToolSwitch>** .|
|**AdditionalOptions**|Необязательный параметр типа **string**.|
|**EffectiveWorkingDirectory**|Необязательный параметр типа **string**.|
|**EnableErrorListRegex**|Необязательный параметр типа **bool**.<br/><br/>Значение по умолчанию — `true`.|
|**ErrorListRegex**|Необязательный параметр **ITaskItem[]** .|
|**ErrorListListExclusion**|Необязательный параметр **ITaskItem[]** .|
|**GenerateCommandLine**|Необязательный параметр типа **string**.<br/><br/>Использует значения **format** *CommandLineFormat* [по умолчанию = CommandLineFormat.ForBuildLog] и **EscapeFormat** *escapeFormat* [по умолчанию = EscapeFormat.Default].|
|**GenerateCommandLineExceptSwitches**|Необязательный параметр типа **string**.<br/><br/>Использует значения **switchesToRemove** *string[]* , **format** *CommandLineFormat* [по умолчанию = CommandLineFormat.ForBuildLog] и **EscapeFormat** *escapeFormat* [по умолчанию = EscapeFormat.Default].|

## <a name="see-also"></a>См. также раздел

[Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)<br/>
[Задачи](../msbuild/msbuild-tasks.md)
