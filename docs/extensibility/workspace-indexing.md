---
title: Рабочая область индексирования в Visual Studio | Документы Microsoft
ms.custom: ''
ms.date: 02/21/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 3163e98c-1c79-48a7-813f-7923be894ba1
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 5004db0d895d1fdc697c18606c346c24cd484527
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="workspace-indexing"></a>Индексирование в рабочей области

В решении, системы проектов несут ответственность за предоставление функциональные возможности для построения, отладки, **GoTo** поиск символов и многое другое. Системы проектов можно сделать эту работу, поскольку они понимают, отношения и возможности файлы в проекте. [Открыть папку](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) рабочей области должен же подробные сведения для предоставления также богатые возможности интегрированной среды разработки. Коллекции и постоянное хранилище данных — это процесс, называемого индексированием рабочей области. Это индексированных данных можно выполнять запросы через набор асинхронные API. Расширителей могут участвовать в процессе индексирования, предоставляя <xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScanner>, которые известны способы их обработки определенных типов файлов.

## <a name="types-of-indexed-data"></a>Типы индексированных данных.

Существует три вида данных, которые индексируются. Обратите внимание, что тип, ожидаемый от сканеров файла отличается от типа, десериализации из индекса.

|Данные|Тип файла сканера|Тип результата запроса индекса|Связанные типы|
|--|--|--|--|
|Ссылки|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfo>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfoType>|
|Символы|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinition>|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinitionSearchResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.ISymbolService> следует использовать вместо `IIndexWorkspaceService` для запросов|
|Значения данных|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataValue>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataResult`1>||

## <a name="querying-for-indexed-data"></a>Запрос индексированных данных

Существует два асинхронных типа, для доступа к материализованных данных. Во-первых, через <xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceData>. Он обеспечивает базовый доступ к одному файлу `FileReferenceResult` и `FileDataResult` данных, который кэширует результаты. Во-вторых, <xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceService> которого не использовать кэширование, но обеспечивает дополнительные возможности запросов.

```csharp
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Indexing;

private static IIndexWorkspaceData GetCachedIndexedData(IWorkspace workspace)
{
    // Gets access to indexed data wrapped in a cache.
    return workspace?.GetIndexWorkspaceDataService()?.CreateIndexWorkspaceData();
}

private static IIndexWorkspaceService GetDirectIndexedData(IWorkspace workspace)
{
    // Gets direct access to indexed data.
    // Can also be casted to IIndexWorkspaceService2.
    return workspace?.GetIndexWorkspaceService();
}
```

## <a name="participating-in-indexing"></a>Участие в индексирования

Индексирование рабочей области ниже примерно следующую последовательность:

1. Обнаружение и сохранение файла системные объекты в рабочей области (только в начальной открытия scan).
1. Каждого файла, соответствующего поставщика с самым высоким приоритетом получит запрос на поиск `FileReferenceInfo`s.
1. Каждого файла, соответствующего поставщика с самым высоким приоритетом получит запрос на поиск `SymbolDefinition`s.
1. Каждого файла, запрашиваются все поставщики `FileDataValue`s.

Расширения можно экспортировать сканер, реализовав `IWorkspaceProviderFactory<IFileScanner>` и экспорта типа с <xref:Microsoft.VisualStudio.Workspace.Indexing.ExportFileScannerAttribute>. `SupportedTypes` Аргументом атрибута должно быть одно или несколько значений из <xref:Microsoft.VisualStudio.Workspace.Indexing.FileScannerTypeConstants>. Пример сканер, в разделе VS SDK [пример](https://github.com/Microsoft/VSSDK-Extensibility-Samples/blob/master/Open_Folder_Extensibility/C%23/SymbolScannerSample/TxtFileSymbolScanner.cs).

> [!WARNING]
> Не экспортировать файл сканера, поддерживающего `FileScannerTypeConstants.FileScannerContentType` типа. Он используется Microsoft только для внутренних целей.

В более сложных ситуациях расширение может динамически поддерживает произвольный набор типов файлов. Вместо того чтобы экспортировать MEF `IWorkspaceProviderFactory<IFileScanner>`, можно экспортировать расширение `IWorkspaceProviderFactory<IFileScannerProvider>`. Когда индексирование начинается, этот тип фабрики будет импортированных, экземпляр и иметь его <xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScannerProvider.GetSymbolScannersAsync%2A> вызванного метода. `IFileScanner` экземпляры, поддерживающие любое значение от `FileScannerTpeConstants` будет принят на обработку, не только символы.

## <a name="next-steps"></a>Следующие шаги

* [Рабочие области и языковые службы](workspace-language-services.md) -сведения об интеграции служб языка в рабочую область открыть папку.
* [Рабочая область построения](workspace-build.md) -открыть папку поддерживает построение систем, таких как MSBuild и файлы makefile.