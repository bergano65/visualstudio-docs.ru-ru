---
title: Пошаговое руководство. Использование команды оболочки с расширением редактора | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - add a menu command
ms.assetid: 08526848-a442-4cd4-afa1-b2eac2005adb
caps.latest.revision: 47
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0312d98dd6959cb5d67d593c4bf0af39fa1889eb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65693360"
---
# <a name="walkthrough-using-a-shell-command-with-an-editor-extension"></a>Пошаговое руководство. Использование командной оболочки в расширении редактора
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Из VSPackage можно добавить в редактор такие компоненты, как команды меню. В этом пошаговом руководстве показано, как добавить Оформление в текстовое представление в редакторе, вызвав команду меню.  
  
 В этом пошаговом руководстве демонстрируется использование VSPackage вместе с частью компонента Managed Extensibility Framework (MEF). Для регистрации команды меню в оболочке Visual Studio необходимо использовать VSPackage, а для доступа к части компонента MEF можно использовать команду.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, пакет SDK для Visual Studio не устанавливается из центра загрузки. Он входит в состав программы установки Visual Studio как дополнительный компонент. Кроме того, пакет SDK для VS можно установить позже. Дополнительные сведения см. [в разделе Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-an-extension-with-a-menu-command"></a>Создание расширения с помощью команды меню  
 Создайте пакет VSPackage, который помещает команду меню **Add оформления** в меню **Сервис** .  
  
1. Создайте проект VSIX C# с именем `MenuCommandTest` и добавьте настраиваемое имя шаблона элемента команды **аддадорнмент**. Дополнительные сведения см. в разделе [Создание расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2. Открывается решение с именем Менукоммандтест. Файл Менукоммандтестпаккаже содержит код, который создает команду меню и помещает ее в меню **Сервис** . На этом этапе команда просто отображает окно сообщения. В последующих шагах показано, как изменить это значение, чтобы отобразить оформление комментария.  
  
3. Откройте файл source.extension.vsixmanifest в редакторе манифестов VSIX. `Assets`Вкладка должна содержать строку для Microsoft. VisualStudio. VSPackage с именем менукоммандтест.  
  
4. Сохраните и закройте файл Source. extension. vsixmanifest.  
  
## <a name="adding-a-mef-extension-to-the-command-extension"></a>Добавление расширения MEF к расширению команды  
  
1. В **Обозреватель решений**щелкните правой кнопкой мыши узел решения, выберите **Добавить**, а затем щелкните **Новый проект**. В диалоговом окне **Добавление нового проекта** щелкните **расширяемость** в разделе **Visual C#**, а затем **проект VSIX**. Присвойте проекту имя `CommentAdornmentTest`.  
  
2. Так как этот проект будет взаимодействовать со строго именованной сборкой VSPackage, необходимо подписать сборку. Можно повторно использовать файл ключа, уже созданный для сборки VSPackage.  
  
    1. Откройте свойства проекта и выберите вкладку **Подписывание** .  
  
    2. Выберите **подписать сборку**.  
  
    3. В разделе **выберите файл ключа строгого имени**выберите файл key. snk, созданный для сборки менукоммандтест.  
  
## <a name="referring-to-the-mef-extension-in-the-vspackage-project"></a>Ссылка на расширение MEF в проекте VSPackage  
 Поскольку в VSPackage добавляется компонент MEF, необходимо указать оба типа ресурсов в манифесте.  
  
> [!NOTE]
> Дополнительные сведения о MEF см. в разделе [Managed Extensibility Framework (MEF)](https://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde).  
  
#### <a name="to-refer-to-the-mef-component-in-the-vspackage-project"></a>Ссылка на компонент MEF в проекте VSPackage  
  
1. В проекте Менукоммандтест откройте файл Source. extension. vsixmanifest в редакторе манифеста VSIX.  
  
2. На вкладке **активы** щелкните **создать**.  
  
3. В списке **тип** выберите **Microsoft. VisualStudio. MefComponent**.  
  
4. В списке **источник** выберите **проект в текущем решении**.  
  
5. В списке **проект** выберите **комментадорнменттест**.  
  
6. Сохраните и закройте файл Source. extension. vsixmanifest.  
  
7. Убедитесь, что проект Менукоммандтест содержит ссылку на проект Комментадорнменттест.  
  
8. В проекте Комментадорнменттест задайте проект, чтобы создать сборку. В **Обозреватель решений**выберите проект и найдите в окне **свойств** свойство **Копировать выходные данные сборки в OutputDirectory** и задайте для него **значение true**.  
  
## <a name="defining-a-comment-adornment"></a>Определение оформления комментария  
 Крайний комментарий состоит из объекта <xref:Microsoft.VisualStudio.Text.ITrackingSpan> , который отслеживает выбранный текст и некоторые строки, представляющие автора и описание текста.  
  
#### <a name="to-define-a-comment-adornment"></a>Определение оформления комментария  
  
1. В проекте Комментадорнменттест добавьте новый файл класса и назовите его `CommentAdornment` .  
  
2. Добавьте следующие ссылки.  
  
    1. Microsoft. VisualStudio. Кореутилити  
  
    2. Microsoft. VisualStudio. Text. Data  
  
    3. Microsoft. VisualStudio. Text. Logic  
  
    4. Microsoft. VisualStudio. Text. UI  
  
    5. Microsoft. VisualStudio. Text. UI. WPF  
  
    6. System.ComponentModel.Composition  
  
    7. PresentationCore  
  
    8. PresentationFramework  
  
    9. WindowsBase  
  
3. Добавьте следующий оператор `using` .  
  
    ```vb  
    using Microsoft.VisualStudio.Text;  
    ```  
  
4. Файл должен содержать класс с именем `CommentAdornment` .  
  
    ```  
    internal class CommentAdornment  
    ```  
  
5. Добавьте три поля в `CommentAdornment` класс для <xref:Microsoft.VisualStudio.Text.ITrackingSpan> , автора и описание.  
  
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
  
## <a name="creating-a-visual-element-for-the-adornment"></a>Создание визуального элемента для оформления  
 Необходимо также определить визуальный элемент для своего оформления. Для этого пошагового руководства определите элемент управления, который наследуется от класса Windows Presentation Foundation (WPF) <xref:System.Windows.Controls.Canvas> .  
  
1. Создайте класс в проекте Комментадорнменттест и присвойте ему имя `CommentBlock` .  
  
2. Добавьте следующие операторы `using`.  
  
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
  
3. Сделайте `CommentBlock` класс производным от <xref:System.Windows.Controls.Canvas> .  
  
    ```csharp  
    internal class CommentBlock : Canvas  
    { }  
    ```  
  
4. Добавьте некоторые закрытые поля для определения визуальных аспектов оформления.  
  
    ```csharp  
    private Geometry textGeometry;  
    private Grid commentGrid;  
    private static Brush brush;  
    private static Pen solidPen;  
    private static Pen dashPen;  
    ```  
  
5. Добавьте конструктор, который определяет Оформление комментария и добавляет соответствующий текст.  
  
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
  
6. Также реализуйте <xref:System.Windows.Controls.Panel.OnRender%2A> обработчик событий, который рисует Оформление.  
  
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
  
## <a name="adding-an-iwpftextviewcreationlistener"></a>Добавление Ивпфтекствиевкреатионлистенер  
 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>— Это часть компонента MEF, которую можно использовать для прослушивания событий создания.  
  
1. Добавьте файл класса в проект Комментадорнменттест и назовите его `Connector` .  
  
2. Добавьте следующие операторы `using`.  
  
    ```csharp  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Utilities;  
    ```  
  
3. Объявите класс, реализующий <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> , и экспортируйте его с помощью <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Text" и <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> объекта <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> . Атрибут типа содержимого определяет тип содержимого, к которому применяется компонент. Текстовый тип является базовым типом для всех типов файлов, не являющихся двоичными. Таким образом, почти каждое созданное текстовое представление будет иметь такой тип. Атрибут роли текстового представления определяет вид текстового представления, к которому применяется компонент. Роли представления текста документа обычно отображают текст, состоящий из строк и хранящийся в файле.  
  
     [!code-csharp[VSSDKMenuCommandTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkmenucommandtest/cs/commentadornmenttest/connector.cs#11)]
     [!code-vb[VSSDKMenuCommandTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkmenucommandtest/vb/commentadornmenttest/connector.vb#11)]  
  
4. Реализуйте <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> метод таким образом, чтобы он вызывал статическое `Create()` событие объекта `CommentAdornmentManager` .  
  
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
  
## <a name="defining-an-adornment-layer"></a>Определение слоя оформления  
 Чтобы добавить новый декоративный элемент, необходимо определить слой оформлений.  
  
#### <a name="to-define-an-adornment-layer"></a>Определение слоя оформления  
  
1. В `Connector` классе Объявите открытое поле типа <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition> и экспортируйте его с помощью объекта <xref:Microsoft.VisualStudio.Utilities.NameAttribute> , который задает уникальное имя для слоя оформления и объект <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> , определяющий отношение Z-порядка этого слоя оформления к другим слоям представления текста (текст, курсор и выделение).  
  
    ```csharp  
    [Export(typeof(AdornmentLayerDefinition))]  
    [Name("CommentAdornmentLayer")]  
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
    public AdornmentLayerDefinition commentLayerDefinition;  
  
    ```  
  
## <a name="providing-comment-adornments"></a>Предоставление оформлений комментариев  
 При определении оформления также реализуйте поставщик элементов комментария и диспетчер элементов комментариев. Поставщик оформлений комментариев сохраняет список оформлений комментариев, прослушивает <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> события в базовом текстовом буфере и удаляет декоративные элементы комментариев при удалении базового текста.  
  
1. Добавьте новый файл класса в проект Комментадорнменттест и назовите его `CommentAdornmentProvider` .  
  
2. Добавьте следующие операторы `using`.  
  
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
  
4. Добавьте закрытые поля для текстового буфера и список оформлений комментариев, связанных с буфером.  
  
    ```csharp  
    private ITextBuffer buffer;  
    private IList<CommentAdornment> comments = new List<CommentAdornment>();  
  
    ```  
  
5. Добавьте конструктор для `CommentAdornmentProvider` . Этот конструктор должен иметь закрытый доступ, так как экземпляр поставщика создается с помощью `Create()` метода. Конструктор добавляет `OnBufferChanged` обработчик событий в <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> событие.  
  
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
  
    ```csharp  
    private void OnBufferChanged(object sender, TextContentChangedEventArgs e)  
    {  
        //Make a list of all comments that have a span of at least one character after applying the change. There is no need to raise a changed event for the deleted adornments. The adornments are deleted only if a text change would cause the view to reformat the line and discard the adornments.  
        IList<CommentAdornment> keptComments = new List<CommentAdornment>(this.comments.Count);  
  
        foreach (CommentAdornment comment in this.comments)  
        {  
            Span span = comment.Span.GetSpan(e.After);  
            //if a comment does not span at least one character, its text was deleted.   
            if (span.Length != 0)  
            {  
                keptComments.Add(comment);  
            }  
        }  
  
        this.comments = keptComments;  
    }  
  
    ```  
  
     [!code-csharp[VSSDKMenuCommandTest#21](../snippets/csharp/VS_Snippets_VSSDK/vssdkmenucommandtest/cs/commentadornmenttest/commentadornmentprovider.cs#21)]
     [!code-vb[VSSDKMenuCommandTest#21](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkmenucommandtest/vb/commentadornmenttest/commentadornmentprovider.vb#21)]  
  
9. Добавьте объявление для `CommentsChanged` события.  
  
    ```csharp  
    public event EventHandler<CommentsChangedEventArgs> CommentsChanged;  
    ```  
  
10. Создайте `Add()` метод для добавления оформления.  
  
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
  
12. Добавьте `GetComments()` метод, который возвращает все комментарии в заданном диапазоне снимка.  
  
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
  
13. Добавьте класс с именем `CommentsChangedEventArgs` , как показано ниже.  
  
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
  
## <a name="managing-comment-adornments"></a>Управление оформлениями комментариев  
 Диспетчер декоративных элементов комментариев создает Оформление и добавляет его в слой оформления. Он прослушивает <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> события и, чтобы он мог переместить или удалить оформление. Он также прослушивает `CommentsChanged` событие, которое запускается поставщиком элементов комментариев при добавлении или удалении комментариев.  
  
1. Добавьте файл класса в проект Комментадорнменттест и назовите его `CommentAdornmentManager` .  
  
2. Добавьте следующие операторы `using`.  
  
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
  
4. Добавьте некоторые закрытые поля.  
  
    ```csharp  
    private readonly IWpfTextView view;  
    private readonly IAdornmentLayer layer;  
    private readonly CommentAdornmentProvider provider;  
    ```  
  
5. Добавьте конструктор, который подписывает руководителя к <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> событиям и, а также к `CommentsChanged` событию. Конструктор является закрытым, так как экземпляр диспетчера создается статическим `Create()` методом.  
  
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
  
6. Добавьте `Create()` метод, который получает поставщик, или при необходимости создает его.  
  
    ```csharp  
    public static CommentAdornmentManager Create(IWpfTextView view)  
    {  
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentManager>(delegate { return new CommentAdornmentManager(view); });  
    }  
    ```  
  
7. Добавьте `CommentsChanged` обработчик.  
  
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
  
8. Добавьте <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> обработчик.  
  
    ```csharp  
    private void OnClosed(object sender, EventArgs e)  
    {  
        this.provider.Detach();  
        this.view.LayoutChanged -= OnLayoutChanged;  
        this.view.Closed -= OnClosed;  
    }  
    ```  
  
9. Добавьте <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> обработчик.  
  
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
  
     [!code-csharp[VSSDKMenuCommandTest#35](../snippets/csharp/VS_Snippets_VSSDK/vssdkmenucommandtest/cs/commentadornmenttest/commentadornmentmanager.cs#35)]
     [!code-vb[VSSDKMenuCommandTest#35](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkmenucommandtest/vb/commentadornmenttest/commentadornmentmanager.vb#35)]  
  
## <a name="using-the-menu-command-to-add-the-comment-adornment"></a>Использование команды меню для добавления оформления комментария  
 Можно использовать команду меню для создания оформления комментария путем реализации `MenuItemCallback` метода VSPackage.  
  
1. Добавьте в проект Менукоммандтест следующие ссылки:  
  
    - Microsoft. VisualStudio. TextManager. Interop  
  
    - Microsoft. VisualStudio. Editor  
  
    - Microsoft. VisualStudio. Text. UI. WPF  
  
2. Откройте файл AddAdornment.cs и добавьте следующие `using` инструкции.  
  
    ```csharp  
    using Microsoft.VisualStudio.TextManager.Interop;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Editor;  
    using CommentAdornmentTest;  
    ```  
  
3. Удалите метод метода ShowMessageBox () и добавьте следующий обработчик команд.  
  
    ```csharp  
    private void AddAdornmentHandler(object sender, EventArgs e)  
    {  
    }  
    ```  
  
4. Добавьте код для получения активного представления. Чтобы получить активное значение, необходимо получить `SVsTextManager` оболочку Visual Studio Shell `IVsTextView` .  
  
    ```csharp  
    private void AddAdornmentHandler(object sender, EventArgs e)  
    {  
        IVsTextManager txtMgr = (IVsTextManager)ServiceProvider.GetService(typeof(SVsTextManager));  
        IVsTextView vTextView = null;  
        int mustHaveFocus = 1;  
        txtMgr.GetActiveView(mustHaveFocus, null, out vTextView);  
    }  
    ```  
  
5. Если это текстовое представление является экземпляром текстового представления редактора, его можно привести к <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> интерфейсу, а затем получить <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> и связанный с ним объект <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> . Используйте <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> для вызова `Connector.Execute()` метода, который получает поставщик оформлений комментария и добавляет Оформление. Обработчик команд теперь должен выглядеть следующим образом:  
  
    ```csharp  
    private void AddAdornmentHandler(object sender, EventArgs e)  
    {  
        IVsTextManager txtMgr = (IVsTextManager)ServiceProvider.GetService(typeof(SVsTextManager));  
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
  
6. Задайте метод Аддадорнменсандлер в качестве обработчика для команды Аддадорнмент в конструкторе Аддадорнмент.  
  
    ```csharp  
    private AddAdornment(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException(nameof(package));  
        }  
  
        this.package = package;  
  
        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
        if (commandService != null)  
        {  
            CommandID menuCommandID = new CommandID(MenuGroup, CommandId);  
            EventHandler eventHandler = this.AddAdornmentHandler;  
            MenuCommand menuItem = new MenuCommand(eventHandler, menuCommandID);  
            commandService.AddCommand(menuItem);  
        }  
    }  
    ```  
  
## <a name="building-and-testing-the-code"></a>Сборка и тестирование кода  
  
1. Постройте решение и запустите отладку. Должен отобразиться экспериментальный экземпляр.  
  
2. Создание текстового файла. Введите текст и выберите его.  
  
3. В меню **Сервис** выберите команду **вызвать добавление оформления**. В правой части текстового окна должно отобразиться всплывающее окно, которое должно содержать текст, напоминающий следующий текст.  
  
     йоурусернаме  
  
     Фаурскоре...  
  
## <a name="see-also"></a>См. также:  
 [Пошаговое руководство. Связывание типа контента с расширением имени файла](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
