---
title: Класс TrackedVCToolTask | Документация Майкрософт
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
ms.openlocfilehash: 8a4272f7800e0532c0674fe7117e839cb16557d5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594933"
---
# <a name="trackedvctooltask-base-class"></a>Базовый класс TrackedVCToolTask

В конечном счете многие задачи наследуются от класса <xref:Microsoft.Build.Utilities.Task> и класса [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask). Этот класс добавляет несколько параметров в задачи, производные от [VCToolTask](../msbuild/vctooltask-base-class.md). Эти параметры перечислены в настоящем документе.

## <a name="parameters"></a>Параметры

В следующей таблице описываются параметры базового класса **TrackedVCToolTask**.

|Параметр|Description|
|---------------|-----------------|
|**DeleteOutputOnExecute**|Необязательный параметр типа **bool**.|
|**EnableExecuteTool**|Необязательный параметр типа **bool**.|
|**ExcludedInputPaths**|Необязательный параметр **ITaskItem[]** .|
|**MinimalRebuildFromTracking**|Необязательный параметр типа **bool**.|
|**PathOverride**|Необязательный параметр типа **string**.|
|**PostBuildTrackingCleanup**|Необязательный параметр типа **bool**.|
|**RootSource**|Необязательный параметр типа **string**.|
|**SkippedExecution**|Необязательный параметр вывода типа **bool**.|
|**SourcesCompiled**|Необязательный параметр вывода **ITaskItem[]** .|
|**TLogCommandFile**|Необязательный параметр **ITaskItem[]** .|
|**TLogReadFiles**|Необязательный параметр **ITaskItem[]** .|
|**TLogWriteFiles**|Необязательный параметр **ITaskItem[]** .|
|**ToolArchitecture**|Необязательный параметр типа **string**.|
|**TrackCommandLines**|Необязательный параметр типа **bool**.|
|**TrackFileAccess**|Необязательный параметр типа **bool**.|
|**TrackedInputFilesToIgnore**|Необязательный параметр **ITaskItem[]** .|
|**TrackedOutputFilesToIgnore**|Необязательный параметр **ITaskItem[]** .|
|**TrackerFrameworkPath**|Необязательный параметр типа **string**.|
|**TrackerSdkPath**|Необязательный параметр типа **string**.|

## <a name="see-also"></a>См. также раздел

[Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)<br/>
[Задачи](../msbuild/msbuild-tasks.md)
