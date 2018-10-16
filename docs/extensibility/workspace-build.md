---
title: Рабочая область построения в Visual Studio | Документы Microsoft
ms.custom: ''
ms.date: 02/21/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 813f7a5e-f298-4469-9f4c-a5bddf5a6e14
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: f7415c99c68436519f9bab721fe88a48f750fa1c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31143931"
---
# <a name="workspace-build"></a>Рабочая область построения

Поддержка сборки [открыть папку](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) сценариев требуется расширитель для предоставления [индексированных](workspace-indexing.md) и [контекст файла](workspace-file-contexts.md) данные для [рабочей](workspaces.md), как а также действие построения для запуска.

Ниже приводится объяснение того, что потребуется расширения.

## <a name="build-file-context"></a>Контекст файла сборки

- Фабрика поставщика
  - `ExportFileContextProviderAttribute` атрибут с `supportedContextTypeGuids` как и все применимые `string` константы из `BuildContextTypes`
  - Реализует `IWorkspaceProviderFactory<IFileContextProvider>`
  - Поставщик контекста файла
    - Возвращает `FileContext` для каждой сборки операции и поддерживаемые конфигурации
      - `contextType` От <xref:Microsoft.VisualStudio.Workspace.Build.BuildContextTypes>
      - `context` реализует <xref:Microsoft.VisualStudio.Workspace.Build.IBuildConfigurationContext> с `Configuration` свойство в качестве конфигурации сборки (например `"Debug|x86"`, `"ret"`, или `null` Если не применяется). Кроме того, используйте экземпляр <xref:Microsoft.VisualStudio.Workspace.Build.BuildConfigurationContext>. Значение конфигурации **необходимо** с конфигурацией значения файлов данных.

## <a name="indexed-build-file-data-value"></a>Значение данных файла индексированных построения

- Фабрика поставщика
  - `ExportFileScannerAttribute` атрибут с `IReadOnlyCollection<FileDataValue>` поддерживаемого типа
  - Реализует `IWorkspaceProviderFactory<IFileScanner>`
- Проверки файлов на `ScanContentAsync<T>`
  - Возвращает данные при `FileScannerTypeConstants.FileDataValuesType` — аргумент типа
  - Возвращает значение для каждой конфигурации, созданные с помощью файла:
    - `type` как `BuildConfigurationContext.ContextTypeGuid`
    - `context` в качестве конфигурации сборки (например `"Debug|x86"`, `"ret"`, или `null` Если не применяется). Это значение **должен** соответствует конфигурации из файла контекста.

## <a name="build-file-context-action"></a>Действие контекста файла сборки

- Фабрика поставщика
  - `ExportFileContextActionProvider` атрибут с `supportedContextTypeGuids` как и все применимые `string` константы из `BuildContextTypes`
  - Реализует `IWorkspaceProviderFactory<IFileContextActionProvider>`
- Действия поставщика на `IFileContextActionProvider.GetActionsAsync`
  - Вернуть `IFileContextAction` , соответствующий данной `FileContext.ContextType` значение
- Контекст действия с файлом
  - Реализует `IFileContextAction` и <xref:Microsoft.VisualStudio.Workspace.Extensions.VS.IVsCommandItem>
  - `CommandGroup` Возвращает свойство `16537f6e-cb14-44da-b087-d1387ce3bf57`
  - `CommandId` — `0x1000` для сборки, `0x1010` для перестроения или `0x1020` для очистки

>[!NOTE]
>Поскольку `FileDataValue` должен быть индексирован, будет минимальное количество времени между открытием в рабочей области и точку сканирования файла для сборки полную функциональность. Задержка будет виден на сначала открыть папку, так как нет кэшированной индекса.

## <a name="reporting-messages-from-a-build"></a>Сообщения для построения отчетов

Сборки, могут возникать сообщения об ошибках, предупреждения и сведения для пользователей одним из двух способов. Простым способом является использование <xref:Microsoft.VisualStudio.Workspace.Build.IBuildMessageService> и предоставить <xref:Microsoft.VisualStudio.Workspace.Build.BuildMessage>, следующим образом:

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

`BuildMessage.Type` и `BuildMessage.LogMessage` поведения, где представлены сведения для пользователя. Любой `BuildMessage.TaskType` отличный от `None` сформирует **список ошибок** запись с заданной сведения. `LogMessage` вывода в **построения** области **вывода** окно инструментов.

Кроме того, расширения могут непосредственно взаимодействовать с **список ошибок** или **построения** области. В версиях до Visual Studio 2017 г. версия 15,7 есть ошибка, где `pszProjectUniqueName` аргумент <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane2.OutputTaskItemStringEx2*> учитывается.

>[!WARNING]
>При вызове `IFileContextAction.ExecuteAsync` можно предоставлять произвольные базовой реализации для `IProgress<IFileContextActionProgressUpdate>` аргумент. Никогда не вызвать `IProgress<IFileContextActionProgressUpdate>.Report(IFileContextActionProgressUpdate)` напрямую. В настоящее время существует общих принципов использовать этот аргумент, но эти рекомендации могут быть изменены.

## <a name="build-related-apis"></a>API, связанные с построения

- <xref:Microsoft.VisualStudio.Workspace.Build.IBuildConfigurationContext> Предоставляет сведения о конфигурации сборки.
- <xref:Microsoft.VisualStudio.Workspace.Build.IBuildMessageService> Показывает <xref:Microsoft.VisualStudio.Workspace.Build.BuildMessage>s для пользователей.

## <a name="tasksvsjson-and-launchvsjson"></a>Tasks.VS.JSON и launch.vs.json

На создание файла tasks.vs.json или launch.vs.json Подробнее [настройки построения и отладки задачи](../ide/customize-build-and-debug-tasks-in-visual-studio.md).

## <a name="next-steps"></a>Следующие шаги

* [Протокол для сервера язык](language-server-protocol.md) -Узнайте, как интегрировать языка серверов в Visual Studio.