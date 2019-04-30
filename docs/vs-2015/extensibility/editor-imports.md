---
title: Импорт в редакторе | Документация Майкрософт
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
ms.openlocfilehash: 4805bff12d284dc5a54451e157c9e8fb92deeae2
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63432129"
---
# <a name="editor-imports"></a>Импорт в редакторе
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Вы можете импортировать несколько служб редактора фабрик и брокеров, которые предоставляют расширения с различными видами доступ к базовым редактором. Например, вы можете импортировать <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> добавив <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> для данного типа содержимого. (Этот навигатор позволяет выполнять различные виды поисковые запросы на текстовый буфер).  
  
 Чтобы использовать редактор импорта, импортируйте его как поля или свойства класса, который экспортирует в компоненте Managed Extensibility Framework.  
  
> [!NOTE]
> Дополнительные сведения о Managed Extensibility Framework, см. в разделе [Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde).  
  
## <a name="import-syntax"></a>Синтаксис импорта  
 Приведенный ниже показано, как импортировать редактора параметры фабрики служб.  
  
```  
[Import]  
internal IEditorOptionsFactoryService EditorOptions { get; set; }  
```  
  
 Если вы хотите импортировать службы в виде поля и не свойство, необходимо присвоить значение его `null` в объявлении, чтобы избежать предупреждений компилятора о не Присвоение переменной:  
  
```  
[Import]  
internal IEditorOptionsFactoryService m_editorOptions = null;  
```  
  
 Дополнительные примеры использования imports см. в разделе ниже пошаговых руководства:  
  
 [Пошаговое руководство: создание глифа поля](../extensibility/walkthrough-creating-a-margin-glyph.md)  
  
 [Пошаговое руководство: настройка представления текста](../extensibility/walkthrough-customizing-the-text-view.md)  
  
 [Пошаговое руководство: выделение текста](../extensibility/walkthrough-highlighting-text.md)  
  
 [Пошаговое руководство: отображение всплывающих подсказок для кратких сведений](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)  
  
 [Пошаговое руководство: отображение справки по цифровым подписям](../extensibility/walkthrough-displaying-signature-help.md)  
  
 [Пошаговое руководство: отображение завершения операторов](../extensibility/walkthrough-displaying-statement-completion.md)  
  
 [Пошаговое руководство: Отображение смарт-тегов](../misc/walkthrough-displaying-smarttags.md)  
  
## <a name="importing-the-service-provider"></a>Импорт поставщика услуг  
 Можно также импортировать <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> (найдено в сборке Microsoft.VisualStudio.Shell.Immutable.10.0) таким же образом, чтобы получить доступ к службам Visual Studio:  
  
```  
[Import]  
internal SVsServiceProvider ServiceProvider = null;   
```  
  
 См. [Пошаговое руководство: Доступ к объекту DTE из расширения редактора](../extensibility/walkthrough-accessing-the-dte-object-from-an-editor-extension.md) Дополнительные сведения.  
  
## <a name="services"></a>Службы  
 Редактор службы — обычно одной сущности, которые предоставляют службы и являются общими для нескольких компонентов.  
  
|Импорт|Предоставляет|  
|------------|--------------|  
|<xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService>|Связь расширений файлов и <xref:Microsoft.VisualStudio.Utilities.IContentType> объектов.|  
|<xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>|Коллекция объектов <xref:Microsoft.VisualStudio.Utilities.IContentType>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformationService>|Объекты <xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformation>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>|Многие объекты адаптера редактора:<br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|  
|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearchFactoryService>|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearch> Объект для данного представления текста.|  
|<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>|Объект <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|  
|<xref:Microsoft.VisualStudio.Text.ITextDocumentFactoryService>|Объект <xref:Microsoft.VisualStudio.Text.ITextDocument>.|  
|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceService>|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceCollection%601> Различий.|  
|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalStringDifferenceService>|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalDifferenceCollection> Различий.|  
|<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>|<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> Или <xref:Microsoft.VisualStudio.Text.Projection.IElisionBuffer>.|  
|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph> Для набора <xref:Microsoft.VisualStudio.Text.ITextBuffer> объектов.|  
|<xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>|<xref:Microsoft.VisualStudio.Text.Classification.IClassifier> Для <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|  
|<xref:Microsoft.VisualStudio.Text.Classification.IViewClassifierAggregatorService>|<xref:Microsoft.VisualStudio.Text.Classification.IClassifier> Для <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMapService>|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap> Для <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap> Для <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>|Поддерживает коллекцию объектов <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> объектов.|  
|<xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>|<xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> Для текстового буфера.|  
|<xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService>|<xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> Для представления текста.|  
|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptionsFactoryService>|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptions> Для указанной области.|  
|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMapFactoryService>|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMap> Для представления текста.|  
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndent> Для <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|Возвращает автоматический отступ <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentProvider> объектов.|  
|<xref:Microsoft.VisualStudio.Text.Editor.ITextEditorFactoryService>|Управляет <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> для <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>.|  
|<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedTextSourceFactoryService>|Объект <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource>.|  
|<xref:Microsoft.VisualStudio.Text.Formatting.IRtfBuilderService>|Создает текст с форматированием RTF из набора диапазонов снимка.|  
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencerFactoryService>|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencer> Для <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextParagraphPropertiesFactoryService>|Объект <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> для форматирования строк текста в представлении.|  
|<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService>|Объект <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperations> для объекта <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>|Выполняет поиск в снимок текста.|  
|<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>|<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> Для <xref:Microsoft.VisualStudio.Text.ITextBuffer> по <xref:Microsoft.VisualStudio.Utilities.IContentType>.|  
|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService>|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager> Для представления текста.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IGlyphService>|Стандартный набор глифов.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStackMapService>|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStack> Для <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IWpfKeyboardTrackingService>|Отслеживает сочетания обработки.|  
|<xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService>|Стандартный <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> объектов.|  
|<xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistoryRegistry>|Поддерживает связь между текстовыми буферами и <xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistory> объектов.|  
  
## <a name="other-imports"></a>Другие операции импорта  
 Фабрики поставщиков и брокеры чаще всего это сущности, которые может иметь несколько экземпляров в нескольких компонентов.  
  
|Импорт|Предоставляет|  
|------------|--------------|  
|<xref:Microsoft.VisualStudio.Text.Adornments.IErrorProviderFactory>|<xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> Типа <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>) для данного буфера.|  
|<xref:Microsoft.VisualStudio.Text.Adornments.ITextMarkerProviderFactory>|Средство создания тегов для текстового маркера ( <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> типа <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>).|  
|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProviderFactory>|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProvider> Для заданного <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>|Объект <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>|Объект <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSession>.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>|Объект <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSession>.|  
  
## <a name="see-also"></a>См. также  
 [Языковая служба и точки расширения редактора](../extensibility/language-service-and-editor-extension-points.md)
