---
title: Пошаговое руководство. Использование командной оболочки в расширении редактора | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - add a menu command
ms.assetid: 08526848-a442-4cd4-afa1-b2eac2005adb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d0eade1bf17955bce52ea53b159f23102afb74b8
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444921"
---
# <a name="walkthrough-use-a-shell-command-with-an-editor-extension"></a>Пошаговое руководство. Используйте команду оболочки в расширении редактора
Из VSPackage можно добавить функции, такие как команды меню в редакторе. В этом пошаговом руководстве показано, как добавить элемент оформления для представления текста в редакторе путем вызова команды меню.

 В этом пошаговом руководстве демонстрируется использование VSPackage вместе с частью компонента Managed Extensibility Framework (MEF). Необходимо использовать VSPackage для регистрации команду меню в оболочке Visual Studio. И команду можно использовать для доступа к части компонента MEF.

## <a name="prerequisites"></a>Предварительные требования
 Начиная с Visual Studio 2015, не устанавливайте Visual Studio SDK в центре загрузки. Этот пакет включен в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [установить пакет SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-an-extension-with-a-menu-command"></a>Создание расширения с помощью команды меню
 Создать пакет VSPackage, который помещает команды меню с именем **добавьте оформления** на **средства** меню.

1. Создайте проект VSIX C# с именем `MenuCommandTest`и добавьте имя шаблона элемента настраиваемой команды **AddAdornment**. Дополнительные сведения см. в разделе [создание расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Открывает решение с именем MenuCommandTest. Файл MenuCommandTestPackage содержит код, который создает команду меню и помещает его в **средства** меню. На этом этапе команда приводит только к окно сообщения. Позднее будет показано, как изменить этот параметр для отображения оформления комментариев.

3. Откройте *source.extension.vsixmanifest* файл в редакторе манифестов VSIX. `Assets` Вкладке должна отображаться строка для Microsoft.VisualStudio.VsPackage именованные MenuCommandTest.

4. Сохраните и закройте *source.extension.vsixmanifest* файл.

## <a name="add-a-mef-extension-to-the-command-extension"></a>Добавление расширения MEF для расширения команды

1. В **обозревателе решений**, щелкните правой кнопкой мыши узел решения, нажмите кнопку **добавить**, а затем нажмите кнопку **новый проект**. В **Добавление нового проекта** диалоговом окне щелкните **расширяемости** под **Visual C#**, затем **проект VSIX**. Задайте для проекта имя `CommentAdornmentTest`.

2. Поскольку этот проект будет взаимодействовать со сборкой со строгим именем VSPackage, должен подписать сборку. Можно повторно использовать файл ключа, который уже создан для сборки пакета VSPackage.

    1. Откройте свойства проекта и выберите **подписывание** вкладки.

    2. Выберите **подписать сборку**.

    3. В разделе **выберите файл ключа строгого имени**выберите *Key.snk* файла, созданный для сборки MenuCommandTest.

## <a name="refer-to-the-mef-extension-in-the-vspackage-project"></a>Обращения к расширению MEF в проект VSPackage
 Так как вы добавляете компонент MEF объекту VSPackage, необходимо указать оба вида ресурсов в манифесте.

> [!NOTE]
> Дополнительные сведения о MEF см. в разделе [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

### <a name="to-refer-to-the-mef-component-in-the-vspackage-project"></a>Для ссылки на компонент MEF в проект VSPackage

1. В проекте MenuCommandTest, откройте *source.extension.vsixmanifest* файл в редакторе манифестов VSIX.

2. На **активы** щелкните **New**.

3. В **тип** выберите **Microsoft.VisualStudio.MefComponent**.

4. В **источника** выберите **проект в текущем решении**.

5. В **проекта** выберите **CommentAdornmentTest**.

6. Сохраните и закройте *source.extension.vsixmanifest* файл.

7. Убедитесь, что проект MenuCommandTest имеет ссылку на проект CommentAdornmentTest.

8. В проекте CommentAdornmentTest установите проект для создания сборки. В **обозревателе решений**, выберите проект и искать в **свойства** окно для **копирования выходных данных сборки для OutputDirectory** свойство и присвойте ему значение **true**.

## <a name="define-a-comment-adornment"></a>Определите оформления комментариев
 Сам оформления комментариев состоит из <xref:Microsoft.VisualStudio.Text.ITrackingSpan> выделенный текст и некоторые строки, представляющие автор и описание текста, который отслеживает.

#### <a name="to-define-a-comment-adornment"></a>Для определения оформления комментариев

1. В проекте CommentAdornmentTest, добавьте новый файл класса и назовите его `CommentAdornment`.

2. Добавьте следующие ссылки:

    1. Microsoft.VisualStudio.CoreUtility

    2. Microsoft.VisualStudio.Text.Data

    3. Microsoft.VisualStudio.Text.Logic

    4. Microsoft.VisualStudio.Text.UI

    5. Microsoft.VisualStudio.Text.UI.Wpf

    6. System.ComponentModel.Composition

    7. PresentationCore

    8. PresentationFramework

    9. WindowsBase

3. Добавьте следующий `using` инструкции.

    ```csharp
    using Microsoft.VisualStudio.Text;
    ```

4. Этот файл должен содержать класс с именем `CommentAdornment`.

    ```csharp
    internal class CommentAdornment
    ```

5. Добавьте три поля в `CommentAdornment` класса для <xref:Microsoft.VisualStudio.Text.ITrackingSpan>, автор и описание.

    ```csharp
    public readonly ITrackingSpan Span;
    public readonly string Author;
    public readonly string Text;
    ```

6. Добавьте конструктор, который инициализирует поля.

    ```csharp
    public CommentAdornment(SnapshotSpan span, string author, string text)
    {
        this.Span = span.Snapshot.CreateTrackingSpan(span, SpanTrackingMode.EdgeExclusive);
        this.Author = author;
        this.Text = text;
    }
    ```

## <a name="create-a-visual-element-for-the-adornment"></a>Создать визуальный элемент для оформления
 Определите визуальный элемент для вашего элемента оформления. В этом пошаговом руководстве определения элемента управления, который наследует от класса Windows Presentation Foundation (WPF) <xref:System.Windows.Controls.Canvas>.

1. Создайте класс в проекте CommentAdornmentTest и назовите его `CommentBlock`.

2. Добавьте следующие инструкции `using`.

    ```csharp
    using Microsoft.VisualStudio.Text;
    using System;
    using System.Windows;
    using System.Windows.Controls;
    using System.Windows.Media;
    using System.Windows.Shapes;
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Utilities;
    ```

3. Сделать `CommentBlock` наследовать класс от <xref:System.Windows.Controls.Canvas>.

    ```csharp
    internal class CommentBlock : Canvas
    { }
    ```

4. Добавьте несколько закрытых полей для определения визуальных характеристик элемента оформления.

    ```csharp
    private Geometry textGeometry;
    private Grid commentGrid;
    private static Brush brush;
    private static Pen solidPen;
    private static Pen dashPen;
    ```

5. Добавьте конструктор, который определяет оформления комментариев и добавляет соответствующий текст.

    ```csharp
    public CommentBlock(double textRightEdge, double viewRightEdge,
            Geometry newTextGeometry, string author, string body)
    {
        if (brush == null)
        {
            brush = new SolidColorBrush(Color.FromArgb(0x20, 0x00, 0xff, 0x00));
            brush.Freeze();
            Brush penBrush = new SolidColorBrush(Colors.Green);
            penBrush.Freeze();
            solidPen = new Pen(penBrush, 0.5);
            solidPen.Freeze();
            dashPen = new Pen(penBrush, 0.5);
            dashPen.DashStyle = DashStyles.Dash;
            dashPen.Freeze();
        }

        this.textGeometry = newTextGeometry;

        TextBlock tb1 = new TextBlock();
        tb1.Text = author;
        TextBlock tb2 = new TextBlock();
        tb2.Text = body;

        const int MarginWidth = 8;
        this.commentGrid = new Grid();
        this.commentGrid.RowDefinitions.Add(new RowDefinition());
        this.commentGrid.RowDefinitions.Add(new RowDefinition());
        ColumnDefinition cEdge = new ColumnDefinition();
        cEdge.Width = new GridLength(MarginWidth);
        ColumnDefinition cEdge2 = new ColumnDefinition();
        cEdge2.Width = new GridLength(MarginWidth);
        this.commentGrid.ColumnDefinitions.Add(cEdge);
        this.commentGrid.ColumnDefinitions.Add(new ColumnDefinition());
        this.commentGrid.ColumnDefinitions.Add(cEdge2);

        System.Windows.Shapes.Rectangle rect = new System.Windows.Shapes.Rectangle();
        rect.RadiusX = 6;
        rect.RadiusY = 3;
        rect.Fill = brush;
        rect.Stroke = Brushes.Green;

            Size inf = new Size(double.PositiveInfinity, double.PositiveInfinity);
            tb1.Measure(inf);
            tb2.Measure(inf);
            double middleWidth = Math.Max(tb1.DesiredSize.Width, tb2.DesiredSize.Width);
            this.commentGrid.Width = middleWidth + 2 * MarginWidth;

        Grid.SetColumn(rect, 0);
        Grid.SetRow(rect, 0);
        Grid.SetRowSpan(rect, 2);
        Grid.SetColumnSpan(rect, 3);
        Grid.SetRow(tb1, 0);
        Grid.SetColumn(tb1, 1);
        Grid.SetRow(tb2, 1);
        Grid.SetColumn(tb2, 1);
        this.commentGrid.Children.Add(rect);
        this.commentGrid.Children.Add(tb1);
        this.commentGrid.Children.Add(tb2);

        Canvas.SetLeft(this.commentGrid, Math.Max(viewRightEdge - this.commentGrid.Width - 20.0, textRightEdge + 20.0));
        Canvas.SetTop(this.commentGrid, textGeometry.GetRenderBounds(solidPen).Top);

        this.Children.Add(this.commentGrid);
    }
    ```

6. Кроме того, реализовать <xref:System.Windows.Controls.Panel.OnRender%2A> обработчик событий, который рисует оформления.

    ```csharp
    protected override void OnRender(DrawingContext dc)
    {
        base.OnRender(dc);
        if (this.textGeometry != null)
        {
            dc.DrawGeometry(brush, solidPen, this.textGeometry);
            Rect textBounds = this.textGeometry.GetRenderBounds(solidPen);
            Point p1 = new Point(textBounds.Right, textBounds.Bottom);
            Point p2 = new Point(Math.Max(Canvas.GetLeft(this.commentGrid) - 20.0, p1.X), p1.Y);
            Point p3 = new Point(Math.Max(Canvas.GetLeft(this.commentGrid), p1.X), (Canvas.GetTop(this.commentGrid) + p1.Y) * 0.5);
            dc.DrawLine(dashPen, p1, p2);
            dc.DrawLine(dashPen, p2, p3);
        }
    }
    ```

## <a name="add-an-iwpftextviewcreationlistener"></a>Add an IWpfTextViewCreationListener
 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> — Это часть компонентов MEF, можно использовать для ожидания передачи данных, чтобы просмотреть события создания.

1. Добавьте файл класса в проект CommentAdornmentTest и назовите его `Connector`.

2. Добавьте следующие инструкции `using`.

    ```csharp
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Utilities;
    ```

3. Объявите класс, реализующий <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>и экспортировать его с <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> «текст» и <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> из <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document>. Атрибут типа содержимого задает тип содержимого, к которому применяется компонента. Тип текста является базовым типом для всех типов файлов не являлись двоичными. Таким образом почти все представления текста, который создается будет этого типа. Атрибут роли представления текста указывает тип представления текста, к которому применяется компонента. Роли представления текста документа обычно Показать текст, который состоит из строк и хранится в файле.

     [!code-vb[VSSDKMenuCommandTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_1.vb)]
     [!code-csharp[VSSDKMenuCommandTest#11](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_1.cs)]

4. Реализуйте <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> он вызывает статический метод `Create()` событие `CommentAdornmentManager`.

    ```csharp
    public void TextViewCreated(IWpfTextView textView)
    {
        CommentAdornmentManager.Create(textView);
    }
    ```

5. Добавьте метод, который можно использовать для выполнения команды.

    ```csharp
    static public void Execute(IWpfTextViewHost host)
    {
        IWpfTextView view = host.TextView;
        //Add a comment on the selected text. 
        if (!view.Selection.IsEmpty)
        {
            //Get the provider for the comment adornments in the property bag of the view.
            CommentAdornmentProvider provider = view.Properties.GetProperty<CommentAdornmentProvider>(typeof(CommentAdornmentProvider));

            //Add some arbitrary author and comment text. 
            string author = System.Security.Principal.WindowsIdentity.GetCurrent().Name;
            string comment = "Four score....";

            //Add the comment adornment using the provider.
            provider.Add(view.Selection.SelectedSpans[0], author, comment);
        }
    }
    ```

## <a name="define-an-adornment-layer"></a>Определите слое оформлений
 Чтобы добавить нового оформления, необходимо определить слое оформлений.

### <a name="to-define-an-adornment-layer"></a>Для определения слое оформлений

1. В `Connector` определите открытое поле типа <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition>и экспортировать его с <xref:Microsoft.VisualStudio.Utilities.NameAttribute> , задающий уникальное имя для слое оформлений и <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> , определяющий отношение Z-порядок этом слое оформлений весь прочий текст Просмотр уровней (текст, курсор и выделение).

    ```csharp
    [Export(typeof(AdornmentLayerDefinition))]
    [Name("CommentAdornmentLayer")]
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
    public AdornmentLayerDefinition commentLayerDefinition;

    ```

## <a name="provide-comment-adornments"></a>Укажите элементы оформления комментариев
 При определении элемент оформления, также реализуйте поставщик элемента оформления комментариев и диспетчер оформления комментариев. Поставщик элемента оформления комментариев хранит список элементов оформления комментариев, прослушивает <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> события в базовом текстовом буфере и удаляет элементы оформления комментарий при удалении основной текст.

1. Добавьте новый файл класса в проект CommentAdornmentTest и назовите его `CommentAdornmentProvider`.

2. Добавьте следующие инструкции `using`.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Collections.ObjectModel;
    using Microsoft.VisualStudio.Text;
    using Microsoft.VisualStudio.Text.Editor;
    ```

3. Добавьте класс с именем `CommentAdornmentProvider`.

    ```csharp
    internal class CommentAdornmentProvider
    {
    }
    ```

4. Добавьте закрытые поля для текстового буфера и список элементов оформления комментариев, связанных в буфер.

    ```csharp
    private ITextBuffer buffer;
    private IList<CommentAdornment> comments = new List<CommentAdornment>();

    ```

5. Добавьте конструктор для `CommentAdornmentProvider`. Этот конструктор следует имеют закрытый доступ, так как экземпляр поставщика создается путем `Create()` метод. Конструктор добавляет `OnBufferChanged` в обработчике событий <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> событий.

    ```csharp
    private CommentAdornmentProvider(ITextBuffer buffer)
    {
        this.buffer = buffer;
        //listen to the Changed event so we can react to deletions. 
        this.buffer.Changed += OnBufferChanged;
    }

    ```

6. Добавьте метод `Create()`.

    ```csharp
    public static CommentAdornmentProvider Create(IWpfTextView view)
    {
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentProvider>(delegate { return new CommentAdornmentProvider(view.TextBuffer); });
    }

    ```

7. Добавьте метод `Detach()`.

    ```csharp
    public void Detach()
    {
        if (this.buffer != null)
        {
            //remove the Changed listener 
            this.buffer.Changed -= OnBufferChanged;
            this.buffer = null;
        }
    }
    ```

8. Добавление `OnBufferChanged` обработчик событий.

     [!code-csharp[VSSDKMenuCommandTest#21](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_2.cs)]
     [!code-vb[VSSDKMenuCommandTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_2.vb)]

9. Добавьте объявление для `CommentsChanged` событий.

    ```csharp
    public event EventHandler<CommentsChangedEventArgs> CommentsChanged;
    ```

10. Создание `Add()` метод, чтобы добавить оформления.

    ```csharp
    public void Add(SnapshotSpan span, string author, string text)
    {
        if (span.Length == 0)
            throw new ArgumentOutOfRangeException("span");
        if (author == null)
            throw new ArgumentNullException("author");
        if (text == null)
            throw new ArgumentNullException("text");

        //Create a comment adornment given the span, author and text.
        CommentAdornment comment = new CommentAdornment(span, author, text);

        //Add it to the list of comments. 
        this.comments.Add(comment);

        //Raise the changed event.
        EventHandler<CommentsChangedEventArgs> commentsChanged = this.CommentsChanged;
        if (commentsChanged != null)
            commentsChanged(this, new CommentsChangedEventArgs(comment, null));
    }

    ```

11. Добавление `RemoveComments()` метод.

    ```csharp
    public void RemoveComments(SnapshotSpan span)
    {
        EventHandler<CommentsChangedEventArgs> commentsChanged = this.CommentsChanged;

        //Get a list of all the comments that are being kept
        IList<CommentAdornment> keptComments = new List<CommentAdornment>(this.comments.Count);

        foreach (CommentAdornment comment in this.comments)
        {
            //find out if the given span overlaps with the comment text span. If two spans are adjacent, they do not overlap. To consider adjacent spans, use IntersectsWith. 
            if (comment.Span.GetSpan(span.Snapshot).OverlapsWith(span))
            {
                //Raise the change event to delete this comment. 
                if (commentsChanged != null)
                    commentsChanged(this, new CommentsChangedEventArgs(null, comment));
            }
            else
                keptComments.Add(comment);
        }

        this.comments = keptComments;
    }
    ```

12. Добавление `GetComments()` метод, возвращающий все комментарии в диапазон данного снимка.

    ```csharp
    public Collection<CommentAdornment> GetComments(SnapshotSpan span)
    {
        IList<CommentAdornment> overlappingComments = new List<CommentAdornment>();
        foreach (CommentAdornment comment in this.comments)
        {
            if (comment.Span.GetSpan(span.Snapshot).OverlapsWith(span))
                overlappingComments.Add(comment);
        }

        return new Collection<CommentAdornment>(overlappingComments);
    }
    ```

13. Добавьте класс с именем `CommentsChangedEventArgs`, как показано ниже.

    ```csharp
    internal class CommentsChangedEventArgs : EventArgs
    {
        public readonly CommentAdornment CommentAdded;

        public readonly CommentAdornment CommentRemoved;

        public CommentsChangedEventArgs(CommentAdornment added, CommentAdornment removed)
        {
            this.CommentAdded = added;
            this.CommentRemoved = removed;
        }
    }
    ```

## <a name="manage-comment-adornments"></a>Управление элементы оформления комментариев
 Диспетчер оформления комментариев создает оформления и добавляет его в слое оформлений. Он прослушивает <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> и <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> события, поэтому ее можно переместить или удалить оформления. Он также прослушивает `CommentsChanged` событие, инициируемое поставщиком оформления комментариев при комментарии добавляются или удаляются.

1. Добавьте файл класса в проект CommentAdornmentTest и назовите его `CommentAdornmentManager`.

2. Добавьте следующие инструкции `using`.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Windows.Media;
    using Microsoft.VisualStudio.Text;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Text.Formatting;
    ```

3. Добавьте класс с именем `CommentAdornmentManager`.

    ```csharp
    internal class CommentAdornmentManager
        {
        }
    ```

4. Добавьте несколько закрытых полей.

    ```csharp
    private readonly IWpfTextView view;
    private readonly IAdornmentLayer layer;
    private readonly CommentAdornmentProvider provider;
    ```

5. Добавьте конструктор, который создает подписку, чтобы диспетчер мог <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> и <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> события, а также с `CommentsChanged` событий. Конструктор является закрытым, поскольку диспетчер создается статическим `Create()` метод.

    ```csharp
    private CommentAdornmentManager(IWpfTextView view)
    {
        this.view = view;
        this.view.LayoutChanged += OnLayoutChanged;
        this.view.Closed += OnClosed;

        this.layer = view.GetAdornmentLayer("CommentAdornmentLayer");

        this.provider = CommentAdornmentProvider.Create(view);
        this.provider.CommentsChanged += OnCommentsChanged;
    }
    ```

6. Добавление `Create()` метод, который возвращает поставщик или при необходимости создает ее.

    ```csharp
    public static CommentAdornmentManager Create(IWpfTextView view)
    {
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentManager>(delegate { return new CommentAdornmentManager(view); });
    }
    ```

7. Добавление `CommentsChanged` обработчика.

    ```csharp
    private void OnCommentsChanged(object sender, CommentsChangedEventArgs e)
    {
        //Remove the comment (when the adornment was added, the comment adornment was used as the tag). 
        if (e.CommentRemoved != null)
            this.layer.RemoveAdornmentsByTag(e.CommentRemoved);

        //Draw the newly added comment (this will appear immediately: the view does not need to do a layout). 
        if (e.CommentAdded != null)
            this.DrawComment(e.CommentAdded);
    }
    ```

8. Добавление <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> обработчика.

    ```csharp
    private void OnClosed(object sender, EventArgs e)
    {
        this.provider.Detach();
        this.view.LayoutChanged -= OnLayoutChanged;
        this.view.Closed -= OnClosed;
    }
    ```

9. Добавление <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> обработчика.

    ```csharp
    private void OnLayoutChanged(object sender, TextViewLayoutChangedEventArgs e)
    {
        //Get all of the comments that intersect any of the new or reformatted lines of text.
        List<CommentAdornment> newComments = new List<CommentAdornment>();

        //The event args contain a list of modified lines and a NormalizedSpanCollection of the spans of the modified lines.  
        //Use the latter to find the comments that intersect the new or reformatted lines of text. 
        foreach (Span span in e.NewOrReformattedSpans)
        {
            newComments.AddRange(this.provider.GetComments(new SnapshotSpan(this.view.TextSnapshot, span)));
        }

        //It is possible to get duplicates in this list if a comment spanned 3 lines, and the first and last lines were modified but the middle line was not. 
        //Sort the list and skip duplicates.
        newComments.Sort(delegate(CommentAdornment a, CommentAdornment b) { return a.GetHashCode().CompareTo(b.GetHashCode()); });

        CommentAdornment lastComment = null;
        foreach (CommentAdornment comment in newComments)
        {
            if (comment != lastComment)
            {
                lastComment = comment;
                this.DrawComment(comment);
            }
        }
    }
    ```

10. Добавьте закрытый метод, который рисует комментарий.

     [!code-csharp[VSSDKMenuCommandTest#35](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_3.cs)]
     [!code-vb[VSSDKMenuCommandTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_3.vb)]

## <a name="use-the-menu-command-to-add-the-comment-adornment"></a>Используйте команду меню, чтобы добавить комментарий оформления
 Команды меню можно использовать для создания оформления комментариев, реализовав `MenuItemCallback` методе VSPackage.

1. Добавьте следующие ссылки в проект MenuCommandTest:

    - Microsoft.VisualStudio.TextManager.Interop

    - Microsoft.VisualStudio.Editor

    - Microsoft.VisualStudio.Text.UI.Wpf

2. Откройте *AddAdornment.cs* файл и добавьте следующие `using` инструкций.

    ```csharp
    using Microsoft.VisualStudio.TextManager.Interop;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Editor;
    using CommentAdornmentTest;
    ```

3. Удалить `Execute()` метод и добавьте следующий обработчик команд.

    ```csharp
    private async void AddAdornmentHandler(object sender, EventArgs e)
    {
    }
    ```

4. Добавьте код для получения активное представление. Необходимо получить `SVsTextManager` оболочки Visual Studio для получения активной `IVsTextView`.

    ```csharp
    private async void AddAdornmentHandler(object sender, EventArgs e)
    {
        IVsTextManager txtMgr = (IVsTextManager) await ServiceProvider.GetServiceAsync(typeof(SVsTextManager));
        IVsTextView vTextView = null;
        int mustHaveFocus = 1;
        txtMgr.GetActiveView(mustHaveFocus, null, out vTextView);
    }
    ```

5. Если данного представления текста — это экземпляр представление текстового редактора, их можно привести к <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> интерфейс, а затем получите <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> и связанный с ним <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>. Используйте <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> для вызова `Connector.Execute()` метод, который получает поставщик элемента оформления комментариев и добавляет оформления. Обработчик команд теперь должен выглядеть так этот код:

    ```csharp
    private async void AddAdornmentHandler(object sender, EventArgs e)
    {
        IVsTextManager txtMgr = (IVsTextManager) await ServiceProvider.GetServiceAsync(typeof(SVsTextManager));
        IVsTextView vTextView = null;
        int mustHaveFocus = 1;
        txtMgr.GetActiveView(mustHaveFocus, null, out vTextView);
        IVsUserData userData = vTextView as IVsUserData;
         if (userData == null)
        {
            Console.WriteLine("No text view is currently open");
            return;
        }
        IWpfTextViewHost viewHost;
        object holder;
        Guid guidViewHost = DefGuidList.guidIWpfTextViewHost;
        userData.GetData(ref guidViewHost, out holder);
        viewHost = (IWpfTextViewHost)holder;
        Connector.Execute(viewHost);
    }
    ```

6. Задайте метод AddAdornmentHandler в качестве обработчика команды AddAdornment в конструкторе AddAdornment.

    ```csharp
    private AddAdornment(AsyncPackage package, OleMenuCommandService commandService)
    {
        this.package = package ?? throw new ArgumentNullException(nameof(package));
        commandService = commandService ?? throw new ArgumentNullException(nameof(commandService));

        var menuCommandID = new CommandID(CommandSet, CommandId);
        var menuItem = new MenuCommand(this.AddAdornmentHandler, menuCommandID);
        commandService.AddCommand(menuItem);
    }
    ```

## <a name="build-and-test-the-code"></a>Построение и тестирование кода

1. Постройте решение и запустите отладку. Откроется экспериментальный экземпляр.

2. Создание текстового файла. Введите текст, а затем выберите его.

3. На **средства** меню, щелкните **вызова добавьте оформления**. Всплывающую должны отображаться в правой части текстового окна и должно содержать текст, похожий на следующий текст.

     Имя_пользователя

     Fourscore...

## <a name="see-also"></a>См. также
- [Пошаговое руководство: Связывание типа контента с расширением имени файла](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
