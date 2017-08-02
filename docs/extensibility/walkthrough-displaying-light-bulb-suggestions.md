---
title: "Пошаговое руководство: Отображение лампочки предложения | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 99e5566d-450e-4660-9bca-454e1c056a02
caps.latest.revision: 16
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: e3838b7f9161991840bc5498f66abcfd3ce2b248
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-displaying-light-bulb-suggestions"></a>Пошаговое руководство: Отображение лампочки предложения
Лампочки являются значков, используемых в редакторе Visual Studio, разверните для отображения набора действий, например исправления для проблем, анализаторы встроенный код или переработки кода.  
  
 В редакторах Visual C# и Visual Basic можно также использовать платформы компилятора .NET («Roslyn») для записи и упаковать собственную анализаторов кода с помощью действий, отображающих лампочки автоматически. Дополнительные сведения:  
  
-   [Практическое руководство: Запись C# диагностики и исправления кода](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-C%23-Analyzer-and-Code-Fix)  
  
-   [Практическое руководство: Запись в Visual Basic диагностики и исправления кода](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-Visual-Basic-Analyzer-and-Code-Fix)  
  
 Другие языки, например C++ также обеспечивают лампочки некоторые быстрых действий, например предложение, чтобы создать реализацию заглушки этой функции.  
  
 Вот, как выглядит лампочка. В проекте Visual Basic или Visual C# красной волнистой линией отображается под именем переменной при недопустимом. При наведении недопустимый идентификатор лампочка отображается рядом с курсором.  
  
 ![лампочка](~/docs/extensibility/media/lightbulb.png "лампочки")  
  
 Если щелкнуть стрелку вниз лампочка, предлагаемые действия отображается вместе с Предварительный просмотр выбранного действия. В этом случае показаны изменения, которые будут внесены в код при выполнении действия.  
  
 ![Предварительный просмотр лампочки](~/docs/extensibility/media/lightbulbpreview.png "LightBulbPreview")  
  
 Лампочки можно использовать для предоставления предложенные действия. Например можно предоставить перемещать Открытие фигурных скобок для новой строки или переместить их в конец предыдущей строки. Следующем пошаговом руководстве демонстрируется создание лампочка, которая отображается на текущее слово и имеет два предлагаемых действий: **преобразовать в верхний регистр** и **преобразовать в нижний регистр**.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, не установить пакет SDK для Visual Studio из центра загрузки. Она будет включена в качестве дополнительного компонента в установку Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [установка Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Создание проекта Managed Extensibility Framework (MEF)  
  
1.  Создайте проект VSIX C#. (В **новый проект** диалогового окна выберите **Visual C# и расширяемость**, затем **проект VSIX**.) Присвойте решению имя `LightBulbTest`.  
  
2.  Добавить **классификатора редактор** шаблона элемента в проект. Дополнительные сведения см. в разделе [создания расширения с помощью редактора шаблона элемента](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Удалите файлы существующих классов.  
  
4.  Добавьте следующую ссылку в проект и задайте **Копировать локально** в `False`:  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
5.  Добавьте новый файл класса и назовите его **LightBulbTest**.  
  
6.  Добавьте следующие операторы using:  
  
    ```c#  
    using System;  
    using System.Linq;  
    using System.Collections.Generic;  
    using System.Threading.Tasks;  
    using Microsoft.VisualStudio.Language.Intellisense;  
    using Microsoft.VisualStudio.Text;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Text.Operations;  
    using Microsoft.VisualStudio.Utilities;  
    using System.ComponentModel.Composition;  
    using System.Threading;  
  
    ```  
  
## <a name="implementing-the-light-bulb-source-provider"></a>Реализация поставщика источника лампочка  
  
1.  В файле класса LightBulbTest.cs удалите класс LightBulbTest. Добавьте класс с именем **TestSuggestedActionsSourceProvider** , реализующий <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>.</xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider> Экспортировать его с именем **предлагаемые действия теста** и <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>«текст».</xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>  
  
    ```c#  
    [Export(typeof(ISuggestedActionsSourceProvider))]  
    [Name("Test Suggested Actions")]  
    [ContentType("text")]  
    internal class TestSuggestedActionsSourceProvider : ISuggestedActionsSourceProvider  
    ```  
  
2.  В классе поставщика источника импорта <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>и добавить его в качестве свойства.</xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>  
  
    ```c#  
    [Import(typeof(ITextStructureNavigatorSelectorService))]  
    internal ITextStructureNavigatorSelectorService NavigatorService { get; set; }  
    ```  
  
3.  Реализация <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider.CreateSuggestedActionsSource%2A>метода, возвращающего <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>объекта.</xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> </xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider.CreateSuggestedActionsSource%2A> Мы обсудим источника в следующем разделе.  
  
    ```c#  
    public ISuggestedActionsSource CreateSuggestedActionsSource(ITextView textView, ITextBuffer textBuffer)  
    {  
        if (textBuffer == null && textView == null)  
        {  
            return null;  
        }  
        return new TestSuggestedActionsSource(this, textView, textBuffer);  
    }  
    ```  
  
## <a name="implementing-the-isuggestedactionsource"></a>Реализация ISuggestedActionSource  
 Рекомендуемое действие источника отвечает за сбор набор действий, предлагаемое и добавляя их в нужном контексте. В этом случае контекст текущего слова, и рекомендуемые действия, которые **UpperCaseSuggestedAction** и **LowerCaseSuggestedAction**, который будет рассматриваться в следующем разделе.  
  
1.  Добавьте класс **TestSuggestedActionsSource** , реализующий <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>.</xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>  
  
    ```c#  
    internal class TestSuggestedActionsSource : ISuggestedActionsSource  
    ```  
  
2.  Добавьте закрытые поля только для чтения для поставщика источника предлагаемое действие, текстовый буфер и представления текста.  
  
    ```c#  
    private readonly TestSuggestedActionsSourceProvider m_factory;  
    private readonly ITextBuffer m_textBuffer;  
    private readonly ITextView m_textView;  
    ```  
  
3.  Добавьте конструктор, который задает закрытые поля.  
  
    ```c#  
    public TestSuggestedActionsSource(TestSuggestedActionsSourceProvider testSuggestedActionsSourceProvider, ITextView textView, ITextBuffer textBuffer)  
    {  
        m_factory = testSuggestedActionsSourceProvider;  
        m_textBuffer = textBuffer;  
        m_textView = textView;  
    }  
    ```  
  
4.  Добавьте закрытый метод, который возвращает word, который находится под курсором. Следующий метод выглядит в текущем положении курсора и запрашивает экстент слова навигатор структуру текста. Если курсор находится в word, <xref:Microsoft.VisualStudio.Text.Operations.TextExtent>возвращается в выходной параметр; в противном случае `out` параметр `null` , а метод возвращает `false`.</xref:Microsoft.VisualStudio.Text.Operations.TextExtent>  
  
    ```c#  
    private bool TryGetWordUnderCaret(out TextExtent wordExtent)  
    {  
        ITextCaret caret = m_textView.Caret;  
        SnapshotPoint point;  
  
        if (caret.Position.BufferPosition > 0)  
        {  
            point = caret.Position.BufferPosition - 1;  
        }  
        else  
        {  
            wordExtent = default(TextExtent);  
            return false;  
        }  
  
        ITextStructureNavigator navigator = m_factory.NavigatorService.GetTextStructureNavigator(m_textBuffer);  
  
        wordExtent = navigator.GetExtentOfWord(point);  
        return true;  
    }  
    ```  
  
5.  Реализация <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.HasSuggestedActionsAsync%2A>метода.</xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.HasSuggestedActionsAsync%2A> Редактор вызывает этот метод, чтобы узнать, следует ли отображать лампочка. Этот вызов выполняется довольно часто, например всякий раз, когда курсор перемещается из одной строки в другую или при наведении указателя мыши на волнистую линию ошибки. Он является асинхронным, чтобы разрешить другие операции пользовательского интерфейса для выполнения то время как этот метод работает. Поэтому в большинстве случаев этот метод должен выполнять синтаксический анализ и анализ текущей строки, обработка может занять некоторое время.  
  
     В нашей реализации он асинхронно получает <xref:Microsoft.VisualStudio.Text.Operations.TextExtent>и определяет, является ли область значительные, т. е. наличие какой-либо текст, отличные от пробельных.</xref:Microsoft.VisualStudio.Text.Operations.TextExtent>  
  
    ```c#  
    public Task<bool> HasSuggestedActionsAsync(ISuggestedActionCategorySet requestedActionCategories, SnapshotSpan range, CancellationToken cancellationToken)  
    {  
        return Task.Factory.StartNew(() =>  
        {  
            TextExtent extent;  
            if (TryGetWordUnderCaret(out extent))  
            {  
                // don't display the action if the extent has whitespace  
                return extent.IsSignificant;  
              }  
            return false;  
        });  
    }  
    ```  
  
6.  Реализация <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.GetSuggestedActions%2A>метода, который возвращает массив <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet>объектов, содержащих разные <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction>объектов.</xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction> </xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> </xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.GetSuggestedActions%2A> Этот метод вызывается, когда развернута лампочка.  
  
    > [!WARNING]
    >  Следует убедиться, что реализаций `HasSuggestedActionsAsync()` и `GetSuggestedActions()` являются постоянной; это, если `HasSuggestedActionsAsync()` возвращает `true`, затем `GetSuggestedActions()` должны иметь некоторые действия для отображения. Во многих случаях `HasSuggestedActionsAsync()` вызывается непосредственно перед вызовом `GetSuggestedActions()`, но это не. Например, если пользователь вызывает действия лампочка, нажав клавишу (CTRL +.) только `GetSuggestedActions()` вызывается.  
  
    ```c#  
    public IEnumerable<SuggestedActionSet> GetSuggestedActions(ISuggestedActionCategorySet requestedActionCategories, SnapshotSpan range, CancellationToken cancellationToken)  
    {  
        TextExtent extent;  
        if (TryGetWordUnderCaret(out extent) && extent.IsSignificant)  
        {  
            ITrackingSpan trackingSpan = range.Snapshot.CreateTrackingSpan(extent.Span, SpanTrackingMode.EdgeInclusive);  
            var upperAction = new UpperCaseSuggestedAction(trackingSpan);  
            var lowerAction = new LowerCaseSuggestedAction(trackingSpan);  
            return new SuggestedActionSet[] { new SuggestedActionSet(new ISuggestedAction[] { upperAction, lowerAction }) };  
        }  
        return Enumerable.Empty<SuggestedActionSet>();  
    }   
    ```  
  
7.  Определение `SuggestedActionsChanged` события.  
  
    ```c#  
    public event EventHandler<EventArgs> SuggestedActionsChanged;  
    ```  
  
8.  Для завершения реализации, добавьте реализации для `Dispose()` и `TryGetTelemetryId()` методы. Мы не хотим сделать телеметрии, поэтому просто возвращает значение false и равным пустой идентификатор GUID.  
  
    ```c#  
    public void Dispose()  
    {  
    }  
  
    public bool TryGetTelemetryId(out Guid telemetryId)  
    {  
        // This is a sample provider and doesn't participate in LightBulb telemetry  
        telemetryId = Guid.Empty;  
        return false;  
    }  
    ```  
  
## <a name="implementing-light-bulb-actions"></a>Реализация действия лампочка  
  
1.  В проекте добавьте ссылку на Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll и набор **Копировать локально** в `False`.  
  
2.  Создайте два класса с именем первого `UpperCaseSuggestedAction` и второй с именем `LowerCaseSuggestedAction`. Оба класса реализуют <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction>.</xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction>  
  
    ```c#  
    internal class UpperCaseSuggestedAction : ISuggestedAction   
    internal class LowerCaseSuggestedAction : ISuggestedAction  
    ```  
  
     Оба класса индивидуальны, за исключением того, что один вызов <xref:System.String.ToUpper%2A>и другие вызовы <xref:System.String.ToLower%2A>.</xref:System.String.ToLower%2A> </xref:System.String.ToUpper%2A> В дальнейших шагах рассматривается создание класса для действия преобразования в верхний регистр, но вам необходимо реализовать оба класса. Используйте инструкции по реализации действия преобразования в верхний регистр в качестве шаблона для реализации действия преобразования в нижний регистр.  
  
3.  Добавьте следующие операторы using для этих классов:  
  
    ```c#  
    using Microsoft.VisualStudio.Imaging.Interop;  
    using System.Windows;  
    using System.Windows.Controls;  
    using System.Windows.Documents;  
    using System.Windows.Media;  
  
    ```  
  
4.  Объявите набор закрытых полей.  
  
    ```c#  
    private ITrackingSpan m_span;  
    private string m_upper;  
    private string m_display;  
    private ITextSnapshot m_snapshot;  
    ```  
  
5.  Добавьте конструктор, который задает поля.  
  
    ```c#  
    public UpperCaseSuggestedAction(ITrackingSpan span)  
    {  
        m_span = span;  
        m_snapshot = span.TextBuffer.CurrentSnapshot;  
        m_upper = span.GetText(m_snapshot).ToUpper();  
        m_display = string.Format("Convert '{0}' to upper case", span.GetText(m_snapshot));  
    }  
    ```  
  
6.  Реализация <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetPreviewAsync%2A>метода, так что он отображает Просмотр действий.</xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetPreviewAsync%2A>  
  
    ```c#  
    public Task<object> GetPreviewAsync(CancellationToken cancellationToken)  
    {  
        var textBlock = new TextBlock();  
        textBlock.Padding = new Thickness(5);  
        textBlock.Inlines.Add(new Run() { Text = m_upper });  
        return Task.FromResult<object>(textBlock);  
    }  
    ```  
  
7.  Реализуйте <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetActionSetsAsync%2A>метод, возвращающий пустой <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet>перечисления.</xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> </xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetActionSetsAsync%2A>  
  
    ```c#  
    public Task<IEnumerable<SuggestedActionSet>> GetActionSetsAsync(CancellationToken cancellationToken)  
    {  
        return Task.FromResult<IEnumerable<SuggestedActionSet>>(null);  
    }  
    ```  
  
8.  Реализуйте свойства указанным ниже образом.  
  
    ```c#  
    public bool HasActionSets  
    {  
        get { return false; }  
    }  
    public string DisplayText  
    {  
        get { return m_display; }  
    }  
    public ImageMoniker IconMoniker  
    {  
       get { return default(ImageMoniker); }  
    }  
    public string IconAutomationText  
    {  
        get  
        {  
            return null;  
        }  
    }  
    public string InputGestureText  
    {  
        get  
        {  
            return null;  
        }  
    }  
    public bool HasPreview  
    {  
        get { return true; }  
    }  
    ```  
  
9. Реализация <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.Invoke%2A>метода, заменив текст в диапазоне его эквивалент в верхнем регистре.</xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.Invoke%2A>  
  
    ```c#  
    public void Invoke(CancellationToken cancellationToken)  
    {  
        m_span.TextBuffer.Replace(m_span.GetSpan(m_snapshot), m_upper);  
    }  
    ```  
  
    > [!WARNING]
    >  Действие лампочка **Invoke** метод не должен отображать пользовательский Интерфейс.  Если действие открыть новый пользовательский Интерфейс (например окно предварительного просмотра или выбора), не имеют пользовательского интерфейса непосредственно из пользовательского **Invoke** метода, но вместо этого планирование для отображения пользовательского интерфейса после возврата из **Invoke**.  
  
10. Для завершения реализации, добавьте `Dispose()` и `TryGetTelemetryId()` методы.  
  
    ```c#  
    public void Dispose()  
    {  
    }  
  
    public bool TryGetTelemetryId(out Guid telemetryId)  
    {  
        // This is a sample action and doesn't participate in LightBulb telemetry  
        telemetryId = Guid.Empty;  
        return false;  
    }  
    ```  
  
11. Не забудьте сделать то же самое для `LowerCaseSuggestedAction` изменение отображения текста «Преобразование «{0}» нижний регистр» и вызов <xref:System.String.ToUpper%2A> <xref:System.String.ToLower%2A>.</xref:System.String.ToLower%2A> </xref:System.String.ToUpper%2A>  
  
## <a name="building-and-testing-the-code"></a>Сборка и тестирование кода  
 Чтобы проверить код, создания LightBulbTest решения и запустите его в экспериментальном экземпляре.  
  
1.  Постройте решение.  
  
2.  При запуске этого проекта в отладчике создается второй экземпляр Visual Studio.  
  
3.  Создайте текстовый файл и введите любой текст. Вы должны увидеть лампочка слева от текста.  
  
     ![Тестирование лампочки](~/docs/extensibility/media/testlightbulb.png "TestLIghtBulb")  
  
4.  Укажите лампочка. Вы должны увидеть стрелку вниз.  
  
5.  При нажатии кнопки лампочка, предлагаются два действия должен отображаться, вместе с предварительной версии выбранного действия.  
  
     ![Тестирование лампочки, расширенное](~/docs/extensibility/media/testlightbulbexpanded.gif "TestLIghtBulbExpanded")  
  
6.  Если выбрать первое действие, все символы текущего слова должны преобразоваться в верхний регистр. Если выбрать второе действие, все символы должны преобразоваться в нижний регистр.
