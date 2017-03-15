---
title: "Пошаговое руководство: Выделение текста | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - highlight text
ms.assetid: 64b772ad-4392-42e9-a237-5137f0384bf0
caps.latest.revision: 42
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 029cc7785c49a08c7128bfaaff8f236e438efad8
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-highlighting-text"></a>Пошаговое руководство: Выделение текста
Путем создания компонентов Managed Extensibility Framework (MEF), можно добавить различные визуальные эффекты в редактор. В этом пошаговом руководстве показано, как выделить все вхождения текущего слова в текстовом файле. Если слово встречается более одного раза в текстовый файл и поместите курсор в одно вхождение, каждое вхождение будет выделен.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, не установить пакет SDK для Visual Studio из центра загрузки. Она будет включена в качестве дополнительного компонента в установку Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [установка Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Создание проекта MEF  
  
1.  Создайте проект VSIX C#. (В **новый проект** диалогового окна выберите **Visual C# и расширяемость**, затем **проект VSIX**.) Присвойте решению имя `HighlightWordTest`.  
  
2.  Добавьте в проект шаблон элемента редактор классификатора. Дополнительные сведения см. в разделе [создания расширения с помощью редактора шаблона элемента](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Удалите файлы существующих классов.  
  
## <a name="defining-a-textmarkertag"></a>Определение TextMarkerTag  
 Первым шагом в выделение текста является подкласс <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>и определить его внешний вид.</xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>  
  
#### <a name="to-define-a-textmarkertag-and-a-markerformatdefinition"></a>Чтобы определить TextMarkerTag и MarkerFormatDefinition  
  
1.  Добавьте файл класса и назовите его **HighlightWordTag**.  
  
2.  Добавьте следующие ссылки:  
  
    1.  Microsoft.VisualStudio.CoreUtility  
  
    2.  Microsoft.VisualStudio.Text.Data  
  
    3.  Microsoft.VisualStudio.Text.Logic  
  
    4.  Microsoft.VisualStudio.Text.UI  
  
    5.  Microsoft.VisualStudio.Text.UI.Wpf  
  
    6.  System.ComponentModel.Composition  
  
    7.  Presentation.Core  
  
    8.  Presentation.Framework  
  
3.  Импортируйте следующие пространства имен.  
  
    ```c#  
    using System;  
    using System.Collections.Generic;  
    using System.ComponentModel.Composition;  
    using System.Linq;  
    using System.Threading;  
    using Microsoft.VisualStudio.Text;  
    using Microsoft.VisualStudio.Text.Classification;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Text.Operations;  
    using Microsoft.VisualStudio.Text.Tagging;  
    using Microsoft.VisualStudio.Utilities;  
    using System.Windows.Media;  
    ```  
  
4.  Создайте класс, наследуемый от <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>и назовите его `HighlightWordTag`.</xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>  
  
    ```c#  
    internal class HighlightWordTag : TextMarkerTag  
    {  
  
    }  
    ```  
  
5.  Создайте второй класс, наследуемый от <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>и назовите его HighlightWordFormatDefinition.</xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> Для использования данного определения формата для тег, его необходимо экспортировать со следующими атрибутами:  
  
    -   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: теги позволяет ссылаться на этот формат</xref:Microsoft.VisualStudio.Utilities.NameAttribute>  
  
    -   <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: в результате форматирования для отображения в пользовательском Интерфейсе</xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>  
  
    ```c#  
  
    [Export(typeof(EditorFormatDefinition))]  
    [Name("MarkerFormatDefinition/HighlightWordFormatDefinition")]  
    [UserVisible(true)]  
    internal class HighlightWordFormatDefinition : MarkerFormatDefinition  
    {  
  
    }  
    ```  
  
6.  В конструкторе HighlightWordFormatDefinition определите его отображаемое имя и внешний вид. Свойство фона определяет цвет заливки, а свойства Foreground определяет цвет границы.  
  
    ```c#  
    public HighlightWordFormatDefinition()  
    {  
                this.BackgroundColor = Colors.LightBlue;  
        this.ForegroundColor = Colors.DarkBlue;  
        this.DisplayName = "Highlight Word";  
        this.ZOrder = 5;  
    }  
    ```  
  
7.  В конструкторе HighlightWordTag передайте имя определения формата, которое вы только что создали.  
  
    ```  
    public HighlightWordTag() : base("MarkerFormatDefinition/HighlightWordFormatDefinition") { }  
    ```  
  
## <a name="implementing-an-itagger"></a>Реализация ITagger  
 Следующим шагом является реализация <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>интерфейса.</xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> Назначает этот интерфейс для данного текстового буфера, теги, предоставляющие выделение текста и других визуальных эффектов.  
  
#### <a name="to-implement-a-tagger"></a>Для реализации средство создания тегов  
  
1.  Создайте класс, реализующий <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>типа `HighlightWordTag`и назовите его `HighlightWordTagger`.</xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>  
  
    ```c#  
    internal class HighlightWordTagger : ITagger<HighlightWordTag>  
    {  
  
    }  
    ```  
  
2.  Добавьте следующие частные поля и свойства класса:  
  
    -   <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, Которой соответствует текущее представление текста.</xref:Microsoft.VisualStudio.Text.Editor.ITextView>  
  
    -   <xref:Microsoft.VisualStudio.Text.ITextBuffer>, Которой соответствует текстовый буфер, который лежит в основе текстового представления.</xref:Microsoft.VisualStudio.Text.ITextBuffer>  
  
    -   <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>, Который используется для поиска текста.</xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>  
  
    -   <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>, Который имеет методы для перемещения в пределах текстового диапазона.</xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>  
  
    -   Объект <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection>, который содержит набор слов, чтобы выделить.</xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection>  
  
    -   Объект <xref:Microsoft.VisualStudio.Text.SnapshotSpan>, который соответствует текущее слово.</xref:Microsoft.VisualStudio.Text.SnapshotSpan>  
  
    -   Объект <xref:Microsoft.VisualStudio.Text.SnapshotPoint>, который соответствует текущей позиции курсора.</xref:Microsoft.VisualStudio.Text.SnapshotPoint>  
  
    -   Объект блокировки.  
  
    ```c#  
    ITextView View { get; set; }  
    ITextBuffer SourceBuffer { get; set; }  
    ITextSearchService TextSearchService { get; set; }  
    ITextStructureNavigator TextStructureNavigator { get; set; }  
    NormalizedSnapshotSpanCollection WordSpans { get; set; }  
    SnapshotSpan? CurrentWord { get; set; }  
    SnapshotPoint RequestedPoint { get; set; }  
    object updateLock = new object();  
  
    ```  
  
3.  Добавьте конструктор, который инициализирует свойства, перечисленные выше и добавляет <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>и <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged>обработчики событий.</xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> </xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>  
  
    ```c#  
    public HighlightWordTagger(ITextView view, ITextBuffer sourceBuffer, ITextSearchService textSearchService,  
    ITextStructureNavigator textStructureNavigator)  
    {  
        this.View = view;  
        this.SourceBuffer = sourceBuffer;  
        this.TextSearchService = textSearchService;  
        this.TextStructureNavigator = textStructureNavigator;  
        this.WordSpans = new NormalizedSnapshotSpanCollection();  
        this.CurrentWord = null;  
        this.View.Caret.PositionChanged += CaretPositionChanged;  
        this.View.LayoutChanged += ViewLayoutChanged;  
    }  
  
    ```  
  
4.  Обработчики событий, оба вызова `UpdateAtCaretPosition` метод.  
  
    ```c#  
    void ViewLayoutChanged(object sender, TextViewLayoutChangedEventArgs e)  
    {  
        // If a new snapshot wasn't generated, then skip this layout   
        if (e.NewSnapshot != e.OldSnapshot)  
        {  
            UpdateAtCaretPosition(View.Caret.Position);  
        }  
    }  
  
    void CaretPositionChanged(object sender, CaretPositionChangedEventArgs e)  
    {  
        UpdateAtCaretPosition(e.NewPosition);  
    }  
    ```  
  
5.  Необходимо также добавить `TagsChanged` события, который будет вызываться при помощи метода update.  
  
     [!code-cs[#10 VSSDKHighlightWordTest](../extensibility/codesnippet/CSharp/walkthrough-highlighting-text_1.cs) ] 
     [!code-vb [VSSDKHighlightWordTest&#10;](../extensibility/codesnippet/VisualBasic/walkthrough-highlighting-text_1.vb)]  
  
6.  `UpdateAtCaretPosition()` Метод находит все слова в текстовом буфере, идентичный word, где находится курсор и создает список <xref:Microsoft.VisualStudio.Text.SnapshotSpan>объекты, соответствующие вхождения слова.</xref:Microsoft.VisualStudio.Text.SnapshotSpan> Затем он вызывает `SynchronousUpdate`, что вызывает `TagsChanged` события.  
  
    ```c#  
    void UpdateAtCaretPosition(CaretPosition caretPosition)  
    {  
        SnapshotPoint? point = caretPosition.Point.GetPoint(SourceBuffer, caretPosition.Affinity);  
  
        if (!point.HasValue)  
            return;  
  
        // If the new caret position is still within the current word (and on the same snapshot), we don't need to check it   
        if (CurrentWord.HasValue  
            && CurrentWord.Value.Snapshot == View.TextSnapshot  
            && point.Value >= CurrentWord.Value.Start  
            && point.Value <= CurrentWord.Value.End)  
        {  
            return;  
        }  
  
        RequestedPoint = point.Value;  
        UpdateWordAdornments();  
    }  
  
    void UpdateWordAdornments()  
    {  
        SnapshotPoint currentRequest = RequestedPoint;  
        List<SnapshotSpan> wordSpans = new List<SnapshotSpan>();  
        //Find all words in the buffer like the one the caret is on  
        TextExtent word = TextStructureNavigator.GetExtentOfWord(currentRequest);  
        bool foundWord = true;  
        //If we've selected something not worth highlighting, we might have missed a "word" by a little bit  
        if (!WordExtentIsValid(currentRequest, word))  
        {  
            //Before we retry, make sure it is worthwhile   
            if (word.Span.Start != currentRequest  
                 || currentRequest == currentRequest.GetContainingLine().Start  
                 || char.IsWhiteSpace((currentRequest - 1).GetChar()))  
            {  
                foundWord = false;  
            }  
            else  
            {  
                // Try again, one character previous.    
                //If the caret is at the end of a word, pick up the word.  
                word = TextStructureNavigator.GetExtentOfWord(currentRequest - 1);  
  
                //If the word still isn't valid, we're done   
                if (!WordExtentIsValid(currentRequest, word))  
                    foundWord = false;  
            }  
        }  
  
        if (!foundWord)  
        {  
            //If we couldn't find a word, clear out the existing markers  
            SynchronousUpdate(currentRequest, new NormalizedSnapshotSpanCollection(), null);  
            return;  
        }  
  
        SnapshotSpan currentWord = word.Span;  
        //If this is the current word, and the caret moved within a word, we're done.   
        if (CurrentWord.HasValue && currentWord == CurrentWord)  
            return;  
  
        //Find the new spans  
        FindData findData = new FindData(currentWord.GetText(), currentWord.Snapshot);  
        findData.FindOptions = FindOptions.WholeWord | FindOptions.MatchCase;  
  
        wordSpans.AddRange(TextSearchService.FindAll(findData));  
  
        //If another change hasn't happened, do a real update   
        if (currentRequest == RequestedPoint)  
            SynchronousUpdate(currentRequest, new NormalizedSnapshotSpanCollection(wordSpans), currentWord);  
    }  
    static bool WordExtentIsValid(SnapshotPoint currentRequest, TextExtent word)  
    {  
        return word.IsSignificant  
            && currentRequest.Snapshot.GetText(word.Span).Any(c => char.IsLetter(c));  
    }  
  
    ```  
  
7.  `SynchronousUpdate` Выполняет синхронного обновления `WordSpans` и `CurrentWord` свойства и вызывает `TagsChanged` события.  
  
    ```vb  
    void SynchronousUpdate(SnapshotPoint currentRequest, NormalizedSnapshotSpanCollection newSpans, SnapshotSpan? newCurrentWord)  
    {  
        lock (updateLock)  
        {  
            if (currentRequest != RequestedPoint)  
                return;  
  
            WordSpans = newSpans;  
            CurrentWord = newCurrentWord;  
  
            var tempEvent = TagsChanged;  
            if (tempEvent != null)  
                tempEvent(this, new SnapshotSpanEventArgs(new SnapshotSpan(SourceBuffer.CurrentSnapshot, 0, SourceBuffer.CurrentSnapshot.Length)));  
        }  
    }  
    ```  
  
8.  Необходимо реализовать <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A>метод.</xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> Этот метод принимает коллекцию <xref:Microsoft.VisualStudio.Text.SnapshotSpan>объекты и возвращает перечисление диапазонов тегов.</xref:Microsoft.VisualStudio.Text.SnapshotSpan>  
  
     В C# этот метод реализуется как итератор yield, позволяющий отложенные вычисления (то есть оценки набора только в том случае, если при обращении к отдельным элементам) тегов. В Visual Basic добавьте в список и возвращают список.  
  
     Здесь метод возвращает <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601>объекта, имеющего «blue» <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>, который предоставляет синим фоном.</xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> </xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601>  
  
    ```c#  
    public IEnumerable<ITagSpan<HighlightWordTag>> GetTags(NormalizedSnapshotSpanCollection spans)  
    {  
        if (CurrentWord == null)  
            yield break;  
  
        // Hold on to a "snapshot" of the word spans and current word, so that we maintain the same  
        // collection throughout  
        SnapshotSpan currentWord = CurrentWord.Value;  
        NormalizedSnapshotSpanCollection wordSpans = WordSpans;  
  
        if (spans.Count == 0 || wordSpans.Count == 0)  
            yield break;  
  
        // If the requested snapshot isn't the same as the one our words are on, translate our spans to the expected snapshot   
        if (spans[0].Snapshot != wordSpans[0].Snapshot)  
        {  
            wordSpans = new NormalizedSnapshotSpanCollection(  
                wordSpans.Select(span => span.TranslateTo(spans[0].Snapshot, SpanTrackingMode.EdgeExclusive)));  
  
            currentWord = currentWord.TranslateTo(spans[0].Snapshot, SpanTrackingMode.EdgeExclusive);  
        }  
  
        // First, yield back the word the cursor is under (if it overlaps)   
        // Note that we'll yield back the same word again in the wordspans collection;   
        // the duplication here is expected.   
        if (spans.OverlapsWith(new NormalizedSnapshotSpanCollection(currentWord)))  
            yield return new TagSpan<HighlightWordTag>(currentWord, new HighlightWordTag());  
  
        // Second, yield all the other words in the file   
        foreach (SnapshotSpan span in NormalizedSnapshotSpanCollection.Overlap(spans, wordSpans))  
        {  
            yield return new TagSpan<HighlightWordTag>(span, new HighlightWordTag());  
        }  
    }  
    ```  
  
## <a name="creating-a-tagger-provider"></a>Создание поставщика создания тегов  
 Для создания вашего создания тегов, необходимо реализовать <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>.</xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider> Этот класс является частью компонента MEF, поэтому необходимо задать правильные атрибуты, чтобы этот модуль был распознан.  
  
> [!NOTE]
>  Дополнительные сведения о MEF см. в разделе [Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/Library/6c61b4ec-c6df-4651-80f1-4854f8b14dde).  
  
#### <a name="to-create-a-tagger-provider"></a>Для создания поставщика создания тегов  
  
1.  Создайте класс с именем `HighlightWordTaggerProvider` , реализующий <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>и экспортировать его с <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>«text» и <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.</xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> </xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> </xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> </xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>  
  
    ```c#  
    [Export(typeof(IViewTaggerProvider))]  
    [ContentType("text")]  
    [TagType(typeof(TextMarkerTag))]  
    internal class HighlightWordTaggerProvider : IViewTaggerProvider  
    { }  
    ```  
  
2.  Необходимо импортировать две службы редактора <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>и <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, чтобы создать средство создания тегов.</xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> </xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>  
  
    ```c#  
    [Import]  
    internal ITextSearchService TextSearchService { get; set; }  
  
    [Import]  
    internal ITextStructureNavigatorSelectorService TextStructureNavigatorSelector { get; set; }  
  
    ```  
  
3.  Реализация <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A>метода, возвращающего экземпляр `HighlightWordTagger`.</xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A>  
  
    ```c#  
    public ITagger<T> CreateTagger<T>(ITextView textView, ITextBuffer buffer) where T : ITag  
    {  
        //provide highlighting only on the top buffer   
        if (textView.TextBuffer != buffer)  
            return null;  
  
        ITextStructureNavigator textStructureNavigator =  
            TextStructureNavigatorSelector.GetTextStructureNavigator(buffer);  
  
        return new HighlightWordTagger(textView, buffer, TextSearchService, textStructureNavigator) as ITagger<T>;  
    }  
    ```  
  
## <a name="building-and-testing-the-code"></a>Сборка и тестирование кода  
 Чтобы проверить код, создания HighlightWordTest решения и запустите его в экспериментальном экземпляре.  
  
#### <a name="to-build-and-test-the-highlightwordtest-solution"></a>Для построения и тестирования решений HighlightWordTest  
  
1.  Постройте решение.  
  
2.  При запуске этого проекта в отладчике создается второй экземпляр Visual Studio.  
  
3.  Создайте текстовый файл и введите текст, в котором слова повторяются, например, «hello hello hello».  
  
4.  Поместите курсор в одно из вхождений «hello». Каждое вхождение должны быть выделены синим цветом.  
  
## <a name="see-also"></a>См. также  
 [Пошаговое руководство: Связывание типа контента с расширением имени файла](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
