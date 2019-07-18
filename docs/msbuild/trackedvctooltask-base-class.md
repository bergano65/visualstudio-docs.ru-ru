---
title: Класс TrackedVCToolTask | Документация Майкрософт
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
ms.openlocfilehash: 4a4044416131a27ca313d10d02404094c5f5e219
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62938873"
---
# <a name="trackedvctooltask-base-class"></a>Базовый класс TrackedVCToolTask

В конечном счете многие задачи наследуются от класса <xref:Microsoft.Build.Utilities.Task> и класса [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask). Этот класс добавляет несколько параметров в задачи, производные от [VCToolTask](../msbuild/vctooltask-base-class.md). Эти параметры перечислены в настоящем документе.

## <a name="parameters"></a>Параметры

В следующей таблице описываются параметры базового класса **TrackedVCToolTask**.

|Параметр|Описание|
|---------------|-----------------|
|**DeleteOutputOnExecute**|Необязательный параметр типа **bool**.|
|**EnableExecuteTool**|Необязательный параметр типа **bool**.|
|**ExcludedInputPaths**|Необязательный параметр **ITaskItem[]**.|
|**MinimalRebuildFromTracking**|Необязательный параметр типа **bool**.|
|**PathOverride**|Необязательный параметр типа **string**.|
|**PostBuildTrackingCleanup**|Необязательный параметр типа **bool**.|
|**RootSource**|Необязательный параметр типа **string**.|
|**SkippedExecution**|Необязательный параметр вывода типа **bool**.|
|**SourcesCompiled**|Необязательный параметр вывода **ITaskItem[]**.|
|**TLogCommandFile**|Необязательный параметр **ITaskItem[]**.|
|**TLogReadFiles**|Необязательный параметр **ITaskItem[]**.|
|**TLogWriteFiles**|Необязательный параметр **ITaskItem[]**.|
|**ToolArchitecture**|Необязательный параметр типа **string**.|
|**TrackCommandLines**|Необязательный параметр типа **bool**.|
|**TrackFileAccess**|Необязательный параметр типа **bool**.|
|**TrackedInputFilesToIgnore**|Необязательный параметр **ITaskItem[]**.|
|**TrackedOutputFilesToIgnore**|Необязательный параметр **ITaskItem[]**.|
|**TrackerFrameworkPath**|Необязательный параметр типа **string**.|
|**TrackerSdkPath**|Необязательный параметр типа **string**.|

## <a name="see-also"></a>См. также

[Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)<br/>
[Задачи](../msbuild/msbuild-tasks.md)