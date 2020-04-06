---
title: 'Пошаговое: Выделение текста Документы Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - highlight text
ms.assetid: 64b772ad-4392-42e9-a237-5137f0384bf0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c35b1a032993a6c183191aafff77d8adeba4a3ef
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697402"
---
# <a name="walkthrough-highlight-text"></a>Пошаговое прохождение: Выделите текст
Вы можете добавить различные визуальные эффекты в редактор, создав компоненты управляемой расширительности (MEF). В этом пошаговом слове показано, как выделить каждое появление текущего слова в текстовом файле. Если слово происходит более одного раза в текстовом файле, и вы позиционируете карету в одном случае, каждое возникновение выделяется.

## <a name="prerequisites"></a>Предварительные требования
 Начиная с Visual Studio 2015, вы не устанавливаете Visual Studio SDK из центра загрузки. Он включен в качестве дополнительной функции в Visual Studio установки. Вы также можете установить VS SDK позже. Для получения дополнительной информации, [см.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-mef-project"></a>Создание проекта MEF

1. Создайте проект СЗ VSIX. (В **диалоге нового проекта** выберите **Visual C / Расширяемость,** затем **VSIX Project**.) Назовите решение. `HighlightWordTest`

2. Добавьте шаблон элемента классификатора редактора в проект. Для получения дополнительной информации [см. Создать расширение с шаблоном элемента редактора](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Удалите файлы существующих классов.

## <a name="define-a-textmarkertag"></a>Определите TextMarkerTag
 Первым шагом в выделении текста <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> является подкласс и определение его внешнего вида.

### <a name="to-define-a-textmarkertag-and-a-markerformatdefinition"></a>Определить TextMarkerTag и MarkerFormatDefinition

1. Добавьте файл класса и назовите его **HighlightWordTag.**

2. Добавьте следующие ссылки.

    1. Microsoft.VisualStudio.CoreUtility

    2. Microsoft.VisualStudio.Text.Data

    3. Microsoft.VisualStudio.Text.Logic

    4. Microsoft.VisualStudio.Text.UI

    5. Microsoft.VisualStudio.Text.UI.Wpf

    6. System.ComponentModel.Composition

    7. Презентация.Ядро

    8. Презентация.Рамочная

3. Импортируйте следующие пространства имен.

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

4. Создайте класс, который <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> наследует `HighlightWordTag`и называет его.

    ```csharp
    internal class HighlightWordTag : TextMarkerTag
    {

    }
    ```

5. Создайте второй класс, <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>который наследует `HighlightWordFormatDefinition`от, и назовите его. Для того, чтобы использовать это определение формата для тега, вы должны экспортировать его со следующими атрибутами:

    - <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: теги используют это для ссылки на этот формат

    - <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: это приводит к тому, что формат появляется в uI

    ```csharp

    [Export(typeof(EditorFormatDefinition))]
    [Name("MarkerFormatDefinition/HighlightWordFormatDefinition")]
    [UserVisible(true)]
    internal class HighlightWordFormatDefinition : MarkerFormatDefinition
    {

    }
    ```

6. В конструкторе для HighlightWordFormatDefinition определите его название и внешний вид. Свойство фона определяет цвет заполнения, в то время как свойство переднего плана определяет цвет границы.

    ```csharp
    public HighlightWordFormatDefinition()
    {
                this.BackgroundColor = Colors.LightBlue;
        this.ForegroundColor = Colors.DarkBlue;
        this.DisplayName = "Highlight Word";
        this.ZOrder = 5;
    }
    ```

7. В конструкторе для HighlightWordTag, перейдите в названии формата определения вы создали.

    ```
    public HighlightWordTag() : base("MarkerFormatDefinition/HighlightWordFormatDefinition") { }
    ```

## <a name="implement-an-itagger"></a>Реализация ITagger
 Следующим шагом является реализация <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> интерфейса. Этот интерфейс присваивает данному буферу текста теги, которые обеспечивают выделение текста и другие визуальные эффекты.

### <a name="to-implement-a-tagger"></a>Для реализации тегера

1. Создайте класс, <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> который `HighlightWordTag`реализует тип, `HighlightWordTagger`и назовите его.

    ```csharp
    internal class HighlightWordTagger : ITagger<HighlightWordTag>
    {

    }
    ```

2. Добавьте в класс следующие частные поля и свойства:

    - An <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, который соответствует текущему текстовому представлению.

    - An <xref:Microsoft.VisualStudio.Text.ITextBuffer>, который соответствует буферу текста, лежащему в основе представления текста.

    - An <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>, который используется для поиска текста.

    - An <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>, который имеет методы для навигации в пределах текстовых пролетов.

    - A <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection>, который содержит набор слов, чтобы выделить.

    - A <xref:Microsoft.VisualStudio.Text.SnapshotSpan>, что соответствует текущему слову.

    - A <xref:Microsoft.VisualStudio.Text.SnapshotPoint>, что соответствует текущему положению кареты.

    - Объект блокировки.

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

3. Добавьте конструктор, который инициализирует <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> свойства, перечисленные ранее, и добавляет обработчики событий. <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged>

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

4. Обработчики событий `UpdateAtCaretPosition` вызывают метод.

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

5. Необходимо также добавить `TagsChanged` событие, которое называется методом обновления.

     [!code-csharp[VSSDKHighlightWordTest#10](../extensibility/codesnippet/CSharp/walkthrough-highlighting-text_1.cs)]
     [!code-vb[VSSDKHighlightWordTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-highlighting-text_1.vb)]

6. Метод `UpdateAtCaretPosition()` находит каждое слово в буфере текста, идентичное слову, где <xref:Microsoft.VisualStudio.Text.SnapshotSpan> расположен курсор, и строит список объектов, которые соответствуют возникновениям слова. Затем он `SynchronousUpdate`вызывает, `TagsChanged` который поднимает событие.

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

7. Выполняет `SynchronousUpdate` синхронное обновление `WordSpans` и `CurrentWord` свойства, и `TagsChanged` поднимает событие.

    ```csharp
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

8. Метод необходимо <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> реализовать. Этот метод принимает <xref:Microsoft.VisualStudio.Text.SnapshotSpan> набор объектов и возвращает перечисление диапазонов тегов.

     В C, реализовать этот метод в качестве итератора выхода, который позволяет ленивый оценки (т.е. оценка набора только при доступе отдельных элементов) тегов. В Visual Basic добавьте теги в список и верните список.

     Здесь метод возвращает <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> объект с "синим", <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>который обеспечивает синий фон.

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

## <a name="create-a-tagger-provider"></a>Создание поставщика Tagger
 Чтобы создать теггер, необходимо <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>реализовать. Этот класс является компонентной частью MEF, поэтому необходимо установить правильные атрибуты, чтобы это расширение было распознано.

> [!NOTE]
> Для получения дополнительной информации о MEF [см.](/dotnet/framework/mef/index)

### <a name="to-create-a-tagger-provider"></a>Создание поставщика tagger

1. Создайте класс, `HighlightWordTaggerProvider` названный, который <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>реализует, и экспортировать его с <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "текст" и <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> . <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>

    ```csharp
    [Export(typeof(IViewTaggerProvider))]
    [ContentType("text")]
    [TagType(typeof(TextMarkerTag))]
    internal class HighlightWordTaggerProvider : IViewTaggerProvider
    { }
    ```

2. Вы должны импортировать два <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService> редактора услуг, и <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, чтобы мгновенно теггер.

    ```csharp
    [Import]
    internal ITextSearchService TextSearchService { get; set; }

    [Import]
    internal ITextStructureNavigatorSelectorService TextStructureNavigatorSelector { get; set; }

    ```

3. Реализация <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> метода возврата экземпляра `HighlightWordTagger`.

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

## <a name="build-and-test-the-code"></a>Создание и тестирование кода
 Чтобы протестировать этот код, создайте решение HighlightWordTest и запустите его в экспериментальном экземпляре.

### <a name="to-build-and-test-the-highlightwordtest-solution"></a>Создание и тестирование решения HighlightWordTest

1. Создайте решение.

2. При запуске этого проекта в отладчике запускается второй экземпляр Visual Studio.

3. Создайте текстовый файл и введите текст, в котором повторяются слова, например, "привет привет".

4. Расположите курсор в одном из случаев "привет". Каждое явление должно быть выделено синим цветом.

## <a name="see-also"></a>См. также
- [Прохождение: Свяжите тип содержимого с расширением имени файла](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
