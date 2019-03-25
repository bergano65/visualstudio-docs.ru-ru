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
ms.author: Michael.Blome
ms.workload:
- multiple
ms.openlocfilehash: 4c7cc3490735dbd9ac43cd43555ec673cc3afccd
ms.sourcegitcommit: 4ffb7be5384ad566ce46538032bf8561754c61a4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2019
ms.locfileid: "58070504"
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