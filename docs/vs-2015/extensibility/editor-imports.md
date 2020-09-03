---
title: Редактор импортирует | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - services
ms.assetid: 8d096de3-33b4-427a-a122-4aeff8a72da0
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1fc32d0126d912acab104ecefe3cb62d80b8513f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690322"
---
# <a name="editor-imports"></a>Импорт в редакторе
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Можно импортировать несколько служб редактора, фабрик и брокеров, которые предоставляют расширение с разными видами доступа к основному редактору. Например, можно импортировать, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> чтобы предоставить <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> для определенного типа содержимого. (Этот Навигатор позволяет выполнять различные виды поиска в текстовом буфере.)  
  
 Чтобы использовать импорт редактора, импортируйте его как поле или свойство класса, который экспортирует компонент Managed Extensibility Framework компонента.  
  
> [!NOTE]
> Дополнительные сведения о Managed Extensibility Framework см. в разделе [Managed Extensibility Framework (MEF)](https://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde).  
  
## <a name="import-syntax"></a>Синтаксис импорта  
 В следующем примере показано, как импортировать службу фабрики параметров редактора.  
  
```  
[Import]  
internal IEditorOptionsFactoryService EditorOptions { get; set; }  
```  
  
 Если вы хотите импортировать службу как поле, а не свойство, следует задать для него значение `null` в объявлении, чтобы избежать предупреждений компилятора о неназначении переменной.  
  
```  
[Import]  
internal IEditorOptionsFactoryService m_editorOptions = null;  
```  
  
 Дополнительные примеры использования импортов см. в следующих пошаговых руководствах.  
  
 [Пошаговое руководство. Создание глифа поля](../extensibility/walkthrough-creating-a-margin-glyph.md)  
  
 [Пошаговое руководство. Настройка представления текста](../extensibility/walkthrough-customizing-the-text-view.md)  
  
 [Пошаговое руководство. Выделение текста](../extensibility/walkthrough-highlighting-text.md)  
  
 [Пошаговое руководство. Отображение всплывающих подсказок для кратких сведений](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)  
  
 [Пошаговое руководство. Отображение справки сигнатуры](../extensibility/walkthrough-displaying-signature-help.md)  
  
 [Пошаговое руководство. Отображение завершения операторов](../extensibility/walkthrough-displaying-statement-completion.md)  
  
 [Пошаговое руководство. Отображение смарт-тегов](../misc/walkthrough-displaying-smarttags.md)  
  
## <a name="importing-the-service-provider"></a>Импорт поставщика услуг  
 Чтобы <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> получить доступ к службам Visual Studio, можно также импортировать (в сборке Microsoft. VisualStudio. Shell. неизменяемый. 10.0).  
  
```  
[Import]  
internal SVsServiceProvider ServiceProvider = null;   
```  
  
 Дополнительные сведения см. [в разделе Пошаговое руководство. доступ к объекту DTE из расширения редактора](../extensibility/walkthrough-accessing-the-dte-object-from-an-editor-extension.md) .  
  
## <a name="services"></a>Службы  
 Службы редактора обычно являются отдельными сущностями, которые предоставляют службу и являются общими для нескольких компонентов.  
  
|Импорт|Предоставляет|  
|------------|--------------|  
|<xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService>|Отношение между расширениями файлов и <xref:Microsoft.VisualStudio.Utilities.IContentType> объектами.|  
|<xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>|Коллекция объектов <xref:Microsoft.VisualStudio.Utilities.IContentType>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformationService>|Объекты <xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformation>|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>|Многие объекты адаптера редактора:<br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|  
|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearchFactoryService>|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearch>Объект для заданного текстового представления.|  
|<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>|Объект <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|  
|<xref:Microsoft.VisualStudio.Text.ITextDocumentFactoryService>|Объект <xref:Microsoft.VisualStudio.Text.ITextDocument>.|  
|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceService>|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceCollection%601>Различия между ними.|  
|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalStringDifferenceService>|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalDifferenceCollection>Различия между ними.|  
|<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>|Объект <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> или <xref:Microsoft.VisualStudio.Text.Projection.IElisionBuffer> .|  
|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph>Для набора <xref:Microsoft.VisualStudio.Text.ITextBuffer> объектов.|  
|<xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>|<xref:Microsoft.VisualStudio.Text.Classification.IClassifier>Для <xref:Microsoft.VisualStudio.Text.ITextBuffer> .|  
|<xref:Microsoft.VisualStudio.Text.Classification.IViewClassifierAggregatorService>|<xref:Microsoft.VisualStudio.Text.Classification.IClassifier>Для <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|  
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMapService>|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap>Для <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|  
|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap>Для <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|  
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>|Поддерживает коллекцию <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> объектов.|  
|<xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>|Объект <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> для текстового буфера.|  
|<xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService>|<xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601>Для текстового представления.|  
|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptionsFactoryService>|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptions>Для указанной области.|  
|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMapFactoryService>|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMap>Для текстового представления.|  
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndent>Для <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|  
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|Возвращает автоматический отступ через <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentProvider> объекты.|  
|<xref:Microsoft.VisualStudio.Text.Editor.ITextEditorFactoryService>|Управляет <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> для <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> .|  
|<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedTextSourceFactoryService>|Объект <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource>.|  
|<xref:Microsoft.VisualStudio.Text.Formatting.IRtfBuilderService>|Создает текст в формате RTF из набора диапазонов снимка.|  
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencerFactoryService>|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencer>Для <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|  
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextParagraphPropertiesFactoryService>|Объект <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> для форматирования строк текста в представлении.|  
|<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService>|<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperations>Объект для <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|  
|<xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>|Выполняет поиск моментального снимка текста.|  
|<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>|Объект <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> для <xref:Microsoft.VisualStudio.Text.ITextBuffer> <xref:Microsoft.VisualStudio.Utilities.IContentType> .|  
|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService>|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager>Для текстового представления.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IGlyphService>|Стандартный набор глифов.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStackMapService>|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStack>Для <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IWpfKeyboardTrackingService>|Отслеживает обработку клавиатуры.|  
|<xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService>|Стандартные <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> объекты.|  
|<xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistoryRegistry>|Поддерживает связь между текстовыми буферами и  <xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistory> объектами.|  
  
## <a name="other-imports"></a>Другие операции импорта  
 Фабрики поставщиков и брокеры — это обычно сущности, которые могут иметь несколько экземпляров в нескольких компонентах.  
  
|Импорт|Предоставляет|  
|------------|--------------|  
|<xref:Microsoft.VisualStudio.Text.Adornments.IErrorProviderFactory>|Объект <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> типа <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> ) для заданного буфера.|  
|<xref:Microsoft.VisualStudio.Text.Adornments.ITextMarkerProviderFactory>|Средство создания тегов текстовых меток ( <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> типа <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> ).|  
|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProviderFactory>|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProvider>Для заданного объекта <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>|Объект <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>|Объект <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSession>.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>|Объект <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSession>.|  
  
## <a name="see-also"></a>См. также:  
 [Языковая служба и точки расширения редактора](../extensibility/language-service-and-editor-extension-points.md)
