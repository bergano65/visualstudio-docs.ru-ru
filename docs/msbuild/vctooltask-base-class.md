---
title: Класс VCToolTask | Документация Майкрософт
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
ms.openlocfilehash: df75bb998d2b8c6486e20c4c3ca0d80347c8f88a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "75591675"
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
