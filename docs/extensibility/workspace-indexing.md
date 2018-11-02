---
title: Рабочая область, индексирование в Visual Studio | Документация Майкрософт
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
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49939154"
---
# <a name="workspace-indexing"></a>Индексирование в рабочей области

В решении, проект системы отвечают за предоставление функциональных возможностей для построения, отладки, **GoTo** поиск символа и многое другое. Системы проектов может сделать это вместо, так как они понять, отношения и возможности файлов в проекте. [Открыть папку](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) рабочая область должна же получить представление о, предоставляют широкие возможности интегрированной среды разработки также. Сбор и постоянное хранение этих данных — это процесс, называемого индексированием рабочей области. Эти индексированные данные можно запрашивать через набор асинхронных интерфейсов API. Расширители могут участвовать в процессе индексирования, предоставляя <xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScanner>s, который знает как обрабатывать определенные типы файлов.

## <a name="types-of-indexed-data"></a>Типы индексированных данных

Существует три типа данных, которые индексируются. Обратите внимание, что тип, ожидаемый от сканеров файла отличается от типа десериализован из индекса.

|Данные|Тип файла сканера|Тип результата запроса в индекс|Связанные типы|
|--|--|--|--|
|Ссылки|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfo>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfoType>|
|Символы|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinition>|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinitionSearchResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.ISymbolService> следует использовать вместо `IIndexWorkspaceService` для запросов|
|Значения данных|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataValue>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataResult`1>||

## <a name="querying-for-indexed-data"></a>Запрос индексированных данных

Существует два асинхронных типа, для доступа к материализованных данных. Во-первых, через <xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceData>. Он обеспечивает базовый доступ к одному файлу `FileReferenceResult` и `FileDataResult` данные и кэширует результаты. Второй — <xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceService> которых не использовать кэширование, но обеспечивает дополнительные возможности выполнения запросов.

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

## <a name="participating-in-indexing"></a>Участие в индексирование

Примерно индексирования рабочей области соответствует следующей последовательности:

1. Обнаружение и сохранения файла системных сущностей в рабочей области (только на открытие начальной проверки).
1. На файл, соответствующий поставщик с самым высоким приоритетом предлагается для проверки на наличие `FileReferenceInfo`s.
1. На файл, соответствующий поставщик с самым высоким приоритетом предлагается для проверки на наличие `SymbolDefinition`s.
1. Каждого файла, запрашиваются все поставщики `FileDataValue`s.

Расширения можно экспортировать сканера путем реализации `IWorkspaceProviderFactory<IFileScanner>` и экспорт типа с <xref:Microsoft.VisualStudio.Workspace.Indexing.ExportFileScannerAttribute>. `SupportedTypes` Аргументом атрибута должно быть одно или несколько значений из <xref:Microsoft.VisualStudio.Workspace.Indexing.FileScannerTypeConstants>. Пример сканер, см. в разделе VS SDK [пример](https://github.com/Microsoft/VSSDK-Extensibility-Samples/blob/master/Open_Folder_Extensibility/C%23/SymbolScannerSample/TxtFileSymbolScanner.cs).

> [!WARNING]
> Не экспортируйте файл сканера, поддерживающего `FileScannerTypeConstants.FileScannerContentType` типа. Он используется Microsoft только для внутренних целей.

В сложных ситуациях расширение может динамически поддерживает произвольный набор типов файлов. Вместо того чтобы Экспорт MEF `IWorkspaceProviderFactory<IFileScanner>`, расширение можно экспортировать `IWorkspaceProviderFactory<IFileScannerProvider>`. Когда индексирование начинается, этот тип фабрики будет должна импортироваться, создан и у его <xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScannerProvider.GetSymbolScannersAsync%2A> вызванного метода. `IFileScanner` экземпляры, которые поддерживают любое значение от `FileScannerTpeConstants` будут выполняться, не только символы.

## <a name="next-steps"></a>Следующие шаги

* [Рабочие области и языковых служб](workspace-language-services.md) -как интегрировать службы языка в открытой папке рабочей области.
* [Рабочая область построения](workspace-build.md) — открыть папку поддерживает построение систем, таких как MSBuild и файлы makefile.