---
title: Пошаговое руководство. Отображение вариантов использования лампочки | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 99e5566d-450e-4660-9bca-454e1c056a02
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9e95466094f15b4fa166bfdb20c85836da32df96
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/07/2020
ms.locfileid: "89508591"
---
# <a name="walkthrough-displaying-light-bulb-suggestions"></a>Пошаговое руководство. Отображение предложений лампочки
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Лампочки — это значки, используемые в редакторе Visual Studio, которые расширяются для отображения набора действий, например исправления проблем, определяемых встроенными анализаторами кода или рефакторинг кода.  
  
 В редакторах Visual C# и Visual Basic можно также использовать .NET Compiler Platform ("Roslyn") для написания и упаковки собственных анализаторов кода с действиями, которые автоматически отображают лампочки. Дополнительные сведения можно найти в разделе  
  
- [Как написать диагностику и исправление кода C#](https://github.com/dotnet/roslyn/blob/master/docs/wiki/How-To-Write-a-C%23-Analyzer-and-Code-Fix.md)  
  
- [Практические руководства. Написание Visual Basic диагностики и исправления кода](https://github.com/dotnet/roslyn/blob/master/docs/wiki/How-To-Write-a-Visual-Basic-Analyzer-and-Code-Fix.md)  
  
  Другие языки, такие как C++, также предоставляют лампочки для некоторых быстрых действий, например предложение создать реализацию заглушки этой функции.  
  
  Вот как выглядит лампочка. В проекте Visual Basic или Visual C# красная волнистая линия появляется под именем переменной, если она недопустима. При наведении указателя мыши на недопустимый идентификатор рядом с курсором отображается лампочка.  
  
  ![лампочка](../extensibility/media/lightbulb.png "Лампочк")  
  
  Если щелкнуть стрелку вниз на лампочке, отобразится набор предлагаемых действий вместе с предварительной версией выбранного действия. В этом случае отображаются изменения, которые будут внесены в код при выполнении действия.  
  
  ![предварительная версия лампочки](../extensibility/media/lightbulbpreview.png "лигхтбулбпревиев")  
  
  Можно использовать лампочки для предоставления собственных предлагаемых действий. Например, можно указать действия для перемещения открывающих фигурных скобок на новую строку или их перемещения в конец предыдущей строки. В следующем пошаговом руководстве показано, как создать лампочку, которая отображается в текущем слове и имеет два предлагаемых действия: **преобразовать в верхний регистр** и **преобразовать в нижний регистр**.  
  
## <a name="prerequisites"></a>Предварительные условия  
 Начиная с Visual Studio 2015, пакет SDK для Visual Studio не устанавливается из центра загрузки. Он входит в состав программы установки Visual Studio как дополнительный компонент. Кроме того, пакет SDK для VS можно установить позже. Дополнительные сведения см. [в разделе Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Создание проекта Managed Extensibility Framework (MEF)  
  
1. Создание проекта VSIX C#. (В диалоговом окне **Новый проект** выберите **Visual C#/Extensibility**, а затем **проект VSIX**.) Присвойте решению имя `LightBulbTest` .  
  
2. Добавьте шаблон элемента **классификатора редактора** в проект. Дополнительные сведения см. в разделе [Создание расширения с помощью шаблона элемента редактора](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Удалите файлы существующих классов.  
  
4. Добавьте в проект следующую ссылку и установите для параметра **Копировать локально** значение `False` :  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
5. Добавьте новый файл класса и назовите его **лигхтбулбтест**.  
  
6. Добавьте операторы using:  
  
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
  
1. В файле класса LightBulbTest.cs удалите класс Лигхтбулбтест. Добавьте класс с именем **тестсугжестедактионссаурцепровидер** , реализующий интерфейс <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider> . Экспортируйте его с именем **предложенные действия теста** и с <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> текстом "Text".  
  
    ```csharp  
    [Export(typeof(ISuggestedActionsSourceProvider))]  
    [Name("Test Suggested Actions")]  
    [ContentType("text")]  
    internal class TestSuggestedActionsSourceProvider : ISuggestedActionsSourceProvider  
    ```  
  
2. В классе исходного поставщика импортируйте <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> и добавьте его в качестве свойства.  
  
    ```csharp  
    [Import(typeof(ITextStructureNavigatorSelectorService))]  
    internal ITextStructureNavigatorSelectorService NavigatorService { get; set; }  
    ```  
  
3. Реализуйте <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider.CreateSuggestedActionsSource%2A> метод, чтобы вернуть <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> объект. Источник будет обсуждаться в следующем разделе.  
  
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
  
## <a name="implementing-the-isuggestedactionsource"></a>Реализация Исугжестедактионсаурце  
 Предлагаемый источник действия отвечает за сбор набора предлагаемых действий и их добавление в нужный контекст. В данном случае контекстом является текущее слово, а предлагаемые действия — **упперкасесугжестедактион** и **ловеркасесугжестедактион**, которые мы рассмотрим в следующем разделе.  
  
1. Добавьте класс **тестсугжестедактионссаурце** , реализующий интерфейс <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> .  
  
    ```csharp  
    internal class TestSuggestedActionsSource : ISuggestedActionsSource  
    ```  
  
2. Добавьте закрытые поля только для чтения для предлагаемого поставщика источника действия, текстового буфера и представления текста.  
  
    ```csharp  
    private readonly TestSuggestedActionsSourceProvider m_factory;  
    private readonly ITextBuffer m_textBuffer;  
    private readonly ITextView m_textView;  
    ```  
  
3. Добавьте конструктор, который задает закрытые поля.  
  
    ```csharp  
    public TestSuggestedActionsSource(TestSuggestedActionsSourceProvider testSuggestedActionsSourceProvider, ITextView textView, ITextBuffer textBuffer)  
    {  
        m_factory = testSuggestedActionsSourceProvider;  
        m_textBuffer = textBuffer;  
        m_textView = textView;  
    }  
    ```  
  
4. Добавьте закрытый метод, который возвращает слово, находящегося в данный момент в курсоре. Следующий метод просматривает текущее положение курсора и запрашивает структуру текста для экстента слова. Если курсор находится на слове, <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> возвращается в параметре out; в противном случае — значение, `out` `null` а метод возвращает `false` .  
  
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
  
5. Выполните метод <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.HasSuggestedActionsAsync%2A>. Редактор вызывает этот метод, чтобы выяснить, следует ли отображать лампочку. Этот вызов выполняется довольно часто, например при каждом переходе курсора с одной строки на другую или при наведении указателя мыши на волнистую ошибку. Он является асинхронным, чтобы разрешить выполнение других операций пользовательского интерфейса во время работы этого метода. В большинстве случаев этот метод должен выполнять синтаксический анализ и анализ текущей строки, поэтому обработка может занять некоторое время.  
  
     В нашей реализации он асинхронно получает <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> и определяет, является ли экстент значащим, т. е. имеет ли он какой-либо текст, кроме пробелов.  
  
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
  
6. Реализуйте <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.GetSuggestedActions%2A> метод, который возвращает массив <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> объектов, содержащих различные <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction> объекты. Этот метод вызывается при раскрытии лампочки.  
  
    > [!WARNING]
    > Следует убедиться в том, что реализации `HasSuggestedActionsAsync()` и `GetSuggestedActions()` являются единообразными, то есть, если `HasSuggestedActionsAsync()` возвращает `true` , то `GetSuggestedActions()` должны иметь некоторые действия для вывода. Во многих случаях `HasSuggestedActionsAsync()` вызывается непосредственно перед `GetSuggestedActions()` , но это не всегда так. Например, если пользователь вызывает действия лампочки нажатием клавиши (CTRL +.), `GetSuggestedActions()` вызывается только метод.  
  
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
  
7. Определите `SuggestedActionsChanged` событие.  
  
    ```csharp  
    public event EventHandler<EventArgs> SuggestedActionsChanged;  
    ```  
  
8. Чтобы завершить реализацию, добавьте реализации для `Dispose()` `TryGetTelemetryId()` методов и. Мы не хотим выполнять телеметрию, поэтому просто возвращайте значение false и задайте для GUID значение Empty.  
  
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
  
1. В проекте добавьте ссылку на Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll и задайте для параметра **Копировать локально** значение `False` .  
  
2. Создайте два класса с именами `UpperCaseSuggestedAction` и `LowerCaseSuggestedAction`. В обоих классах реализован интерфейс <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction>.  
  
    ```csharp  
    internal class UpperCaseSuggestedAction : ISuggestedAction   
    internal class LowerCaseSuggestedAction : ISuggestedAction  
    ```  
  
     Эти два класса похожи за тем исключением, что один из них вызывает <xref:System.String.ToUpper%2A>, а другой вызывает <xref:System.String.ToLower%2A>. В дальнейших шагах рассматривается создание класса для действия преобразования в верхний регистр, но вам необходимо реализовать оба класса. Используйте инструкции по реализации действия преобразования в верхний регистр в качестве шаблона для реализации действия преобразования в нижний регистр.  
  
3. Добавьте следующие операторы using для следующих классов:  
  
    ```csharp  
    using Microsoft.VisualStudio.Imaging.Interop;  
    using System.Windows;  
    using System.Windows.Controls;  
    using System.Windows.Documents;  
    using System.Windows.Media;  
  
    ```  
  
4. Объявите набор закрытых полей.  
  
    ```csharp  
    private ITrackingSpan m_span;  
    private string m_upper;  
    private string m_display;  
    private ITextSnapshot m_snapshot;  
    ```  
  
5. Добавьте конструктор, который задает поля.  
  
    ```csharp  
    public UpperCaseSuggestedAction(ITrackingSpan span)  
    {  
        m_span = span;  
        m_snapshot = span.TextBuffer.CurrentSnapshot;  
        m_upper = span.GetText(m_snapshot).ToUpper();  
        m_display = string.Format("Convert '{0}' to upper case", span.GetText(m_snapshot));  
    }  
    ```  
  
6. Реализуйте <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetPreviewAsync%2A> метод, чтобы он отображал предварительный просмотр действия.  
  
    ```csharp  
    public Task<object> GetPreviewAsync(CancellationToken cancellationToken)  
    {  
        var textBlock = new TextBlock();  
        textBlock.Padding = new Thickness(5);  
        textBlock.Inlines.Add(new Run() { Text = m_upper });  
        return Task.FromResult<object>(textBlock);  
    }  
    ```  
  
7. Реализуйте <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetActionSetsAsync%2A> метод, чтобы он возвращал пустое <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> перечисление.  
  
    ```csharp  
    public Task<IEnumerable<SuggestedActionSet>> GetActionSetsAsync(CancellationToken cancellationToken)  
    {  
        return Task.FromResult<IEnumerable<SuggestedActionSet>>(null);  
    }  
    ```  
  
8. Реализуйте свойства указанным ниже образом.  
  
    ```csharp  
    public bool HasActionSets  
    {  
        get { return false; }  
    }  
    public string DisplayText  
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
    public void Invoke(CancellationToken cancellationToken)  
    {  
        m_span.TextBuffer.Replace(m_span.GetSpan(m_snapshot), m_upper);  
    }  
    ```  
  
    > [!WARNING]
    > Метод **вызова** действия лампочки не должен отображаться в пользовательском интерфейсе.  Если действие создает новый пользовательский интерфейс (например, диалоговое окно предварительного просмотра или выбора), не выводит пользовательский интерфейс непосредственно в методе **Invoke** , а вместо этого планирует отображение пользовательского интерфейса после возврата из **вызова**.  
  
10. Чтобы завершить реализацию, добавьте `Dispose()` `TryGetTelemetryId()` методы и.  
  
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
  
11. Не забудьте сделать то же самое для `LowerCaseSuggestedAction` изменения отображаемого текста, чтобы преобразовать его в {0} нижний регистр, и вызов <xref:System.String.ToUpper%2A> <xref:System.String.ToLower%2A> .  
  
## <a name="building-and-testing-the-code"></a>Сборка и тестирование кода  
 Чтобы протестировать этот код, создайте решение Лигхтбулбтест и запустите его в экспериментальном экземпляре.  
  
1. Создайте решение.  
  
2. При запуске этого проекта в отладчике создается второй экземпляр Visual Studio.  
  
3. Создайте текстовый файл и введите любой текст. Слева от текста должна появиться лампочка.  
  
     ![тестирование лампочки](../extensibility/media/testlightbulb.png "тестлигхтбулб")  
  
4. Наведите указатель на лампочку. Вы должны увидеть стрелку вниз.  
  
5. Если щелкнуть лампочку, должны отобразиться два предлагаемых действия вместе с предварительной версией выбранного действия.  
  
     ![тестирование лампочки, расширенное](../extensibility/media/testlightbulbexpanded.gif "тестлигхтбулбекспандед")  
  
6. Если выбрать первое действие, все символы текущего слова должны преобразоваться в верхний регистр. Если выбрать второе действие, все символы должны преобразоваться в нижний регистр.
