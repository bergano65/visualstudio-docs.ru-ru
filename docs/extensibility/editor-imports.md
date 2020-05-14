---
title: Редактор Импорт (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - services
ms.assetid: 8d096de3-33b4-427a-a122-4aeff8a72da0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c6af95b452166aa71950ac1e869d333d12d857b9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712014"
---
# <a name="editor-imports"></a>Импорт редактора
Вы можете импортировать ряд услуг редактора, заводов и брокеров, которые предоставляют ваше расширение с различными видами доступа к основному редактору. Например, можно импортировать, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> чтобы <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> предоставить вам данный тип содержимого. (Этот навигатор позволяет выполнять различные виды поиска в буфере текста.)

 Чтобы использовать импорт редактора, вы импортируете его в поле или свойство класса, экспортируемого компонента Рамочной основы управляемой расширительности.

> [!NOTE]
> Для получения дополнительной информации о Рамочной системе управляемого повышения [см.](/dotnet/framework/mef/index)

## <a name="import-syntax"></a>Импортный синтаксис
 Ниже приводится следующий пример, как импортировать услугу фабрики вариантов редактора.

```
[Import]
internal IEditorOptionsFactoryService EditorOptions { get; set; }
```

 Если вы хотите импортировать службу в качестве поля, а `null` не свойства, вы должны установить его в декларации, чтобы избежать предупреждения компилятора о не назначении переменной:

```
[Import]
internal IEditorOptionsFactoryService m_editorOptions = null;
```

 Дополнительные примеры использования импорта можно найти в следующих пошаговых предложениях:

- [Прохождение: Создать маржиглиф](../extensibility/walkthrough-creating-a-margin-glyph.md)

- [Пошаговое: Настроить текстовое представление](../extensibility/walkthrough-customizing-the-text-view.md)

- [Пошаговое прохождение: Выделите текст](../extensibility/walkthrough-highlighting-text.md)

- [Прохождение: Отображение инструментов quickInfo](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)

- [Пошаговая прогулка: Помощь в отображении подписи](../extensibility/walkthrough-displaying-signature-help.md)

- [Пошаговое руководство. Отображение завершения операторов](../extensibility/walkthrough-displaying-statement-completion.md)

- [Прохождение: Отображение лампочки предложения](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)

## <a name="import-the-service-provider"></a>Импорт поставщика услуг
 Вы также можете <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> импортировать (находится в сборке Microsoft.VisualStudio.Shell.Immutable.10.0) таким же образом, чтобы получить доступ к услугам Visual Studio:

```csharp
[Import]
internal SVsServiceProvider ServiceProvider = null;
```

 Смотрите [Walkthrough: Доступ к объекту DTE из расширения редактора](../extensibility/walkthrough-accessing-the-dte-object-from-an-editor-extension.md) для получения дополнительной информации.

## <a name="services"></a>Службы
 Службы редактора, как правило, являются отдельными объектами, предоставляющими услуги и совместно распределенными по нескольким компонентам.

|Импорт|Предоставляет|
|------------|--------------|
|<xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService>|Взаимосвязь между расширениями <xref:Microsoft.VisualStudio.Utilities.IContentType> файлов и объектами.|
|<xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>|Коллекция объектов <xref:Microsoft.VisualStudio.Utilities.IContentType>.|
|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformationService>|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformation>Объектов.|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>|Многие объекты адаптера редактора:<br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|
|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearchFactoryService>|Объект <xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearch> для заданного текстового представления.|
|<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>|<xref:Microsoft.VisualStudio.Text.ITextBuffer>.|
|<xref:Microsoft.VisualStudio.Text.ITextDocumentFactoryService>|<xref:Microsoft.VisualStudio.Text.ITextDocument>.|
|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceService>|Разница <xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceCollection%601> в чем.|
|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalStringDifferenceService>|Разница <xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalDifferenceCollection> в чем.|
|<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>|A <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> или <xref:Microsoft.VisualStudio.Text.Projection.IElisionBuffer>.|
|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>|Для <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph> набора объектов. <xref:Microsoft.VisualStudio.Text.ITextBuffer>|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>|An <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> для <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|
|<xref:Microsoft.VisualStudio.Text.Classification.IViewClassifierAggregatorService>|An <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> для <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMapService>|An <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap> для <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|
|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>|An <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap> для <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>|Поддерживает сбор объектов. <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>|
|<xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>|Для <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> буфера текста.|
|<xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService>|Для <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> текстового представления.|
|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptionsFactoryService>|Для <xref:Microsoft.VisualStudio.Text.Editor.IEditorOptions> указанного объема.|
|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMapFactoryService>|Для <xref:Microsoft.VisualStudio.Text.Editor.IScrollMap> текстового представления.|
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|An <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndent> для <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|Получает автоматический отступ через <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentProvider> объекты.|
|<xref:Microsoft.VisualStudio.Text.Editor.ITextEditorFactoryService>|Управляет <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> для <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>.|
|<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedTextSourceFactoryService>|<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource>.|
|<xref:Microsoft.VisualStudio.Text.Formatting.IRtfBuilderService>|Генерирует текст с форматом RTF из набора диапазонов моментальных снимков.|
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencerFactoryService>|An <xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencer> для <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextParagraphPropertiesFactoryService>|Для <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> форматирования текстовых строк в представлении.|
|<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService>|Объект <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperations> для <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>|Поиск моментального снимка текста.|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>|An <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> для <xref:Microsoft.VisualStudio.Text.ITextBuffer> <xref:Microsoft.VisualStudio.Utilities.IContentType>by .|
|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService>|Для <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager> текстового представления.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IGlyphService>|Стандартный набор глифов.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStackMapService>|An <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStack> для <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IWpfKeyboardTrackingService>|Отслеживает обработку клавиатуры.|
|<xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService>|Стандартные <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> объекты.|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistoryRegistry>|Поддерживает связь между текстовыми <xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistory> буферами и объектами.|

## <a name="other-imports"></a>Прочие импортные товары
 Фабрики-поставщики и брокеры, как правило, являются субъектами, которые могут иметь несколько экземпляров в нескольких компонентах.

|Импорт|Предоставляет|
|------------|--------------|
|<xref:Microsoft.VisualStudio.Text.Adornments.IErrorProviderFactory>|A <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> типа <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>) для данного буфера.|
|<xref:Microsoft.VisualStudio.Text.Adornments.ITextMarkerProviderFactory>|Текстовый маркер tagger <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> (тип). <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>|
|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProviderFactory>|An <xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProvider> для <xref:Microsoft.VisualStudio.Text.Editor.ITextView>данного .|
|<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>|<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>|<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSession>.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>|<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSession>.|

## <a name="see-also"></a>См. также
- [Языковой сервис и точки расширения редактора](../extensibility/language-service-and-editor-extension-points.md)
