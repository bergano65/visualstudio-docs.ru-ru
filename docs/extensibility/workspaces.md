---
title: Рабочие области в Visual Studio | Документы Microsoft
ms.custom: ''
ms.date: 02/21/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 3489592a-dc0c-4cd3-9b08-cd367626980a
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 0230201677fd2422817ca1fbeab6679a424e5c05
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="workspaces"></a>Рабочие области

Рабочая область — представление какой-либо коллекции файлов в Visual Studio [открыть папку](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md), и он представлен <xref:Microsoft.VisualStudio.Workspace.IWorkspace> типа. Сам по себе рабочей области не понимает содержимого или функции, относящиеся к файлам в папке. Вместо этого он предоставляет общий набор API-интерфейсов для функции и расширения для создания и использования данных, другие могут действовать. Производители состоят через [Managed Extensibility Framework](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (MEF) с помощью различных экспорт атрибутов.

## <a name="workspace-providers-and-services"></a>Поставщики рабочей области и службы

Поставщики рабочей области и службы предоставляют данные, а также функциональность для реагирования на содержимое рабочей области. Они могут предоставлять сведения о контекстно-зависимое файла, символы в исходных файлах или реализовать функции.

Использовать оба понятия [шаблон фабрики](https://en.wikipedia.org/wiki/Factory_method_pattern) и импортированные с помощью MEF по рабочей области. Все атрибуты экспорта, реализующие `IProviderMetadataBase` или `IWorkspaceServiceFactoryMetadata`, но есть конкретные типы, которые должна использовать расширения для экспортируемые типы.

Единственным отличием между поставщиками и службы является их связь в рабочую область. Рабочая область может иметь много поставщиков определенного типа, но только одна служба определенного типа создается в каждой рабочей области. Например рабочую область имеет многие поставщики сканера файла, но рабочей области имеется только одна служба индексирования каждой рабочей области.

Еще одно важное отличие — потребление данных от поставщиков и служб. Рабочая область — это точка входа для получения данных от поставщиков для несколько причин. Во-первых поставщики, обычно имеют некоторые небольшим набором данных, которые они создают. Данных может быть символов для исходного файла C# или построить файл контекстов для _CMakeLists.txt_ файла. Рабочей области будет соответствовать запросу потребителя к поставщикам, метаданные которого выравнивание с запросом. Во-вторых, некоторые сценарии позволяют многие поставщики принять участие в запрос, тогда как другие сценарии используют поставщик с высоким приоритетом.

Напротив расширения можно получить экземпляры и напрямую взаимодействовать с рабочей области службы. Методы расширения в `IWorkspace` доступны для служб, предоставляемых Visual Studio, например <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetFileWatcherService%2A>. Расширение может предлагать для компонентов расширения или другие расширения, которые используют службы рабочей области. Пользователям рекомендуется применять <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetServiceAsync%2A> или метод расширения, указываемые на `IWorkspace` типа.

>[!WARNING]
> Не создавать службы, которые конфликтуют с Visual Studio. Это может привести к непредвиденных проблем.

## <a name="disposal-on-workspace-closure"></a>Реализация на закрытия рабочей области

Для закрытия рабочей области расширения может потребоваться dispose, но вызова асинхронного кода. <xref:Microsoft.VisualStudio.Threading.IAsyncDisposable> Интерфейс доступен делает написание этот код просто.

## <a name="related-types"></a>Связанные типы

- <xref:Microsoft.VisualStudio.Workspace.IWorkspace> является центральной для открытых рабочей области, например открытой папки.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspaceProviderFactory`1> Создает поставщик каждой рабочей области при создании экземпляра.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspaceServiceFactory> Создает службу каждой рабочей области при создании экземпляра.
- <xref:Microsoft.VisualStudio.Threading.IAsyncDisposable> должен быть реализован в поставщиков и службам, которые необходимы для выполнения асинхронного кода во время реализации.
- <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper> Предоставляет вспомогательные методы для доступа к хорошо известных служб или произвольные служб.

## <a name="workspace-settings"></a>Параметры рабочей области

Рабочие области имеют <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager> с простой, но многосторонний контроль над рабочей области. Общие параметры в разделе [настройки построения и отладки задачи](../ide/customize-build-and-debug-tasks-in-visual-studio.md).

Параметры для большинства `SettingsType` типы _.json_ файлы, такие как _VSWorkspaceSettings.json_ и _tasks.vs.json_.

Возможности настройки рабочей области основано на «областей», которые являются просто пути в рабочей области. Когда потребитель вызывает метод <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager.GetAggregatedSettings%2A>, объединяются все области, которые включают запрошенный путь и тип параметра. Приоритет статистической обработки области выглядит следующим образом:

1. «Локальные параметры», которые обычно является корневой рабочей области `.vs` каталога.
1. Запрошенный сам путь.
1. Родительский каталог запрошенный путь.
1. Все дополнительные родительских каталогах вплоть до корня рабочей области.
1. «Глобальные параметры», которых находится в каталоге пользователя.

Результат представляет собой экземпляр <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings>. Этот объект содержит параметры для определенного типа и могут запрашиваться для ключа имена параметров, сохраненные как `string`. <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings.GetProperty%2A> Методы и <xref:Microsoft.VisualStudio.Workspace.Settings.WorkspaceSettingsExtensions> вызывающему объекту известен тип запрашиваемого значение параметра ожидается, что методы расширения. Как большинство файлов, параметры сохраняются в виде _.json_ файлы, будет использовать много вызовов `string`, `bool`, `int`и массивов этих типов. Также поддерживаются типы объектов. В таких случаях можно использовать `IWorkspaceSettings` себя в качестве аргумента типа. Пример:

```json
{
  "intValue": 1,
  "stringValue": "s",
  "boolValue": true,
  "stringArray": [
    "s1",
    "s2"
  ],
  "nestedIWorkspaceSettings": {
    "nestedString": "ns"
  }
}
```

При условии, что эти параметры были в пользователя _VSWorkspaceSettings.json_, доступ к данным как:

```csharp
using System.Collections.Generic;
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Settings;

private static void ReadSettings(IWorkspace workspace)
{
    IWorkspaceSettingsManager settingsManager = workspace.GetSettingsManager();
    IWorkspaceSettings settings = settingsManager.GetAggregatedSettings(SettingsTypes.Generic);

    // result == WorkspaceSettingsResult.Success
    WorkspaceSettingsResult result = settings.GetProperty("intValue", out int intValue);
    result = settings.GetProperty("stringValue", out string stringValue);
    result = settings.GetProperty("boolValue", out bool boolValue);
    result = settings.GetProperty("stringArray", out string[] stringArray);
    result = settings.GetProperty("nestedIWorkspaceSettings", out IWorkspaceSettings nestedIWorkspaceSettings);
    result = nestedIWorkspaceSettings.GetProperty("nestedString", out string nestedString);

    // Extension method alternative using default values.
    int intValueOrDefault = settings.Property("intValue", /* default */ 42);

    // Missing key. result == WorkspaceSettingsResult.Undefined
    result = settings.GetProperty("missing", out string missing);

    // Wrong type for a key. result == WorkspaceSettingsResult.Error
    result = settings.GetProperty("intValue", out IWorkspaceSettings notSettings);

    // Special ability to union "stringArray" across all scopes.
    IEnumerable<string> allStringArray = settings.UnionPropertyArray<string>("stringArray");
}
```

>[!NOTE]
>Эти параметры API-интерфейсы не связаны с API-интерфейса в `Microsoft.VisualStudio.Settings` пространства имен. Параметры рабочей области являются независимыми от узла и использовать параметры, относящиеся к рабочей области файлы или поставщиков динамических параметров.

### <a name="providing-dynamic-settings"></a>Предоставление динамических параметров

Расширения могут предоставить <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsProvider>s. Эти поставщики в памяти разрешить расширения для добавления параметров или переопределить другим пользователям.

Экспорт `IWorkspaceSettingsProvider` отличается от других поставщиков рабочей области. Фабрика является не `IWorkspaceProviderFactory` и нет атрибутов специальных типов. Вместо этого следует реализовать <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsProviderFactory> и использовать `[Export(typeof(IWorkspaceSettingsProviderFactory))]`.

```csharp
// Common workspace provider factory pattern
[ExportFeatureProvider(some, args, to, export)]
internal class MyProviderFactory : IWorkspaceProviderFactory<IFeatureProvider>
{
     IFeatureProvider CreateProvider(IWorkspace workspace) => new Provider(workspace);
}

// IWorkspaceSettingsProvider pattern
[Export(typeof(IWorkspaceSettingsProviderFactory))]
internal class MySettingsProviderFactory : IWorkspaceSettingsProviderFactory
{
    // 100 is typically the value used by built-in settings providers. Lower value is higher priority.
    int Priority => 100;

    IWorkspaceSettingsProvider CreateSettingsProvider(IWorkspace workspace) => new MySettingsProvider(workspace);
}
```

>[!TIP]
>При реализации методов, возвращающих `IWorkspaceSettingsSource` (такие как `IWorkspaceSettingsProvider.GetSingleSettings`), верните экземпляр `IWorkspaceSettings` вместо `IWorkspaceSettingsSource`. `IWorkspaceSettings` Дополнительные сведения, могут быть полезны при некоторых параметров агрегатов.

### <a name="settings-related-apis"></a>Параметры, связанные с API-интерфейсы

- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager> Считывает и объединяет параметры для рабочей области.
- <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetSettingsManager%2A> Возвращает `IWorkspaceSettingsManager` для рабочей области.
- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager.GetAggregatedSettings%2A> Возвращает параметры для данной области, агрегируются по всем областям поиска перекрывающихся.
- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings> содержит параметры для определенной области.

## <a name="workspace-suggested-practices"></a>Рабочая область Рекомендуемые методики

- Возвращает объекты из `IWorkspaceProviderFactory.CreateProvider` или аналогичный API, которые их `Workspace` контекст при создании. Интерфейсы поставщиков записываются ожидается, что этот объект сохраняется в момент создания.
- Сохраните специфическим кэши или параметров в пути «Локальные параметры» рабочей области. Создать путь для файла с помощью `Microsoft.VisualStudio.Workspace.WorkspaceHelper.MakeRootedUnderWorkingFolder` в Visual Studio 2017 г 15.6 или более поздней версии. Для версий до версии 15,6 используйте следующий фрагмент кода:

```csharp
using System.IO;
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Settings;

private static string MakeRootedUnderWorkingFolder(IWorkspace workspace, string relativePath)
{
    string workingFolder = workspace.GetSettingsManager().GetAggregatedSettings(SettingsTypes.WorkspaceControlSettings).Property<string>("WorkingFolder");
    return Path.Combine(workingFolder, relativePath);
}
```

## <a name="solution-events-and-package-auto-load"></a>Событий решения и автоматически загрузить пакет

Загрузить пакеты можно реализовать `IVsSolutionEvents7` и вызова `IVsSolution.AdviseSolutionEvents`. Он включает обработку событий на открытие и закрытие папки в Visual Studio.

Контекст пользовательского интерфейса можно использовать для автоматической загрузки пакета. Значение — `4646B819-1AE0-4E79-97F4-8A8176FDD664`.

## <a name="troubleshooting"></a>Устранение неполадок

### <a name="the-sourceexplorerpackage-package-did-not-load-correctly"></a>SourceExplorerPackage пакет не был правильно загружен

Расширяемость рабочей области основан на сильно MEF, а ошибки композиции вызовет размещение открыть папку, чтобы не удалось загрузить пакет. Например, если расширение экспортирует тип с `ExportFileContextProviderAttribute`, но тип реализует только `IWorkspaceProviderFactory<IFileContextActionProvider>`, произойдет ошибка при попытке открыть папку в Visual Studio. Сведения об ошибке можно найти в _%LOCALAPPDATA%\Microsoft\VisualStudio\15.0_id\ComponentModelCache\Microsoft.VisualStudio.Default.err_. Устраните все ошибки для типов, реализованных в расширении.

## <a name="next-steps"></a>Следующие шаги

* [Контекстов файла](workspace-file-contexts.md) -поставщики контекста файла перевести аналитики кода для рабочих областей открыть папку. 
* [Индексирование](workspace-indexing.md) -индексирования рабочей собирает и сохраняет сведения о рабочей области.
