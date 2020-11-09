---
title: Класс TrackedVCToolTask | Документация Майкрософт
description: Сведения о параметрах, которые базовый класс TrackedVCToolTask добавляет к производным от него задачам.
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
ms.openlocfilehash: 01b55e0ad88cb520078479217306bac948e6cd60
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/30/2020
ms.locfileid: "93047000"
---
# <a name="trackedvctooltask-base-class"></a>Базовый класс TrackedVCToolTask

В конечном счете многие задачи наследуются от класса <xref:Microsoft.Build.Utilities.Task> и класса [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask). Этот класс добавляет несколько параметров в задачи, производные от [VCToolTask](../msbuild/vctooltask-base-class.md). Эти параметры перечислены в настоящем документе.

## <a name="parameters"></a>Параметры

В следующей таблице описываются параметры базового класса **TrackedVCToolTask**.

|Параметр|Описание|
|---------------|-----------------|
|**DeleteOutputOnExecute**|Необязательный параметр типа **bool**.|
|**EnableExecuteTool**|Необязательный параметр типа **bool**.|
|**ExcludedInputPaths**|Необязательный параметр **ITaskItem[]** .|
|**MinimalRebuildFromTracking**|Необязательный параметр типа **bool**.|
|**PathOverride**|Необязательный параметр типа **string**.|
|**PostBuildTrackingCleanup**|Необязательный параметр типа **bool**.|
|**RootSource**|Необязательный параметр типа **string**.|
|**SkippedExecution**|Необязательный параметр вывода типа **bool**.|
|**SourcesCompiled**|Необязательный параметр вывода **ITaskItem[]**.|
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

## <a name="see-also"></a>См. также

[Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)<br/>
[Задачи](../msbuild/msbuild-tasks.md)
