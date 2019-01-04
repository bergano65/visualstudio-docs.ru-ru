---
title: Рабочая область построения в Visual Studio | Документация Майкрософт
ms.date: 02/21/2018
ms.topic: conceptual
ms.assetid: 813f7a5e-f298-4469-9f4c-a5bddf5a6e14
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: b0d90a3d317583e987eae83fadae5afa40546701
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53826725"
---
# <a name="workspace-build"></a>Рабочая область построения

Поддержка сборки [открыть папку](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) сценарии требуется расширитель для предоставления [индексированных](workspace-indexing.md) и [контекста файла](workspace-file-contexts.md) данные для [рабочей области](workspaces.md), как а также действие построения для запуска.

Ниже приводится объяснение того что потребуется ваше расширение.

## <a name="build-file-context"></a>Контекст файла сборки

- Фабрика поставщиков
  - `ExportFileContextProviderAttribute` атрибут с `supportedContextTypeGuids` как и все применимые `string` констант `BuildContextTypes`
  - Реализует `IWorkspaceProviderFactory<IFileContextProvider>`
  - Контекст поставщика файлов
    - Вернуть `FileContext` для каждого построения операции и поддерживаемые конфигурации
      - `contextType` От <xref:Microsoft.VisualStudio.Workspace.Build.BuildContextTypes>
      - `context` реализует <xref:Microsoft.VisualStudio.Workspace.Build.IBuildConfigurationContext> с `Configuration` свойство в качестве конфигурации сборки (например `"Debug|x86"`, `"ret"`, или `null` Если не применимо). Кроме того, используйте экземпляр <xref:Microsoft.VisualStudio.Workspace.Build.BuildConfigurationContext>. Значение конфигурации **необходимо** соответствуют конфигурации из значения файлов данных.

## <a name="indexed-build-file-data-value"></a>Значение данных индексированных построения файла

- Фабрика поставщиков
  - `ExportFileScannerAttribute` атрибут с `IReadOnlyCollection<FileDataValue>` поддерживаемый тип
  - Реализует `IWorkspaceProviderFactory<IFileScanner>`
- Файл сканера, установленного на `ScanContentAsync<T>`
  - Возвращает данные при `FileScannerTypeConstants.FileDataValuesType` аргумент типа
  - Возвращает значение данных файла для каждой конфигурации, созданный с помощью:
    - `type` как `BuildConfigurationContext.ContextTypeGuid`
    - `context` в качестве конфигурации сборки (например `"Debug|x86"`, `"ret"`, или `null` Если не применимо). Это значение **необходимо** соответствуют конфигурации из файла контекста.

## <a name="build-file-context-action"></a>Действия файл контекст сборки

- Фабрика поставщиков
  - `ExportFileContextActionProvider` атрибут с `supportedContextTypeGuids` как и все применимые `string` констант `BuildContextTypes`
  - Реализует `IWorkspaceProviderFactory<IFileContextActionProvider>`
- Поставщик действий на `IFileContextActionProvider.GetActionsAsync`
  - Вернуть `IFileContextAction` , соответствующий заданной `FileContext.ContextType` значение
- Действие в контексте файла
  - Реализует `IFileContextAction` и <xref:Microsoft.VisualStudio.Workspace.Extensions.VS.IVsCommandItem>
  - `CommandGroup` Возвращает свойство `16537f6e-cb14-44da-b087-d1387ce3bf57`
  - `CommandId` — `0x1000` для сборки, `0x1010` для перестроения или `0x1020` для очистки

>[!NOTE]
>Так как `FileDataValue` нужно индексировать, будет существовать минимальное количество времени между открытием рабочей области и точки, по которому проверяется на функциональные возможности полной сборки. Задержка будет виден на сначала открыв папку, так как нет ранее кэшированных индекса.

## <a name="reporting-messages-from-a-build"></a>Reporting сообщения из сборки

Сборки могут возникать сообщения об ошибках, предупреждения и сведения для пользователей одним из двух способов. Простым способом является использование <xref:Microsoft.VisualStudio.Workspace.Build.IBuildMessageService> и предоставить <xref:Microsoft.VisualStudio.Workspace.Build.BuildMessage>, следующим образом:

```csharp
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Build;

private static void OutputBuildMessage(IWorkspace workspace)
{
    IBuildMessageService buildMessageService = workspace.GetBuildMessageService();

    if (buildMessageService != null)
    {
      // Example error build message. See the documentation for BuildMessage for more information.
      var message = new BuildMessage()
      {
          Type = BuildMessage.TaskType.Error,
          Code = "MY1001",
          TaskText = "This is a sample error",
          ProjectFile = "buildfile.bld",
          File = "sourcefile.src"
          LogMessage = $"This is sample text that will only go to the Build output window pane.\n"

          // And any other properties to set
      };

      buildMessageService.ReportBuildMessages(new BuildMessage[] { message });
    }
}
```

`BuildMessage.Type` и `BuildMessage.LogMessage` управления поведением где сведения отображаются для пользователя. Любой `BuildMessage.TaskType` отличное от `None` создаст **список ошибок** запись с указанным сведениям. `LogMessage` всегда будут выводиться в **построения** области **вывода** окно инструментов.

Кроме того, расширения могут напрямую взаимодействовать с **список ошибок** или **построения** области. Ошибка в версиях до Visual Studio 2017 версии 15.7 где `pszProjectUniqueName` аргумент <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane2.OutputTaskItemStringEx2*> учитывается.

>[!WARNING]
>Вызывающие объекты `IFileContextAction.ExecuteAsync` можно предоставить произвольные базовой реализации `IProgress<IFileContextActionProgressUpdate>` аргумент. Никогда не вызывать `IProgress<IFileContextActionProgressUpdate>.Report(IFileContextActionProgressUpdate)` напрямую. В настоящее время существует общих принципов с помощью этого аргумента, но эти рекомендации могут быть изменены.

## <a name="build-related-apis"></a>API, связанные с построения

- <xref:Microsoft.VisualStudio.Workspace.Build.IBuildConfigurationContext> Предоставляет сведения о конфигурации сборки.
- <xref:Microsoft.VisualStudio.Workspace.Build.IBuildMessageService> Показывает <xref:Microsoft.VisualStudio.Workspace.Build.BuildMessage>s для пользователей.

## <a name="tasksvsjson-and-launchvsjson"></a>Tasks.VS.JSON и launch.vs.json

Сведения о создании файла tasks.vs.json и launch.vs.json, см. в разделе [Настройка сборки и отладки задачи](../ide/customize-build-and-debug-tasks-in-visual-studio.md).

## <a name="next-steps"></a>Следующие шаги

* [Протокол языкового сервера](language-server-protocol.md) -как интегрировать серверы языка в Visual Studio.