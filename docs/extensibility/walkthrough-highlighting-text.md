---
title: 'Пошаговое руководство: Выделение текста | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - highlight text
ms.assetid: 64b772ad-4392-42e9-a237-5137f0384bf0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 90bf22bfe65b1120f5cc149d95eea25357b8ffa4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-highlighting-text"></a>Пошаговое руководство: Выделение текста
Можно добавить различные визуальные эффекты в редактор, создавая компоненты Managed Extensibility Framework (MEF). В этом пошаговом руководстве показано, как выделить все вхождения текущего слова в текстовом файле. Если слово более одного раза в текстовый файл и поместите курсор в одно вхождение, каждое вхождение будет выделен.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, не установить пакет SDK для Visual Studio из центра загрузки Майкрософт. Он включен в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Создание проекта MEF  
  
1.  Создайте проект VSIX C#. (В **новый проект** диалогового окна выберите **Visual C# / Extensibility**, затем **проект VSIX**.) Присвойте решению имя `HighlightWordTest`.  
  
2.  Добавьте в проект шаблон элемента классификатора редактора. Дополнительные сведения см. в разделе [создания расширения с помощью шаблона элемента редактор](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Удалите файлы существующих классов.  
  
## <a name="defining-a-textmarkertag"></a>Определение TextMarkerTag  
 Первым шагом в выделение текста является подклассом <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> и определяют его внешний вид.  
  
#### <a name="to-define-a-textmarkertag-and-a-markerformatdefinition"></a>Для определения TextMarkerTag и MarkerFormatDefinition  
  
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
  
    ```csharp  
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
  
4.  Создайте класс, наследующий от <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> и назовите его `HighlightWordTag`.  
  
    ```csharp  
    internal class HighlightWordTag : TextMarkerTag  
    {  
  
    }  
    ```  
  
5.  Создайте второй класс, наследующий от <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>и назовите его HighlightWordFormatDefinition. Чтобы использовать это определение формата для вашего тега, его необходимо экспортировать со следующими атрибутами:  
  
    -   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: теги позволяет ссылаться на этот формат  
  
    -   <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: в результате форматирования для отображения в пользовательском Интерфейсе  
  
    ```csharp  
  
    [Export(typeof(EditorFormatDefinition))]  
    [Name("MarkerFormatDefinition/HighlightWordFormatDefinition")]  
    [UserVisible(true)]  
    internal class HighlightWordFormatDefinition : MarkerFormatDefinition  
    {  
  
    }  
    ```  
  
6.  В конструкторе HighlightWordFormatDefinition определите его отображаемое имя и внешний вид. Свойство фона определяет цвет заливки, пока свойство основного определяет цвет границы.  
  
    ```csharp  
    public HighlightWordFormatDefinition()  
    {  
                this.BackgroundColor = Colors.LightBlue;  
        this.ForegroundColor = Colors.DarkBlue;  
        this.DisplayName = "Highlight Word";  
        this.ZOrder = 5;  
    }  
    ```  
  
7.  В конструкторе HighlightWordTag передайте имя определение формата, которую вы только что создали.  
  
    ```  
    public HighlightWordTag() : base("MarkerFormatDefinition/HighlightWordFormatDefinition") { }  
    ```  
  
## <a name="implementing-an-itagger"></a>Реализация ITagger  
 Следующим шагом является реализация <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> интерфейса. Этот интерфейс назначает для данного текстового буфера, теги, предоставляющие выделение текста и других эффектов.  
  
#### <a name="to-implement-a-tagger"></a>Реализация разметчика  
  
1.  Создайте класс, реализующий <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> типа `HighlightWordTag`и назовите его `HighlightWordTagger`.  
  
    ```csharp  
    internal class HighlightWordTagger : ITagger<HighlightWordTag>  
    {  
  
    }  
    ```  
  
2.  Добавьте в класс ниже закрытые поля и свойства:  
  
    -   <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, Который соответствует текущее представление текста.  
  
    -   <xref:Microsoft.VisualStudio.Text.ITextBuffer>, Которой соответствует буфер текста, лежащей в основе представления текста.  
  
    -   <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>, Который используется для поиска текста.  
  
    -   <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>, Который содержит методы для перемещения в пределах фрагментов текста.  
  
    -   Объект <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection>, который содержит набор слов для выделения.  
  
    -   Объект <xref:Microsoft.VisualStudio.Text.SnapshotSpan>, который соответствует текущего слова.  
  
    -   Объект <xref:Microsoft.VisualStudio.Text.SnapshotPoint>, который соответствует текущей позиции курсора.  
  
    -   Объект блокировки.  
  
    ```csharp  
    ITextView View { get; set; }  
    ITextBuffer SourceBuffer { get; set; }  
    ITextSearchService TextSearchService { get; set; }  
    ITextStructureNavigator TextStructureNavigator { get; set; }  
    NormalizedSnapshotSpanCollection WordSpans { get; set; }  
    SnapshotSpan? CurrentWord { get; set; }  
    SnapshotPoint RequestedPoint { get; set; }  
    object updateLock = new object();  
  
    ```  
  
3.  Добавьте конструктор, который инициализирует свойства, перечисленные выше и добавляет <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> и <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> обработчики событий.  
  
    ```csharp  
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
  
4.  Обработчики событий, как вызвать `UpdateAtCaretPosition` метод.  
  
    ```csharp  
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
  
5.  Необходимо также добавить `TagsChanged` событие, которое будет вызываться с помощью метода update.  
  
     [!code-csharp[VSSDKHighlightWordTest#10](../extensibility/codesnippet/CSharp/walkthrough-highlighting-text_1.cs)]
     [!code-vb[VSSDKHighlightWordTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-highlighting-text_1.vb)]  
  
6.  `UpdateAtCaretPosition()` Метод находит все слова в буфере, идентичный word, где находится курсор и создает список <xref:Microsoft.VisualStudio.Text.SnapshotSpan> объекты, которые соответствуют вхождения слова. Затем он вызывает `SynchronousUpdate`, что вызывает `TagsChanged` событий.  
  
    ```csharp  
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
  
7.  `SynchronousUpdate` Выполняет синхронного обновления `WordSpans` и `CurrentWord` свойства и вызывает `TagsChanged` событий.  
  
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
  
8.  Необходимо реализовать <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> метод. Этот метод принимает коллекцию <xref:Microsoft.VisualStudio.Text.SnapshotSpan> объекты и возвращает перечисление диапазонов тегов.  
  
     В C# следует Реализуйте этот метод в качестве yield итератора, который позволяет отложенное вычисление (то есть оценки набора данных только в том случае, когда происходит доступ к отдельным элементам) тегов. В Visual Basic добавьте в список и возвращают список.  
  
     Здесь метод возвращает <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> объекта, имеющего «blue» <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>, который предоставляет синим фоном.  
  
    ```csharp  
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
  
## <a name="creating-a-tagger-provider"></a>Создание поставщика разметчика  
 Чтобы создать ваш создания тегов, необходимо реализовать <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>. Этот класс является частью компонента MEF, необходимо задать правильные атрибуты, чтобы этот модуль был распознан.  
  
> [!NOTE]
>  Дополнительные сведения о MEF см. в разделе [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).  
  
#### <a name="to-create-a-tagger-provider"></a>Для создания поставщика разметчика  
  
1.  Создайте класс с именем `HighlightWordTaggerProvider` , реализующий <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>и экспортировать его с <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> «текст» и <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> из <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.  
  
    ```csharp  
    [Export(typeof(IViewTaggerProvider))]  
    [ContentType("text")]  
    [TagType(typeof(TextMarkerTag))]  
    internal class HighlightWordTaggerProvider : IViewTaggerProvider  
    { }  
    ```  
  
2.  Две службы редактора, необходимо импортировать <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService> и <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, для создания разметчика.  
  
    ```csharp  
    [Import]  
    internal ITextSearchService TextSearchService { get; set; }  
  
    [Import]  
    internal ITextStructureNavigatorSelectorService TextStructureNavigatorSelector { get; set; }  
  
    ```  
  
3.  Реализуйте <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> метод для возврата экземпляра `HighlightWordTagger`.  
  
    ```csharp  
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
 Чтобы проверить код, выполните сборку решения HighlightWordTest и запустите его в экспериментальном экземпляре.  
  
#### <a name="to-build-and-test-the-highlightwordtest-solution"></a>Для построения и тестирования решения HighlightWordTest  
  
1.  Постройте решение.  
  
2.  При запуске этого проекта в отладчике создается второй экземпляр Visual Studio.  
  
3.  Создайте текстовый файл и введите текст с рядом повторяющихся слов, например, «hello hello hello».  
  
4.  Поместите курсор в одно из вхождений «hello». Каждое вхождение должны быть выделены синим цветом.  
  
## <a name="see-also"></a>См. также  
 [Пошаговое руководство. Связывание типа контента с расширением имени файла](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)