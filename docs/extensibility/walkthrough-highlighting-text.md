---
title: Пошаговое руководство. Выделение текста | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - highlight text
ms.assetid: 64b772ad-4392-42e9-a237-5137f0384bf0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9051db64beb1499486f6413cb6e2aac6b0b64241
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56722256"
---
# <a name="walkthrough-highlight-text"></a>Пошаговое руководство. Выделение цветом текста
Можно добавить различные визуальные эффекты к редактору, создав составные части Managed Extensibility Framework (MEF). В этом пошаговом руководстве показано, как можно выделить каждое вхождение текущего слова в текстовом файле. Если когда встречается более одного раза в текстовый файл и поместите курсор в одно вхождение, каждое вхождение будет выделен.

## <a name="prerequisites"></a>Предварительные требования
 Начиная с Visual Studio 2015, не устанавливайте Visual Studio SDK в центре загрузки. Этот пакет включен в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [установить пакет SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Создание проекта MEF

1.  Создайте проект VSIX C#. (В **новый проект** диалоговом окне выберите **Visual C# / Extensibility**, затем **проект VSIX**.) Назовите решение `HighlightWordTest`.

2.  Добавьте в проект шаблон элемента классификатора редактора. Дополнительные сведения см. в разделе [создание расширения с помощью шаблона элемента редактора](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3.  Удалите файлы существующих классов.

## <a name="define-a-textmarkertag"></a>Определение TextMarkerTag
 Первым шагом в выделение текста — в подкласс <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> и определения его внешнего вида.

### <a name="to-define-a-textmarkertag-and-a-markerformatdefinition"></a>Для определения TextMarkerTag и MarkerFormatDefinition

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

4.  Создайте класс, наследуемый от <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> и назовите его `HighlightWordTag`.

    ```csharp
    internal class HighlightWordTag : TextMarkerTag
    {

    }
    ```

5.  Создайте второй класс, наследуемый от <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>и назовите его `HighlightWordFormatDefinition`. Чтобы использовать это определение формата для тега, его необходимо экспортировать со следующими атрибутами:

    -   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: тегов позволяет ссылаться на этот формат

    -   <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: это приводит к формат для отображения в пользовательском Интерфейсе

    ```csharp

    [Export(typeof(EditorFormatDefinition))]
    [Name("MarkerFormatDefinition/HighlightWordFormatDefinition")]
    [UserVisible(true)]
    internal class HighlightWordFormatDefinition : MarkerFormatDefinition
    {

    }
    ```

6.  В конструкторе для HighlightWordFormatDefinition определите его отображаемое имя и внешний вид. Свойство Background определяет цвет заливки, а свойства Foreground определяет цвет границы.

    ```csharp
    public HighlightWordFormatDefinition()
    {
                this.BackgroundColor = Colors.LightBlue;
        this.ForegroundColor = Colors.DarkBlue;
        this.DisplayName = "Highlight Word";
        this.ZOrder = 5;
    }
    ```

7.  В конструкторе для HighlightWordTag передаете имя в определении формата, который вы создали.

    ```
    public HighlightWordTag() : base("MarkerFormatDefinition/HighlightWordFormatDefinition") { }
    ```

## <a name="implement-an-itagger"></a>Реализуйте ITagger
 Следующим шагом является реализация <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> интерфейс. Назначает этот интерфейс для данного текстового буфера, теги, предоставляющие выделение текста и других визуальных эффектов.

### <a name="to-implement-a-tagger"></a>Реализация разметчика

1.  Создайте класс, реализующий <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> типа `HighlightWordTag`и назовите его `HighlightWordTagger`.

    ```csharp
    internal class HighlightWordTagger : ITagger<HighlightWordTag>
    {

    }
    ```

2.  Добавьте в класс ниже закрытые поля и свойства:

    -   <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, Который соответствует текущего текстового представления.

    -   <xref:Microsoft.VisualStudio.Text.ITextBuffer>, Соответствующее в текстовый буфер, который является базовым представлением текста.

    -   <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>, Который используется для поиска текста.

    -   <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>, Который содержит методы для навигации в текстовых диапазонов.

    -   Объект <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection>, который содержит набор слов, чтобы выделить.

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
    object updateLock = new object();

    ```

3.  Добавьте конструктор, который инициализирует свойства, перечисленные ранее и добавляет <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> и <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> обработчики событий.

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

4.  Обработчики событий, обе точки вызова `UpdateAtCaretPosition` метод.

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

5.  Необходимо также добавить `TagsChanged` событие, которое вызывается методом update.

     [!code-csharp[VSSDKHighlightWordTest#10](../extensibility/codesnippet/CSharp/walkthrough-highlighting-text_1.cs)]
     [!code-vb[VSSDKHighlightWordTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-highlighting-text_1.vb)]

6.  `UpdateAtCaretPosition()` Метод находит все слова в текстовом буфере, идентичный word, где находится курсор и создает список <xref:Microsoft.VisualStudio.Text.SnapshotSpan> объектов, которые соответствуют вхождения слова. Затем он вызывает `SynchronousUpdate`, который вызывает `TagsChanged` событий.

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
        //If we've selected something not worth highlighting, we might have missed a "word" by a little bit
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
    static bool WordExtentIsValid(SnapshotPoint currentRequest, TextExtent word)
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

8.  Необходимо реализовать <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> метод. Этот метод принимает коллекцию <xref:Microsoft.VisualStudio.Text.SnapshotSpan> объектов и возвращает перечисление диапазонов с тегами.

     В C# этот метод реализуется итератором yield, позволяющий отложенное вычисление (то есть оценки набора только в том случае, когда происходит доступ к отдельным элементам) тегов. В Visual Basic добавление тегов в список и возвращения списка.

     Здесь метод возвращает <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> объект, имеющий «blue» <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>, который предоставляет синим фоном.

    ```csharp
    public IEnumerable<ITagSpan<HighlightWordTag>> GetTags(NormalizedSnapshotSpanCollection spans)
    {
        if (CurrentWord == null)
            yield break;

        // Hold on to a "snapshot" of the word spans and current word, so that we maintain the same
        // collection throughout
        SnapshotSpan currentWord = CurrentWord.Value;
        NormalizedSnapshotSpanCollection wordSpans = WordSpans;

        if (spans.Count == 0 || wordSpans.Count == 0)
            yield break;

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
            yield return new TagSpan<HighlightWordTag>(currentWord, new HighlightWordTag());

        // Second, yield all the other words in the file 
        foreach (SnapshotSpan span in NormalizedSnapshotSpanCollection.Overlap(spans, wordSpans))
        {
            yield return new TagSpan<HighlightWordTag>(span, new HighlightWordTag());
        }
    }
    ```

## <a name="create-a-tagger-provider"></a>Создание поставщика средство создания тегов
 Чтобы создать ваш средство создания тегов, необходимо реализовать <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>. Этот класс является частью компонента MEF, поэтому вам нужно задать правильные атрибуты, чтобы этот модуль был распознан.

> [!NOTE]
>  Дополнительные сведения о MEF см. в разделе [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

### <a name="to-create-a-tagger-provider"></a>Для создания поставщика средство создания тегов

1.  Создайте класс с именем `HighlightWordTaggerProvider` , реализующий <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>и экспортировать его с <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> «текст» и <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> из <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.

    ```csharp
    [Export(typeof(IViewTaggerProvider))]
    [ContentType("text")]
    [TagType(typeof(TextMarkerTag))]
    internal class HighlightWordTaggerProvider : IViewTaggerProvider
    { }
    ```

2.  Две службы редактора, необходимо импортировать <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService> и <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, для создания экземпляра средство создания тегов.

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
            return null;

        ITextStructureNavigator textStructureNavigator =
            TextStructureNavigatorSelector.GetTextStructureNavigator(buffer);

        return new HighlightWordTagger(textView, buffer, TextSearchService, textStructureNavigator) as ITagger<T>;
    }
    ```

## <a name="build-and-test-the-code"></a>Построение и тестирование кода
 Чтобы протестировать этот код, выполните сборку решения HighlightWordTest и запустите его в экспериментальном экземпляре.

### <a name="to-build-and-test-the-highlightwordtest-solution"></a>Построение и тестирование решения HighlightWordTest

1.  Постройте решение.

2.  При запуске этого проекта в отладчике, запускается второй экземпляр Visual Studio.

3.  Создайте текстовый файл и введите текст, в котором слова повторяются, например, «hello hello hello».

4.  Позиционирование курсора в одно из вхождений «hello». Каждое вхождение должны быть выделены синим цветом.

## <a name="see-also"></a>См. также
- [Пошаговое руководство: Связывание типа контента с расширением имени файла](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)