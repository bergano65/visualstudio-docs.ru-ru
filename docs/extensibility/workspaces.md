---
title: Рабочие области в Visual Studio | Документация Майкрософт
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: da61f3f46d9737bef6c14cf69a52be1951da28fb
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55925440"
---
# <a name="workspaces"></a>Рабочие области

Рабочая область — представление любой сбор таких файлов в Visual Studio [открыть папку](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md), и он представлен <xref:Microsoft.VisualStudio.Workspace.IWorkspace> типа. Сама по себе рабочей области не понимает содержимое или функции, относящиеся к файлам в папке. Вместо этого он предоставляет общий набор API-интерфейсы для функции и расширения для создания и использования данных, может действовать другим пользователям. Производители состоят через [Managed Extensibility Framework](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (MEF) с помощью различных экспорт атрибутов.

## <a name="workspace-providers-and-services"></a>Поставщики рабочей области и службы

Поставщики рабочей области и службы предоставляют данные и функции для реагирования на содержимое рабочей области. Они могут предоставлять сведения о контекстных файла, символы в исходных файлах, или создания функций.

Использовать оба понятия [шаблон фабрики](https://en.wikipedia.org/wiki/Factory_method_pattern) и импортированные с помощью MEF рабочей областью. Все атрибуты экспорта, реализующие `IProviderMetadataBase` или `IWorkspaceServiceFactoryMetadata`, но существуют конкретные типы, которые следует использовать расширения для экспортируемые типы.

Отличие между поставщиками и служб заключается в их связь с рабочей областью. Рабочая область может иметь множество поставщиков определенного типа, но только одна служба определенного типа создается в каждой рабочей области. Например в рабочей области находятся многие поставщики сканера файлов, но рабочая область содержит только одна служба индексирования каждой рабочей области.

Еще одно важное отличие — потребление данных от поставщиков и служб. Рабочая область является точкой входа для получения данных от поставщиков по нескольким причинам. Во-первых поставщики обычно имеют некоторые узкий набор данных, которые они создают. Данные могут быть символы для C# исходный файл или создавать контексты файла для _CMakeLists.txt_ файла. Рабочая область будет соответствовать запросу получателя к поставщикам, метаданные которого выровнять с запросом. Во-вторых, разрешить некоторые сценарии для многих поставщиков принять участие в составлении запроса, тогда как другие сценарии использования поставщика с высоким приоритетом.

Напротив расширения можно получить экземпляры и взаимодействуют непосредственно со службами в рабочей области. Методы расширения на `IWorkspace` доступны для служб, предоставляемых Visual Studio, такие как <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetFileWatcherService%2A>. Расширение может предлагать службы рабочей области для компонентов в модуле или другие расширения для использования. Потребители должны использовать <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetServiceAsync%2A> или метод расширения на `IWorkspace` типа.

>[!WARNING]
> Не создавать службы, которые конфликтуют с Visual Studio. Это может привести к непредвиденных проблем.

## <a name="disposal-on-workspace-closure"></a>Располагаете на закрытия рабочей области

В закрытия рабочей области расширения может потребоваться dispose, но вызов асинхронного кода. <xref:Microsoft.VisualStudio.Threading.IAsyncDisposable> Интерфейс доступен для облегчения написания этот код просто.

## <a name="related-types"></a>Связанные типы

- <xref:Microsoft.VisualStudio.Workspace.IWorkspace> является центральной сущностью, для открытого рабочую область как в открытой папке.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspaceProviderFactory`1> Создает поставщик каждой рабочей области при создании экземпляра.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspaceServiceFactory> Создает службу каждой рабочей области при создании экземпляра.
- <xref:Microsoft.VisualStudio.Threading.IAsyncDisposable> должен быть реализован на поставщики и службы, которые нужно выполнять асинхронный код во время реализации.
- <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper> Предоставляет вспомогательные методы для доступа к хорошо известные услуги, или произвольных служб.

## <a name="workspace-settings"></a>Параметры рабочей области

Рабочие области имеют <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager> с простой, но эффективный контроль над рабочей области. Общий обзор параметров, см. в разделе [Настройка сборки и отладки задачи](../ide/customize-build-and-debug-tasks-in-visual-studio.md).

Параметры для большинства `SettingsType` типы являются _.json_ файлы, такие как _VSWorkspaceSettings.json_ и _tasks.vs.json_.

Мощь параметры рабочей области основано на «области», которые являются просто путей в рабочей области. Когда потребитель вызывает метод <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager.GetAggregatedSettings%2A>, суммируются все области действия, которые включают запрошенный путь и тип параметра. Приоритет статистической обработки область выглядит следующим образом:

1. «Локальные параметры», что обычно корневом каталоге рабочего пространства `.vs` каталога.
1. Запрошенный путь самого.
1. Родительский каталог создаваемого запрошенный путь.
1. Все дополнительные родительские каталоги, включая корневой рабочей области.
1. «Глобальные параметры», которые находится в каталоге пользователя.

Результат — это экземпляр <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings>. Этот объект содержит параметры для определенного типа и могут запрашиваться для ключа имена параметров, хранящихся как `string`. <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings.GetProperty%2A> Методы и <xref:Microsoft.VisualStudio.Workspace.Settings.WorkspaceSettingsExtensions> методы расширения ожидают вызывающему объекту известен тип запрашиваемого значение параметра. Так как большинство файлов параметры сохраняются как _.json_ файлы, будет использовать много вызовов `string`, `bool`, `int`и массивы этих типов. Также поддерживаются типы объектов. В таких случаях можно использовать `IWorkspaceSettings` себя в качестве аргумента типа. Пример:

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

При условии, что эти параметры были в пользователя _VSWorkspaceSettings.json_, данные доступны в виде:

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
>Эти параметры API-интерфейсы не связаны с API, доступных в `Microsoft.VisualStudio.Settings` пространства имен. Параметры рабочей области не зависят от узла и использовать файлы параметров, относящихся к рабочей области или поставщиков динамических параметров.

### <a name="providing-dynamic-settings"></a>Предоставление динамических параметров

Расширения могут предоставить <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsProvider>s. Эти поставщики в памяти разрешить расширения для добавления параметров или переопределить другим пользователям.

Экспорт `IWorkspaceSettingsProvider` отличается от других поставщиков рабочей области. Фабрика не `IWorkspaceProviderFactory` и нет специального атрибута типа. Вместо этого реализовать <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsProviderFactory> и использовать `[Export(typeof(IWorkspaceSettingsProviderFactory))]`.

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
>При реализации методов, возвращающих `IWorkspaceSettingsSource` (таких как `IWorkspaceSettingsProvider.GetSingleSettings`), возвращают экземпляр `IWorkspaceSettings` вместо `IWorkspaceSettingsSource`. `IWorkspaceSettings` предоставляет дополнительные сведения, которые могут быть полезны во время некоторые параметры агрегатов.

### <a name="settings-related-apis"></a>API, связанные с параметрами

- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager> Считывает и объединяет параметры для рабочей области.
- <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetSettingsManager%2A> Получает `IWorkspaceSettingsManager` для рабочей области.
- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager.GetAggregatedSettings%2A> Возвращает параметры для данной области, совокупная для всех перекрывающихся областей.
- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings> содержит параметры для определенной области.

## <a name="workspace-suggested-practices"></a>Рабочая область Предлагаемые рекомендации

- Возвращает объекты из `IWorkspaceProviderFactory.CreateProvider` или аналогичный API, которые их `Workspace` контекст при создании. Интерфейсы поставщиков записываются, ожидается, что этот объект сохраняется при создании.
- Сохраните кэши определенной рабочей области или их параметры «Локальные параметры» путь к рабочей области. Создание пути для файлов с помощью `Microsoft.VisualStudio.Workspace.WorkspaceHelper.MakeRootedUnderWorkingFolder` в Visual Studio 2017 версии 15.6 или более поздней версии. Для версий, предшествующих версии 15.6 используйте следующий фрагмент кода:

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

## <a name="solution-events-and-package-auto-load"></a>События решения и автоматически загрузить пакет

Можно реализовать загруженных пакетов `IVsSolutionEvents7` и вызвать `IVsSolution.AdviseSolutionEvents`. Она включает обработку событий на открытие и закрытие папки в Visual Studio.

Контекст пользовательского интерфейса можно использовать для автоматической загрузки пакета. Значение — `4646B819-1AE0-4E79-97F4-8A8176FDD664`.

## <a name="troubleshooting"></a>Устранение неполадок

### <a name="the-sourceexplorerpackage-package-did-not-load-correctly"></a>SourceExplorerPackage пакет не был правильно загружен

Расширяемость рабочей области во многом на основе MEF, и ошибок композиции приведет размещение открыть папку, чтобы не удалось загрузить пакет. Например, если расширение экспортирует тип с `ExportFileContextProviderAttribute`, но тип реализует только `IWorkspaceProviderFactory<IFileContextActionProvider>`, произойдет ошибка при попытке открыть папку в Visual Studio. Сведения об ошибке можно найти в _%LOCALAPPDATA%\Microsoft\VisualStudio\15.0_id\ComponentModelCache\Microsoft.VisualStudio.Default.err_. Устраните все ошибки, для типов, реализованная в расширении.

## <a name="next-steps"></a>Следующие шаги

* [Файл контексты](workspace-file-contexts.md) -поставщики контекста файлов перевести код аналитики для рабочих областей, открыть папку.
* [Индексирование](workspace-indexing.md) -индексирования рабочей области собирает и сохраняет сведения о рабочем пространстве.
