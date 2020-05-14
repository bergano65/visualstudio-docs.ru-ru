---
title: 'Прохождение: Использование командования Shell с расширением редактора (ru) Документы Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - add a menu command
ms.assetid: 08526848-a442-4cd4-afa1-b2eac2005adb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 52b151b09c1bb7306b4270f9408d0f04a7600aa2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697168"
---
# <a name="walkthrough-use-a-shell-command-with-an-editor-extension"></a>Прохождение: Используйте команду оболочки с расширением редактора
Из VSPackage можно добавить в редактор такие функции, как команды меню. В этом пошаговом показании, как добавить украшение в текстовое представление в редакторе, ссылаясь на команду меню.

 Это пошаговое решение демонстрирует использование VSPackage вместе с компонентной частью Управляемой рамки для расширяемости (MEF). Для регистрации команды меню оболочкой Visual Studio необходимо использовать VSPackage. И вы можете использовать команду для доступа к компонентной части MEF.

## <a name="prerequisites"></a>Предварительные требования
 Начиная с Visual Studio 2015, вы не устанавливаете Visual Studio SDK из центра загрузки. Он включен в качестве дополнительной функции в Visual Studio установки. Вы также можете установить VS SDK позже. Для получения дополнительной информации, [см.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-an-extension-with-a-menu-command"></a>Создание расширения с командой меню
 Создайте VSPackage, который помещает команду меню под названием **Добавить Украшение** в меню **Инструментов.**

1. Создайте проект VSIX `MenuCommandTest`под названием и добавьте имя шаблона шаблона Custom Command **AddAdornment.** Для получения дополнительной информации [см. Создать расширение с командой меню](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Открывается решение под названием MenuCommandTest. В файле MenuCommandTestPackage есть код, который создает команду меню и помещает ее в меню **Инструментов.** На этом этапе команда просто вызывает окно сообщения. Позже шаги покажут, как изменить это для отображения украшения комментария.

3. Откройте файл *source.extension.vsixmanifest* в редакторе VSIX Manifest. Вкладка `Assets` должна иметь строку для Microsoft.VisualStudio.VsPackage под названием MenuCommandTest.

4. Сохранить и закрыть *файл source.extension.vsixmanifest.*

## <a name="add-a-mef-extension-to-the-command-extension"></a>Добавление расширения MEF в расширение команды

1. В **Solution Explorer**, правой кнопкой мыши узла решения, нажмите **Добавить**, а затем нажмите **Новый проект**. В диалоговом окне **Добавить новый проект** нажмите **На расширяемость** под **Visual C ,** затем **VSIX Project**. Присвойте проекту имя `CommentAdornmentTest`.

2. Поскольку этот проект будет взаимодействовать с сильной сборкой VSPackage, необходимо подписать сборку. Можно повторно использовать файл ключа, уже созданный для сборки VSPackage.

    1. Откройте свойства проекта и выберите вкладку **«Подпись».**

    2. Выберите **Знак сборки**.

    3. При **выборе файла с сильным именем**выберите файл *Key.snk,* который был создан для сборки MenuCommandTest.

## <a name="refer-to-the-mef-extension-in-the-vspackage-project"></a>Ссылайтесь на расширение MEF в проекте VSPackage
 Поскольку вы добавляете компонент MEF в VSPackage, необходимо указать оба вида активов в манифесте.

> [!NOTE]
> Для получения дополнительной информации о MEF [см.](/dotnet/framework/mef/index)

### <a name="to-refer-to-the-mef-component-in-the-vspackage-project"></a>Для обозначения компонента MEF в проекте VSPackage

1. В проекте MenuCommandTest откройте файл *source.extension.vsixmanifest* в редакторе VSIX Manifest.

2. На вкладке **Активы** нажмите **Новый**.

3. В списке **Типов** выберите **Microsoft.VisualStudio.MefComponent**.

4. В списке **Исходного** списка выберите **проект в текущем решении.**

5. В списке **проекта** выберите **CommentAdorn**.

6. Сохранить и закрыть *файл source.extension.vsixmanifest.*

7. Убедитесь, что проект MenuCommandTest имеет ссылку на проект CommentAdornTest.

8. В проекте CommentAdornTest установите проект для создания сборки. В **Solution Explorer**выберите проект и посмотрите в окне **Свойств** для **вывода Copy Build Output to OutputDirectory** и установите его на **истину.**

## <a name="define-a-comment-adornment"></a>Определить украшение комментария
 Сам комментарий состоит из <xref:Microsoft.VisualStudio.Text.ITrackingSpan> того, что отслеживает выбранный текст, и некоторые строки, которые представляют автора и описание текста.

#### <a name="to-define-a-comment-adornment"></a>Определить украшение комментария

1. В проекте CommentAdorn добавьте новый файл `CommentAdornment`класса и назовите его.

2. Добавьте следующие ссылки.

    1. Microsoft.VisualStudio.CoreUtility

    2. Microsoft.VisualStudio.Text.Data

    3. Microsoft.VisualStudio.Text.Logic

    4. Microsoft.VisualStudio.Text.UI

    5. Microsoft.VisualStudio.Text.UI.Wpf

    6. System.ComponentModel.Composition

    7. PresentationCore

    8. PresentationFramework

    9. WindowsBase

3. Добавьте `using` следующую директиву.

    ```csharp
    using Microsoft.VisualStudio.Text;
    ```

4. Файл должен содержать класс `CommentAdornment`с именем.

    ```csharp
    internal class CommentAdornment
    ```

5. Добавьте три `CommentAdornment` поля в <xref:Microsoft.VisualStudio.Text.ITrackingSpan>класс для автора и описания.

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

## <a name="create-a-visual-element-for-the-adornment"></a>Создание визуального элемента для украшения
 Определите визуальный элемент для украшения. Для этого пошагового представления определите элемент управления, который следует <xref:System.Windows.Controls.Canvas>из класса Windows Presentation Foundation (WPF).

1. Создайте класс в проекте CommentAdorn и `CommentBlock`назовите его.

2. Добавьте `using` следующие директивы.

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

3. Сделать `CommentBlock` класс <xref:System.Windows.Controls.Canvas>наследовать от .

    ```csharp
    internal class CommentBlock : Canvas
    { }
    ```

4. Добавьте несколько частных полей, чтобы определить визуальные аспекты украшения.

    ```csharp
    private Geometry textGeometry;
    private Grid commentGrid;
    private static Brush brush;
    private static Pen solidPen;
    private static Pen dashPen;
    ```

5. Добавьте конструктор, который определяет украшение комментария и добавляет соответствующий текст.

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

6. Также реализуем <xref:System.Windows.Controls.Panel.OnRender%2A> обработчик событий, который рисует украшение.

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

## <a name="add-an-iwpftextviewcreationlistener"></a>Добавить IWpfTextViewCreationListener
 Компонент <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> MEF, который можно использовать для прослушивания событий создания.

1. Добавьте файл класса в проект CommentAdorntest `Connector`и назовите его.

2. Добавьте `using` следующие директивы.

    ```csharp
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Utilities;
    ```

3. Объявить класс, <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>который реализует, и <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> экспортировать его <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> с <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document>"текст" и . Атрибут типа содержимого определяет вид содержимого, к которому применяется компонент. Тип текста является базовым типом для всех небинарных типов файлов. Таким образом, почти каждый созданный текст будет такого типа. Атрибут роли представления текста определяет вид представления текста, к которому применяется компонент. Роли представления текста документа обычно показывают текст, который состоит из строк и хранится в файле.

     [!code-vb[VSSDKMenuCommandTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_1.vb)]
     [!code-csharp[VSSDKMenuCommandTest#11](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_1.cs)]

4. Реализация <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> метода так, чтобы `Create()` он `CommentAdornmentManager`вызывает статическое событие .

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

## <a name="define-an-adornment-layer"></a>Определить слой украшения
 Чтобы добавить новое украшение, необходимо определить слой украшения.

### <a name="to-define-an-adornment-layer"></a>Определить слой украшения

1. В `Connector` классе объявите публичное <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition>поле типа и <xref:Microsoft.VisualStudio.Utilities.NameAttribute> экспортируете его с помощью элемента, <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> определяющего уникальное название для слоя украшения, и то, что определяет отношение этого слоя украшения к другим слоям представления текста (текст, уход и выбор).

    ```csharp
    [Export(typeof(AdornmentLayerDefinition))]
    [Name("CommentAdornmentLayer")]
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
    public AdornmentLayerDefinition commentLayerDefinition;

    ```

## <a name="provide-comment-adornments"></a>Предоставить комментарии украшения
 Когда вы определяете украшение, также реализовать комментарий украшения поставщика и менеджер украшения комментариев. Поставщик украшений комментариев сохраняет список украшений <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> комментариев, прослушивает события в базовом буфере текста и удаляет украшения комментариев при удалении основного текста.

1. Добавьте новый файл класса в проект CommentAdornmentTest и назовите его. `CommentAdornmentProvider`

2. Добавьте `using` следующие директивы.

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

4. Добавьте частные поля для буфера текста и список комментариев, связанных с буфером.

    ```csharp
    private ITextBuffer buffer;
    private IList<CommentAdornment> comments = new List<CommentAdornment>();

    ```

5. Добавить конструктор `CommentAdornmentProvider`для . Этот конструктор должен иметь частный `Create()` доступ, потому что поставщик мгновенно метод. Конструктор добавляет обработчик `OnBufferChanged` события <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> к событию.

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

8. Добавьте `OnBufferChanged` обработчик событий.

     [!code-csharp[VSSDKMenuCommandTest#21](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_2.cs)]
     [!code-vb[VSSDKMenuCommandTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_2.vb)]

9. Добавьте декларацию `CommentsChanged` для события.

    ```csharp
    public event EventHandler<CommentsChangedEventArgs> CommentsChanged;
    ```

10. Создайте `Add()` метод для добавления украшения.

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

11. Добавьте `RemoveComments()` метод.

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

12. Добавьте `GetComments()` метод, который возвращает все комментарии в заданном диапазоне моментальных снимков.

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

13. Добавить класс `CommentsChangedEventArgs`с именем, следующим образом.

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

## <a name="manage-comment-adornments"></a>Управление комментариями украшения
 Менеджер по украшению комментариев создает украшение и добавляет его в слой украшения. Он слушает события <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> и события, так что он может переместить или удалить украшения. Он также слушает `CommentsChanged` событие, которое уволено поставщиком украшений комментариев при добавлении или удалении комментариев.

1. Добавьте файл класса в проект CommentAdorntest `CommentAdornmentManager`и назовите его.

2. Добавьте `using` следующие директивы.

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

4. Добавьте несколько частных полей.

    ```csharp
    private readonly IWpfTextView view;
    private readonly IAdornmentLayer layer;
    private readonly CommentAdornmentProvider provider;
    ```

5. Добавьте конструктор, который подписывает <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> менеджера <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> на события и `CommentsChanged` события, а также на событие. Конструктор является частным, потому что менеджер мгновенно `Create()` статический метод.

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

6. Добавьте `Create()` метод, который получает поставщика или создает его, если это необходимо.

    ```csharp
    public static CommentAdornmentManager Create(IWpfTextView view)
    {
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentManager>(delegate { return new CommentAdornmentManager(view); });
    }
    ```

7. Добавьте `CommentsChanged` обработчика.

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

8. Добавьте <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> обработчика.

    ```csharp
    private void OnClosed(object sender, EventArgs e)
    {
        this.provider.Detach();
        this.view.LayoutChanged -= OnLayoutChanged;
        this.view.Closed -= OnClosed;
    }
    ```

9. Добавьте <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> обработчика.

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

10. Добавьте частный метод, который рисует комментарий.

     [!code-csharp[VSSDKMenuCommandTest#35](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_3.cs)]
     [!code-vb[VSSDKMenuCommandTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_3.vb)]

## <a name="use-the-menu-command-to-add-the-comment-adornment"></a>Используйте команду меню, чтобы добавить украшение комментариев
 Вы можете использовать команду меню для создания украшения `MenuItemCallback` комментариев, реализуя метод VSPackage.

1. Добавьте следующие ссылки на проект MenuCommandTest:

    - Microsoft.VisualStudio.TextManager.Interop

    - Microsoft.VisualStudio.Редактор

    - Microsoft.VisualStudio.Text.UI.Wpf

2. Откройте *файл AddAdornment.cs* и `using` добавьте следующие директивы.

    ```csharp
    using Microsoft.VisualStudio.TextManager.Interop;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Editor;
    using CommentAdornmentTest;
    ```

3. Удалите `Execute()` метод и добавьте следующий обработчик команды.

    ```csharp
    private async void AddAdornmentHandler(object sender, EventArgs e)
    {
    }
    ```

4. Добавьте код, чтобы получить активное представление. Вы должны `SVsTextManager` получить оболочку Visual Studio, `IVsTextView`чтобы получить активный .

    ```csharp
    private async void AddAdornmentHandler(object sender, EventArgs e)
    {
        IVsTextManager txtMgr = (IVsTextManager) await ServiceProvider.GetServiceAsync(typeof(SVsTextManager));
        IVsTextView vTextView = null;
        int mustHaveFocus = 1;
        txtMgr.GetActiveView(mustHaveFocus, null, out vTextView);
    }
    ```

5. Если это текстовое представление является экземпляром текстового представления <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> редактора, <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> его можно <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>отбросить в интерфейс, а затем получить и связанный с ним . Используйте <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> для `Connector.Execute()` вызова метода, который получает комментарий украшения поставщика и добавляет украшения. Обработчик команды теперь должен выглядеть следующим образом:

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

6. Установите метод AddAdornmentHandler в качестве обработчика для команды AddAdornment в конструкторе AddAdornment.

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

## <a name="build-and-test-the-code"></a>Создание и тестирование кода

1. Постройте решение и запустите отладку. Экспериментальный экземпляр должен появиться.

2. Создание текстового файла. Введите текст, а затем выберите его.

3. В меню **«Инструменты»** нажмите **«Вызвать добавление украшения».** Воздушный шар должен отображаться на правой стороне текстового окна и содержать текст, напоминающий следующий текст.

     ВашUserName

     Fourscore...

## <a name="see-also"></a>См. также
- [Прохождение: Свяжите тип содержимого с расширением имени файла](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
