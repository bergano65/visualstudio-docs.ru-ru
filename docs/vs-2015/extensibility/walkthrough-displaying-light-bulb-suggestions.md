---
title: 'Пошаговое руководство: Отображение предложений лампочки | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 99e5566d-450e-4660-9bca-454e1c056a02
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 34ce6854c5af256c9a4fde35340414b6b2de640f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49252503"
---
# <a name="walkthrough-displaying-light-bulb-suggestions"></a>Пошаговое руководство. Отображение предложений лампочки
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Лампочки являются значков, используемых в редакторе Visual Studio, развернуть, чтобы отобразить набор действий, например исправления для проблем, обозначенных в анализаторов кода, встроенные или рефакторинга кода.  
  
 В редакторах Visual C# и Visual Basic можно также использовать платформы компилятора .NET («Roslyn») для записи и упаковки собственные анализаторы кода с действиями, которые автоматически отображают лампочки. Дополнительные сведения:  
  
-   [Практическое руководство: Написание C# Диагностика и исправление кода](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-C%23-Analyzer-and-Code-Fix)  
  
-   [Практическое руководство: Написание Visual Basic Диагностика и исправление кода](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-Visual-Basic-Analyzer-and-Code-Fix)  
  
 Другие языки, например C++ также предоставляют лампочки для некоторых быстрых действий, например чтобы создать реализацию заглушки этой функции.  
  
 Вот, как выглядит лампочка. В проекте Visual Basic или Visual C# красная волнистая линия отображается под именем переменной при не допускается. При наведении указателя мыши недопустимый идентификатор, лампочка отображается рядом с курсором.  
  
 ![лампочки](../extensibility/media/lightbulb.png "LightBulb")  
  
 Если щелкнуть стрелку вниз в «лампочку», набор предлагаемых действий отображается вместе с Предварительный просмотр выбранного действия. В этом случае он показывает изменений, внесенных в код при выполнении действия.  
  
 ![Предварительный просмотр лампочки](../extensibility/media/lightbulbpreview.png "LightBulbPreview")  
  
 Лампочки можно использовать для предоставления собственных предлагаемые действия. Например можно предоставить перемещать, открыв фигурные скобки на новую строку или переместите их в конце предыдущей строки. Следующего пошагового руководства демонстрируется создание лампочка, которая отображается в текущем слове и имеет два предлагаемых действия: **преобразовать в верхний регистр** и **преобразовать в нижний регистр**.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, не следует устанавливать пакет SDK для Visual Studio из центра загрузки. Она будет включена в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [установка Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Создание проекта Managed Extensibility Framework (MEF)  
  
1.  Создайте проект VSIX C#. (В **новый проект** диалоговом окне выберите **Visual C# / Extensibility**, затем **проект VSIX**.) Назовите решение `LightBulbTest`.  
  
2.  Добавить **классификатора редактора** шаблона элемента в проект. Дополнительные сведения см. в разделе [создание расширения с помощью шаблона элемента редактора](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
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
  
1.  В файле класса LightBulbTest.cs удаления LightBulbTest класса. Добавьте класс с именем **TestSuggestedActionsSourceProvider** , реализующий <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>. Экспортируйте его с именем **предлагаемые действия теста** и <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> «текст».  
  
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
  
3.  Реализуйте <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider.CreateSuggestedActionsSource%2A> метод для возврата <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> объекта. Мы обсудим источнику в следующем разделе.  
  
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
 Источник предлагаемое действие отвечает за сбор набор предлагаемые действия и добавлять их в правильном контексте. В этом случае контекст текущего слова и предлагаемые действия **UpperCaseSuggestedAction** и **LowerCaseSuggestedAction**, который будет рассматриваться в следующем разделе.  
  
1.  Добавьте класс **TestSuggestedActionsSource** , реализующий <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>.  
  
    ```csharp  
    internal class TestSuggestedActionsSource : ISuggestedActionsSource  
    ```  
  
2.  Добавьте закрытые поля только для чтения для поставщика источника предлагаемое действие, текстового буфера и представления текста.  
  
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
  
4.  Добавьте закрытый метод, который возвращает слово, находящейся под курсором. Следующий метод ищет в текущем положении курсора и запрашивает навигатором по структуре текста экстент слова. Если курсор находится на слова, <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> возвращается в выходной параметр; в противном случае `out` параметр `null` и метод возвращает `false`.  
  
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
  
5.  Выполните метод <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.HasSuggestedActionsAsync%2A>. Редактор вызывает этот метод, чтобы узнать, следует ли отображать лампочки. Этот вызов выполняется довольно часто, например, каждый раз, когда курсор перемещается из одной строки в другую или при наведении мыши на ошибку волнистой линией. Он является асинхронным, чтобы разрешить другие операции пользовательского интерфейса для выполнения то время как этот метод работает. Поэтому в большинстве случаев этот метод должен выполнять синтаксический анализ и анализа текущей строки, обработка может занять некоторое время.  
  
     В нашей реализации он асинхронно получает <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> и определяет, является ли экстент значительные, т. е. имеет ли он некоторый текст, отличный от пробела.  
  
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
  
6.  Реализуйте <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.GetSuggestedActions%2A> метод, возвращающий массив <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> объектов, содержащих различные <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction> объектов. Этот метод вызывается, когда она открыта лампочки.  
  
    > [!WARNING]
    >  Следует убедиться в том, реализации `HasSuggestedActionsAsync()` и `GetSuggestedActions()` являются постоянной; это, если `HasSuggestedActionsAsync()` возвращает `true`, затем `GetSuggestedActions()` должны иметь некоторые действия для отображения. Во многих случаях `HasSuggestedActionsAsync()` вызывается непосредственно перед вызовом `GetSuggestedActions()`, но это не всегда так. Например, если пользователь вызывает действия лампочки, нажав клавишу (CTRL +.) только `GetSuggestedActions()` вызывается.  
  
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
  
8.  Чтобы завершить реализацию, добавьте реализации для `Dispose()` и `TryGetTelemetryId()` методы. Мы не хотим сделать данные телеметрии, поэтому просто возвращается значение false и равным пустой идентификатор GUID.  
  
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
  
## <a name="implementing-light-bulb-actions"></a>Реализация действия лампочки  
  
1.  В проекте, добавьте ссылку на Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll и набор **Копировать локально** для `False`.  
  
2.  Создайте два класса с именами `UpperCaseSuggestedAction` и `LowerCaseSuggestedAction`. В обоих классах реализован интерфейс <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction>.  
  
    ```csharp  
    internal class UpperCaseSuggestedAction : ISuggestedAction   
    internal class LowerCaseSuggestedAction : ISuggestedAction  
    ```  
  
     Эти два класса похожи за тем исключением, что один из них вызывает <xref:System.String.ToUpper%2A>, а другой вызывает <xref:System.String.ToLower%2A>. В дальнейших шагах рассматривается создание класса для действия преобразования в верхний регистр, но вам необходимо реализовать оба класса. Используйте инструкции по реализации действия преобразования в верхний регистр в качестве шаблона для реализации действия преобразования в нижний регистр.  
  
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
  
6.  Реализуйте <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetPreviewAsync%2A> метод, потому что он отображается как действия предварительной версии.  
  
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
  
9. Реализуйте метод <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.Invoke%2A>, заменив текст в диапазоне на эквивалентный текст в верхнем регистре.  
  
    ```csharp  
    public void Invoke(CancellationToken cancellationToken)  
    {  
        m_span.TextBuffer.Replace(m_span.GetSpan(m_snapshot), m_upper);  
    }  
    ```  
  
    > [!WARNING]
    >  Действие лампочки **Invoke** метод не должен отображать пользовательский Интерфейс.  Если ваше действие вызвать новый пользовательский Интерфейс (например предварительного просмотра или выбора диалоговое окно), не имеют пользовательского интерфейса, непосредственно из пользовательского **Invoke** метод, но вместо этого запланировать для отображения пользовательского интерфейса после возврата из **Invoke**.  
  
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
  
11. Не забудьте сделать то же самое `LowerCaseSuggestedAction` изменение отображаемый текст для «преобразовать "{0}" в нижний регистр» и при вызове метода <xref:System.String.ToUpper%2A> для <xref:System.String.ToLower%2A>.  
  
## <a name="building-and-testing-the-code"></a>Сборка и тестирование кода  
 Чтобы протестировать этот код, выполните сборку решения LightBulbTest и запустите его в экспериментальном экземпляре.  
  
1.  Постройте решение.  
  
2.  При запуске этого проекта в отладчике создается второй экземпляр Visual Studio.  
  
3.  Создайте текстовый файл и введите любой текст. Вы должны увидеть лампочки слева от текста.  
  
     ![Тестирование лампочки](../extensibility/media/testlightbulb.png "TestLIghtBulb")  
  
4.  Точки в «лампочку». Вы должны увидеть стрелку вниз.  
  
5.  Если щелкнуть «лампочку», два предлагаемых действия следует отображать вместе с предварительной версией выбранное действие.  
  
     ![Тестирование лампочки, расширенное](../extensibility/media/testlightbulbexpanded.gif "TestLIghtBulbExpanded")  
  
6.  Если выбрать первое действие, все символы текущего слова должны преобразоваться в верхний регистр. Если выбрать второе действие, все символы должны преобразоваться в нижний регистр.

