---
title: Сборка рабочей области в Visual Studio | Документация Майкрософт
description: Сведения об расширителье, предоставляющем данные о индексированном и файловом контексте рабочей области для поддержки сценария открытия папки.
ms.custom: SEO-VS-2020
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: e44c2398b873bbca95c971ae1b44ac3de831b2ae
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877108"
---
# <a name="workspace-build"></a>Сборка рабочей области

Для поддержки сборки в сценариях с [открытой папкой](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) требуется расширитель для передачи данных о [проиндексированном](workspace-indexing.md) и [файловом контексте](workspace-file-contexts.md) [рабочей области](workspaces.md), а также выполняемое действие сборки.

Ниже приведена структура того, что потребуется вашему расширению.

## <a name="build-file-context"></a>Контекст файла сборки

- Фабрика поставщиков
  - `ExportFileContextProviderAttribute` атрибут `supportedContextTypeGuids` , содержащий все применимые `string` константы из `BuildContextTypes`
  - Реализует `IWorkspaceProviderFactory<IFileContextProvider>`
  - Поставщик контекста файла
    - Возврат `FileContext` для каждой поддерживаемой операции сборки и конфигурации
      - `contextType` из <xref:Microsoft.VisualStudio.Workspace.Build.BuildContextTypes>
      - `context` реализует <xref:Microsoft.VisualStudio.Workspace.Build.IBuildConfigurationContext> свойство со `Configuration` свойством в качестве конфигурации сборки (например `"Debug|x86"` , `"ret"` или, `null` Если неприменимо). Кроме того, можно использовать экземпляр <xref:Microsoft.VisualStudio.Workspace.Build.BuildConfigurationContext> . Значение конфигурации **должно** соответствовать конфигурации из значения данных индексированного файла.

## <a name="indexed-build-file-data-value"></a>Значение данных индексированного файла сборки

- Фабрика поставщиков
  - `ExportFileScannerAttribute` атрибут с `IReadOnlyCollection<FileDataValue>` поддерживаемым типом
  - Реализует `IWorkspaceProviderFactory<IFileScanner>`
- Средство проверки файлов включено `ScanContentAsync<T>`
  - Возвращает данные, если `FileScannerTypeConstants.FileDataValuesType` является аргументом типа
  - Возвращает значение данных файла для каждой конфигурации, созданной с помощью:
    - `type` тех `BuildConfigurationContext.ContextTypeGuid`
    - `context` в качестве конфигурации сборки (например, `"Debug|x86"` `"ret"` или, `null` если она неприменима). Это значение **должно** соответствовать конфигурации из контекста файла.

## <a name="build-file-context-action"></a>Действие контекста файла сборки

- Фабрика поставщиков
  - `ExportFileContextActionProvider` атрибут `supportedContextTypeGuids` , содержащий все применимые `string` константы из `BuildContextTypes`
  - Реализует `IWorkspaceProviderFactory<IFileContextActionProvider>`
- Поставщик действий в `IFileContextActionProvider.GetActionsAsync`
  - Возврат объекта `IFileContextAction` , соответствующего заданному `FileContext.ContextType` значению
- Действие контекста файла
  - Реализует `IFileContextAction` и <xref:Microsoft.VisualStudio.Workspace.Extensions.VS.IVsCommandItem>
  - `CommandGroup` свойство возвращает `16537f6e-cb14-44da-b087-d1387ce3bf57`
  - `CommandId` предназначен `0x1000` для сборки, `0x1010` для перестроения или `0x1020` для очистки

>[!NOTE]
>Поскольку необходимо `FileDataValue` проиндексировать, между открытием рабочей области и моментом сканирования файла на наличие полной функциональности сборки будет некоторое количество времени. Задержка будет показана в первом открытии папки, так как отсутствует ранее кэшированный индекс.

## <a name="reporting-messages-from-a-build"></a>Сообщения отчетов из сборки

Сборка может предоставлять пользователям сведения, предупреждения и сообщения об ошибках одним из двух способов. Простой способ — использовать <xref:Microsoft.VisualStudio.Workspace.Build.IBuildMessageService> и предоставить <xref:Microsoft.VisualStudio.Workspace.Build.BuildMessage> , например:

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

`BuildMessage.Type` и `BuildMessage.LogMessage` управляют поведением, где данные представляются пользователю. Любое `BuildMessage.TaskType` значение, отличное от `None` , создает запись **Список ошибок** с указанными сведениями. `LogMessage` всегда будет выводиться в области **Построение** окна инструментов **вывода** .

Кроме того, расширения могут напрямую взаимодействовать с **Список ошибок** или областью **построения** . Ошибка существует в версиях до Visual Studio 2017 версии 15,7, где `pszProjectUniqueName` аргумент <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane2.OutputTaskItemStringEx2*> игнорируется.

>[!WARNING]
>Вызывающие объекты `IFileContextAction.ExecuteAsync` могут предоставлять произвольные базовые реализации для `IProgress<IFileContextActionProgressUpdate>` аргумента. Никогда не вызывать `IProgress<IFileContextActionProgressUpdate>.Report(IFileContextActionProgressUpdate)` напрямую. В настоящее время нет общих рекомендаций по использованию этого аргумента, но эти рекомендации могут быть изменены.

## <a name="build-related-apis"></a>Связанные API-интерфейсы сборки

- <xref:Microsoft.VisualStudio.Workspace.Build.IBuildConfigurationContext> предоставляет сведения о конфигурации сборки.
- <xref:Microsoft.VisualStudio.Workspace.Build.IBuildMessageService> показывает <xref:Microsoft.VisualStudio.Workspace.Build.BuildMessage> пользователей.

## <a name="tasksvsjson-and-launchvsjson"></a>tasks.vs.jsи launch.vs.jsна

Сведения о создании tasks.vs.jsдля или launch.vs.jsв файле см. в разделе [Настройка задач сборки и отладки](../ide/customize-build-and-debug-tasks-in-visual-studio.md).

## <a name="next-steps"></a>Дальнейшие действия

* [Протокол языкового сервера](language-server-protocol.md) . Узнайте, как интегрировать языковые серверы в Visual Studio.