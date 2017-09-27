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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 1096b04fee06415e65a93b0ecd8a6257de64edfc
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="walkthrough-displaying-light-bulb-suggestions"></a>Пошаговое руководство: Отображение лампочки предложения
Лампочки являются значков, используемых в редакторе Visual Studio, развернуть, чтобы отобразить набор действий, например исправления для проблем, определяемый встроенных анализаторов или рефакторинга кода.  
  
 В редакторе Visual C# и Visual Basic можно также использовать платформой компилятора .NET («Roslyn») для записи и пакетов собственные анализаторов с действиями, которые автоматически отображают лампочки. Дополнительные сведения:  
  
-   [Практическое руководство: Запись C# диагностики и исправления кода](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-C%23-Analyzer-and-Code-Fix)  
  
-   [Практическое руководство: Запись в Visual Basic диагностики и исправления кода](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-Visual-Basic-Analyzer-and-Code-Fix)  
  
 Других языках, например C++ также обеспечивают лампочки некоторые Быстрые действия, например, чтобы создать реализацию заглушки этой функции.  
  
 Вот, как выглядит лампочки. В проекте Visual Basic или Visual C# красная волнистая линия отображается под именем переменной при является недопустимым. При наведении мыши недопустимым идентификатором, лампочка отображается рядом с курсором.  
  
 ![лампочка](../extensibility/media/lightbulb.png "лампочки")  
  
 Если щелкнуть стрелку вниз лампочка, набор предлагаемых действий отображается вместе со Предварительный просмотр выбранного действия. В этом случае он отображается изменений, внесенных в код при выполнении действия.  
  
 ![Предварительный просмотр лампочки](../extensibility/media/lightbulbpreview.png "LightBulbPreview")  
  
 Лампочки можно использовать для предоставления собственных предложенные действия. Например можно предоставить перемещать открывающих фигурных скобок на новую строку, или переместить их в конец предыдущей строки. Следующее пошаговое руководство демонстрирует создание лампочка, которая отображается в текущем слове и имеет два предлагаемых действия: **преобразовать в верхний регистр** и **преобразовать в нижний регистр**.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, не установить пакет SDK для Visual Studio из центра загрузки Майкрософт. Он включен в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Создание проекта Managed Extensibility Framework (MEF)  
  
1.  Создайте проект VSIX C#. (В **новый проект** диалогового окна выберите **Visual C# / Extensibility**, затем **проект VSIX**.) Присвойте решению имя `LightBulbTest`.  
  
2.  Добавить **классификатора редактора** шаблона элемента в проект. Дополнительные сведения см. в разделе [создания расширения с помощью шаблона элемента редактор](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Удалите файлы существующих классов.  
  
4.  Добавьте следующую ссылку в проект и задайте **Копировать локально** для `False`:  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
5.  Добавьте новый файл класса и назовите его **LightBulbTest**.  
  
6.  Добавьте следующие операторы using:  
  
    ```csharp  
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
  
## <a name="implementing-the-light-bulb-source-provider"></a>Реализация поставщика источника лампочки  
  
1.  В файле класса LightBulbTest.cs удалите класс LightBulbTest. Добавьте класс с именем **TestSuggestedActionsSourceProvider** , реализующий <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>. Экспортировать его с именем **предлагаемые действия теста** и <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> «Text».  
  
    ```csharp  
    [Export(typeof(ISuggestedActionsSourceProvider))]  
    [Name("Test Suggested Actions")]  
    [ContentType("text")]  
    internal class TestSuggestedActionsSourceProvider : ISuggestedActionsSourceProvider  
    ```  
  
2.  Внутри класса поставщика источника, Импорт <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> и добавить его в качестве свойства.  
  
    ```csharp  
    [Import(typeof(ITextStructureNavigatorSelectorService))]  
    internal ITextStructureNavigatorSelectorService NavigatorService { get; set; }  
    ```  
  
3.  Реализуйте <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider.CreateSuggestedActionsSource%2A> метод для возврата <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> объекта. Мы рассмотрим источника в следующем разделе.  
  
    ```csharp  
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
 Предлагаемое действие источника отвечает за сбор набор предлагаемых действий и добавляя их в нужном контексте. В этом случае контекст текущего слова и предлагаются действия **UpperCaseSuggestedAction** и **LowerCaseSuggestedAction**, который будет рассматриваться в следующем разделе.  
  
1.  Добавьте класс **TestSuggestedActionsSource** , реализующий <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>.  
  
    ```csharp  
    internal class TestSuggestedActionsSource : ISuggestedActionsSource  
    ```  
  
2.  Добавьте закрытые поля только для чтения для поставщика источника предлагаемое действие, буфер текста и представлением текста.  
  
    ```csharp  
    private readonly TestSuggestedActionsSourceProvider m_factory;  
    private readonly ITextBuffer m_textBuffer;  
    private readonly ITextView m_textView;  
    ```  
  
3.  Добавьте конструктор, который задает закрытые поля.  
  
    ```csharp  
    public TestSuggestedActionsSource(TestSuggestedActionsSourceProvider testSuggestedActionsSourceProvider, ITextView textView, ITextBuffer textBuffer)  
    {  
        m_factory = testSuggestedActionsSourceProvider;  
        m_textBuffer = textBuffer;  
        m_textView = textView;  
    }  
    ```  
  
4.  Добавьте закрытый метод, возвращающий слова под курсором в данный момент. Следующий метод ищет в текущем положении курсора и запрашивает экстент слова навигатор структуры текста. Если курсор находится в слове, <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> возвращается в выходной параметр; в противном случае `out` параметр `null` , а метод возвращает `false`.  
  
    ```csharp  
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
  
5.  Выполните метод <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.HasSuggestedActionsAsync%2A>. Редактор вызывает этот метод, чтобы определить, следует ли отображать лампочка. Этот вызов выполняется довольно часто, например всякий раз, когда курсор перемещается из одной строки в другую или при наведении указателя мыши на ошибки волнистой линией. Он является асинхронным, чтобы разрешить другие операции пользовательского интерфейса для выполнения то время как работает этот метод. Поэтому в большинстве случаев этот метод должен выполнять синтаксический анализ и анализ текущей строки, обработка может занять некоторое время.  
  
     В нашем реализации его асинхронно получает <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> и определяет, является ли область большое значение, т. е. имеет ли он некоторый текст, отличный от пробела.  
  
    ```csharp  
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
  
6.  Реализуйте <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.GetSuggestedActions%2A> метод, возвращающий массив <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> объектов, которые содержат различные <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction> объектов. Этот метод вызывается, когда она открыта лампочка.  
  
    > [!WARNING]
    >  Следует убедиться в том, реализации `HasSuggestedActionsAsync()` и `GetSuggestedActions()` являются постоянной; это, если `HasSuggestedActionsAsync()` возвращает `true`, затем `GetSuggestedActions()` должны иметь некоторые действия для отображения. Во многих случаях `HasSuggestedActionsAsync()` вызывается непосредственно перед вызовом `GetSuggestedActions()`, но это не. Например, если пользователь вызывает действия лампочка, нажав клавишу (CTRL +.) только `GetSuggestedActions()` вызывается.  
  
    ```csharp  
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
  
7.  Определение `SuggestedActionsChanged` событий.  
  
    ```csharp  
    public event EventHandler<EventArgs> SuggestedActionsChanged;  
    ```  
  
8.  Чтобы завершить реализацию, добавьте реализации для `Dispose()` и `TryGetTelemetryId()` методы. Мы не хотим сделать телеметрии, поэтому просто возвращает значение false и равным пустой GUID.  
  
    ```csharp  
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
  
## <a name="implementing-light-bulb-actions"></a>Реализация действий лампочки  
  
1.  В проекте добавьте ссылку на Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll и набор **Копировать локально** для `False`.  
  
2.  Создайте два класса с именем первого `UpperCaseSuggestedAction` и второй с именем `LowerCaseSuggestedAction`. В обоих классах реализован интерфейс <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction>.  
  
    ```csharp  
    internal class UpperCaseSuggestedAction : ISuggestedAction   
    internal class LowerCaseSuggestedAction : ISuggestedAction  
    ```  
  
     Эти два класса похожи за тем исключением, что один из них вызывает <xref:System.String.ToUpper%2A> и другие вызовы <xref:System.String.ToLower%2A>. В дальнейших шагах рассматривается создание класса для действия преобразования в верхний регистр, но вам необходимо реализовать оба класса. Используйте инструкции по реализации действия преобразования в верхний регистр в качестве шаблона для реализации действия преобразования в нижний регистр.  
  
3.  Добавьте следующие операторы using для этих классов:  
  
    ```csharp  
    using Microsoft.VisualStudio.Imaging.Interop;  
    using System.Windows;  
    using System.Windows.Controls;  
    using System.Windows.Documents;  
    using System.Windows.Media;  
  
    ```  
  
4.  Объявите набор закрытых полей.  
  
    ```csharp  
    private ITrackingSpan m_span;  
    private string m_upper;  
    private string m_display;  
    private ITextSnapshot m_snapshot;  
    ```  
  
5.  Добавьте конструктор, который задает поля.  
  
    ```csharp  
    public UpperCaseSuggestedAction(ITrackingSpan span)  
    {  
        m_span = span;  
        m_snapshot = span.TextBuffer.CurrentSnapshot;  
        m_upper = span.GetText(m_snapshot).ToUpper();  
        m_display = string.Format("Convert '{0}' to upper case", span.GetText(m_snapshot));  
    }  
    ```  
  
6.  Реализация <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetPreviewAsync%2A> метода, потому что он отображается как действия предварительной версии.  
  
    ```csharp  
    public Task<object> GetPreviewAsync(CancellationToken cancellationToken)  
    {  
        var textBlock = new TextBlock();  
        textBlock.Padding = new Thickness(5);  
        textBlock.Inlines.Add(new Run() { Text = m_upper });  
        return Task.FromResult<object>(textBlock);  
    }  
    ```  
  
7.  Реализуйте <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetActionSetsAsync%2A> метод, возвращающий пустой <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> перечисления.  
  
    ```csharp  
    public Task<IEnumerable<SuggestedActionSet>> GetActionSetsAsync(CancellationToken cancellationToken)  
    {  
        return Task.FromResult<IEnumerable<SuggestedActionSet>>(null);  
    }  
    ```  
  
8.  Реализуйте свойства указанным ниже образом.  
  
    ```csharp  
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
  
9. Реализация <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.Invoke%2A> метода, заменив текст в диапазоне в его эквивалент в верхнем регистре.  
  
    ```csharp  
    public void Invoke(CancellationToken cancellationToken)  
    {  
        m_span.TextBuffer.Replace(m_span.GetSpan(m_snapshot), m_upper);  
    }  
    ```  
  
    > [!WARNING]
    >  Действие лампочки **Invoke** метод не должен отображать пользовательский Интерфейс.  Если действие подключить новый пользовательский Интерфейс (например предварительного просмотра или выбора диалогового окна), не имеют пользовательского интерфейса, непосредственно из пользовательского **Invoke** метода, но вместо этого расписания для отображения пользовательского интерфейса после возвращения из **Invoke**.  
  
10. Чтобы завершить реализацию, добавьте `Dispose()` и `TryGetTelemetryId()` методы.  
  
    ```csharp  
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
  
11. Не забудьте сделать то же самое для `LowerCaseSuggestedAction` изменение отображения текста на «Преобразование «{0}» в нижний регистр» и вызов <xref:System.String.ToUpper%2A> для <xref:System.String.ToLower%2A>.  
  
## <a name="building-and-testing-the-code"></a>Сборка и тестирование кода  
 Чтобы проверить код, выполните сборку решения LightBulbTest и запустите его в экспериментальном экземпляре.  
  
1.  Постройте решение.  
  
2.  При запуске этого проекта в отладчике создается второй экземпляр Visual Studio.  
  
3.  Создайте текстовый файл и введите любой текст. Вы увидите лампочки слева от текста.  
  
     ![Тестирование лампочки](../extensibility/media/testlightbulb.png "TestLIghtBulb")  
  
4.  Укажите лампочка. Вы увидите стрелка вниз.  
  
5.  При нажатии кнопки лампочка, два предлагаемых действия следует отображать вместе со Предварительный просмотр выбранного действия.  
  
     ![Тестирование лампочки, расширенное](../extensibility/media/testlightbulbexpanded.gif "TestLIghtBulbExpanded")  
  
6.  Если выбрать первое действие, все символы текущего слова должны преобразоваться в верхний регистр. Если выбрать второе действие, все символы должны преобразоваться в нижний регистр.  
  
