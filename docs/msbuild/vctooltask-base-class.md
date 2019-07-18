---
title: Класс VCToolTask | Документация Майкрософт
ms.date: 03/10/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: 7bdad856a6ea0ec6cca8292bc3095f51c500bcb1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62970722"
---
# <a name="vctooltask-base-class"></a>Базовый класс VCToolTask

В конечном счете многие задачи наследуются от класса <xref:Microsoft.Build.Utilities.Task> и класса [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask). Этот класс добавляет несколько параметров в задачи, производные от него. Эти параметры перечислены в настоящем документе.

## <a name="parameters"></a>Параметры

В следующей таблице описываются параметры базового класса **VCToolTask**.

|Параметр|Описание|
|---------------|-----------------|
|**ActiveToolSwitchesValues**|Необязательный параметр типа **Dictionary\<string, ToolSwitch>**.|
|**AdditionalOptions**|Необязательный параметр типа **string**.|
|**EffectiveWorkingDirectory**|Необязательный параметр типа **string**.|
|**EnableErrorListRegex**|Необязательный параметр типа **bool**.<br/><br/>Значение по умолчанию — `true`.|
|**ErrorListRegex**|Необязательный параметр **ITaskItem[]**.|
|**ErrorListListExclusion**|Необязательный параметр **ITaskItem[]**.|
|**GenerateCommandLine**|Необязательный параметр типа **string**.<br/><br/>Использует значения *format* **CommandLineFormat** [по умолчанию = CommandLineFormat.ForBuildLog] и *escapeFormat* **EscapeFormat** [по умолчанию = EscapeFormat.Default].|
|**GenerateCommandLineExceptSwitches**|Необязательный параметр типа **string**.<br/><br/>Использует значения *switchesToRemove* **string[]**, *format* **CommandLineFormat** [по умолчанию = CommandLineFormat.ForBuildLog] и *escapeFormat* **EscapeFormat** [по умолчанию = EscapeFormat.Default].|

## <a name="see-also"></a>См. также

[Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)<br/>
[Задачи](../msbuild/msbuild-tasks.md)