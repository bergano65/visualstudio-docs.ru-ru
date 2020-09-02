---
title: Индексирование рабочих областей в Visual Studio | Документация Майкрософт
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 9bf7df777d27003fa5763debc772a8804ec28ef5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62952716"
---
# <a name="workspace-indexing"></a>Индексирование рабочей области

В решении системы проектов отвечают за предоставление функциональных возможностей для **сборки, отладки, поиска символов и** т. д. Системы проектов могут выполнять эту работу, поскольку они понимают отношение и возможности файлов в проекте. Рабочая область [открытой папки](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) должна иметь то же представление, что и возможности интегрированной среды разработки. Сбор и постоянное хранение этих данных — это процесс, называемый индексированием рабочей области. Эти индексированные данные можно запрашивать с помощью набора асинхронных API. Расширители могут участвовать в процессе индексирования, предоставляя <xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScanner> , что знает, как обрабатывать определенные типы файлов.

## <a name="types-of-indexed-data"></a>Типы индексированных данных

Существует три типа индексируемых данных. Обратите внимание, что тип, ожидаемый от сканеров файлов, отличается от типа, десериализованного из индекса.

|Данные|Тип сканера файлов|Тип результата запроса индекса|Связанные типы|
|--|--|--|--|
|Ссылки|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfo>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfoType>|
|Символы|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinition>|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinitionSearchResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.ISymbolService> следует использовать вместо `IIndexWorkspaceService` для запросов|
|Значения данных|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataValue>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataResult`1>||

## <a name="querying-for-indexed-data"></a>Запрос индексированных данных

Существует два асинхронных типа, доступных для доступа к материализованным данным. Первый — через <xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceData> . Он предоставляет базовый доступ к отдельным файлам `FileReferenceResult` и `FileDataResult` данным, а также кэширует результаты. Второй —, <xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceService> который не использует кэширование, но позволяет использовать дополнительные возможности запросов.

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

## <a name="participating-in-indexing"></a>Участие в индексировании

Индексирование рабочей области примерно следует за следующей последовательностью:

1. Обнаружение и сохранение сущностей файловой системы в рабочей области (только при первоначальном открытии проверки).
1. Для каждого файла поставщик сопоставления с наивысшим приоритетом запрашивает сканирование для `FileReferenceInfo` s.
1. Для каждого файла поставщик сопоставления с наивысшим приоритетом запрашивает сканирование для `SymbolDefinition` s.
1. Для каждого файла все поставщики запросят указать `FileDataValue` s.

Расширения могут экспортировать сканер, реализовав `IWorkspaceProviderFactory<IFileScanner>` и экспортировав тип с помощью <xref:Microsoft.VisualStudio.Workspace.Indexing.ExportFileScannerAttribute> . `SupportedTypes`Аргумент атрибута должен быть одним или несколькими значениями из <xref:Microsoft.VisualStudio.Workspace.Indexing.FileScannerTypeConstants> . Пример сканера см. в [примере](https://github.com/Microsoft/VSSDK-Extensibility-Samples/blob/master/Open_Folder_Extensibility/C%23/SymbolScannerSample/TxtFileSymbolScanner.cs)для пакета VS SDK.

> [!WARNING]
> Не экспортируйте средство проверки файлов, которое поддерживает этот `FileScannerTypeConstants.FileScannerContentType` тип. Он используется только для внутренних целей корпорации Майкрософт.

В более сложных ситуациях расширение может динамически поддерживать произвольный набор типов файлов. Вместо экспорта MEF `IWorkspaceProviderFactory<IFileScanner>` расширение может быть экспортировано `IWorkspaceProviderFactory<IFileScannerProvider>` . Когда начинается индексирование, этот тип фабрики будет импортирован, создан с созданием экземпляра и <xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScannerProvider.GetSymbolScannersAsync%2A> вызван его метод. `IFileScanner` все экземпляры, поддерживающие любое значение из `FileScannerTpeConstants` , будут учитываться, а не только символами.

## <a name="next-steps"></a>Дальнейшие действия

* [Рабочие области и языковые службы](workspace-language-services.md) — сведения о том, как интегрировать языковые службы в рабочую область открытой папки.
* [Рабочая область сборка](workspace-build.md) . открытая папка поддерживает системы сборки, такие как MSBuild и Makefile.