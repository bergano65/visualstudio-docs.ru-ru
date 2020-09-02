---
title: Рабочие области в Visual Studio | Документация Майкрософт
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 011781b434c4d005e473c5f97c60a9269dc5d034
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62952767"
---
# <a name="workspaces"></a>Рабочие области

Рабочая область — это то, как Visual Studio представляет коллекцию файлов в [открытой папке](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)и представляется <xref:Microsoft.VisualStudio.Workspace.IWorkspace> типом. Сама по себе Рабочая область не понимает содержимое или функции, связанные с файлами в папке. Вместо этого он предоставляет общий набор интерфейсов API для функций и расширений для создания и использования данных, с которыми могут работать другие пользователи. Производители состоят из [Managed Extensibility Framework](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (MEF) с использованием различных атрибутов экспорта.

## <a name="workspace-providers-and-services"></a>Поставщики и службы рабочей области

Поставщики рабочих областей и службы предоставляют данные и функции для реагирования на содержимое рабочей области. Они могут предоставлять контекстные сведения о файлах, символы в исходных файлах или функции сборки.

В обоих понятиях используется [шаблон фабрики](https://en.wikipedia.org/wiki/Factory_method_pattern) и они импортируются в рамках рабочей области с помощью MEF. Все атрибуты экспорта реализуют `IProviderMetadataBase` или `IWorkspaceServiceFactoryMetadata` , но существуют конкретные типы, которые расширения должны использовать для экспортируемых типов.

Одно различие между поставщиками и службами — их связь с рабочей областью. Рабочая область может иметь множество поставщиков определенного типа, но для каждой рабочей области создается только одна служба определенного типа. Например, Рабочая область содержит много поставщиков сканеров файлов, но Рабочая область содержит только одну службу индексирования для каждой рабочей области.

Другим ключевым отличием является использование данных от поставщиков и служб. Рабочая область — это точка входа для получения данных от поставщиков по нескольким причинам. Во первых, поставщики обычно имеют некоторый узкий набор создаваемых данных. Данные могут быть символами для исходного файла C# или контекстами файлов сборки для _CMakeLists.txt_ файла. Рабочая область будет соответствовать запросу потребителя поставщикам, метаданные которых соответствуют запросу. Во-вторых, некоторые сценарии позволяют многим поставщикам участвовать в запросе, в то время как другие сценарии используют поставщик с наивысшим приоритетом.

Расширения, напротив, могут получать экземпляры и взаимодействовать напрямую со службами рабочей области. Методы расширения `IWorkspace` доступны для служб, предоставляемых Visual Studio, таких как <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetFileWatcherService%2A> . Расширение может предоставлять службу рабочей области для компонентов в вашем расширении или для использования другими расширениями. Потребители должны использовать <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetServiceAsync%2A> или метод расширения, предоставленный для `IWorkspace` типа.

>[!WARNING]
> Не создавайте службы, которые конфликтуют с Visual Studio. Это может привести к непредвиденным проблемам.

## <a name="disposal-on-workspace-closure"></a>Реализация при закрытии рабочей области

При закрытии рабочей области расширителям может потребоваться удалить, но вызвать асинхронный код. <xref:Microsoft.VisualStudio.Threading.IAsyncDisposable>Интерфейс доступен для упрощения написания этого кода.

## <a name="related-types"></a>Связанные типы

- <xref:Microsoft.VisualStudio.Workspace.IWorkspace> является центральной сущностью открытой рабочей области, такой как открытая папка.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspaceProviderFactory`1> Создает поставщик для каждого экземпляра рабочей области.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspaceServiceFactory> создает службу для каждой созданной рабочей области.
- <xref:Microsoft.VisualStudio.Threading.IAsyncDisposable> должен быть реализован в поставщиках и службах, которым необходимо выполнять асинхронный код во время реализации.
- <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper> предоставляет вспомогательные методы для доступа к хорошо известным службам или произвольным службам.

## <a name="workspace-settings"></a>Параметры рабочей области

Рабочие области имеют <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager> службу с простым, но мощным контролем над рабочей областью. Основные общие сведения о параметрах см. в разделе [Настройка задач сборки и отладки](../ide/customize-build-and-debug-tasks-in-visual-studio.md).

Для большинства `SettingsType` типов параметров используются файлы _. JSON_ , такие как _VSWorkspaceSettings.jsв_ и _tasks.vs.js_.

Возможности параметров рабочей области изменяются по областям, которые просто являются путями в рабочей области. При вызове потребителя <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager.GetAggregatedSettings%2A> все области, включающие запрошенный путь и тип параметра, суммируются. Приоритет статистической обработки области выглядит следующим образом:

1. «Локальные параметры», обычно это каталог корневого каталога рабочей области `.vs` .
1. Запрошенный путь.
1. Родительский каталог запрошенного пути.
1. Все последующие родительские каталоги вплоть до корня рабочей области включительно.
1. "Глобальные параметры", которые находятся в каталоге пользователя.

Результатом является экземпляр <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings> . Этот объект содержит параметры для конкретного типа и может быть запрошен для настройки имен ключей, хранящихся в `string` . <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings.GetProperty%2A>Методы и <xref:Microsoft.VisualStudio.Workspace.Settings.WorkspaceSettingsExtensions> методы расширения предполагают, что вызывающий объект знает тип запрашиваемого значения параметра. Так как большинство файлов параметров сохраняются в виде _JSON_ , многие вызовы будут использовать `string` `bool` `int` массивы типов,, и. Также поддерживаются типы объектов. В таких случаях можно использовать себя в `IWorkspaceSettings` качестве аргумента типа. Пример:

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

Предполагая, что эти параметры были в _VSWorkspaceSettings.js_пользователя, доступ к данным можно получить следующим образом:

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
>Эти API параметров не связаны с интерфейсами API, доступными в `Microsoft.VisualStudio.Settings` пространстве имен. Параметры рабочей области не зависят от узла и используют файлы параметров рабочей области или поставщики динамических параметров.

### <a name="providing-dynamic-settings"></a>Предоставление динамических параметров

Расширения могут предоставлять <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsProvider> s. Эти поставщики в памяти позволяют расширениям добавлять параметры или переопределять другие.

Экспорт отличается `IWorkspaceSettingsProvider` от других поставщиков рабочих областей. Фабрика не `IWorkspaceProviderFactory` существует, и отсутствует специальный тип атрибута. Вместо этого реализуйте <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsProviderFactory> и используйте `[Export(typeof(IWorkspaceSettingsProviderFactory))]` .

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
>При реализации методов, которые возвращают `IWorkspaceSettingsSource` (Like `IWorkspaceSettingsProvider.GetSingleSettings` ), следует возвращать экземпляр, `IWorkspaceSettings` а не `IWorkspaceSettingsSource` . `IWorkspaceSettings` предоставляет дополнительные сведения, которые могут быть полезны при выполнении некоторых агрегатов параметров.

### <a name="settings-related-apis"></a>Связанные с параметрами API

- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager> операции чтения и агрегирования параметров для рабочей области.
- <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetSettingsManager%2A> Возвращает `IWorkspaceSettingsManager` для рабочей области.
- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager.GetAggregatedSettings%2A> Возвращает параметры для данной области, агрегированной по всем перекрывающимся областям.
- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings> содержит параметры для определенной области.

## <a name="workspace-suggested-practices"></a>Рекомендуемые методики рабочей области

- Возвращают объекты из `IWorkspaceProviderFactory.CreateProvider` или аналогичных API, которые запоминают `Workspace` контекст при создании. Интерфейсы поставщиков записываются, ожидая, что этот объект сохраняется при создании.
- Сохранение кэшей или параметров рабочей области в папке "Локальные параметры" рабочей области. Создайте путь к файлу с помощью `Microsoft.VisualStudio.Workspace.WorkspaceHelper.MakeRootedUnderWorkingFolder` в Visual Studio 2017 версии 15,6 или более поздней. Для версий, предшествовавших версии 15,6, используйте следующий фрагмент кода:

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

## <a name="solution-events-and-package-auto-load"></a>События и автоматическая загрузка пакетов

Загруженные пакеты могут реализовывать `IVsSolutionEvents7` и вызывать `IVsSolution.AdviseSolutionEvents` . Он включает в себя события при открытии и закрытии папки в Visual Studio.

Контекст пользовательского интерфейса можно использовать для автоматической загрузки пакета. Значение равно `4646B819-1AE0-4E79-97F4-8A8176FDD664`.

## <a name="troubleshooting"></a>Устранение неполадок

### <a name="the-sourceexplorerpackage-package-did-not-load-correctly"></a>Пакет Саурцеексплорерпаккаже не был правильно загружен

Расширяемость рабочей области в значительной степени основана на MEF, а ошибки композиции приведут к сбою загрузки пакета с открытой папкой. Например, если расширение экспортирует тип с `ExportFileContextProviderAttribute` , но тип реализуется `IWorkspaceProviderFactory<IFileContextActionProvider>` , при попытке открыть папку в Visual Studio возникнет ошибка.

::: moniker range="vs-2017"

Сведения об ошибке можно найти в _%localappdata%\microsoft\visualstudio\15.0_id \компонентмоделкаче\микрософт.висуалстудио.дефаулт.ЕРР_. Устраните все ошибки для типов, реализованных вашим расширением.

::: moniker-end

::: moniker range=">=vs-2019"

Сведения об ошибке можно найти в _%localappdata%\microsoft\visualstudio\16.0_id \компонентмоделкаче\микрософт.висуалстудио.дефаулт.ЕРР_. Устраните все ошибки для типов, реализованных вашим расширением.

::: moniker-end

## <a name="next-steps"></a>Дальнейшие действия

* Контексты [файлов](workspace-file-contexts.md) . поставщики контекстов файлов предоставляют логику операций с кодом для открытых рабочих областей папок.
* [Индексирование](workspace-indexing.md) — индексирование рабочей области собирает и сохраняет сведения о рабочей области.
