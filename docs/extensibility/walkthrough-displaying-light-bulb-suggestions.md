---
title: 'Пошаговое: Отображение Света Bulb Предложения (ru) Документы Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 99e5566d-450e-4660-9bca-454e1c056a02
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 09773e2be81ce51971709db590a07ca9960104fa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697477"
---
# <a name="walkthrough-display-light-bulb-suggestions"></a>Прохождение: Отображение лампочки предложения
Лампочки — это значки в редакторе Visual Studio, которые расширяются для отображения набора действий, например, исправлений проблем, выявленных встроенными анализаторами кода или рефакторингом кода.

 В редакторах Visual C и Visual Basic вы также можете использовать платформу компилятора .NET ("Рослин") для записи и упаковки собственных анализаторов кода с действиями, которые отображают лампочки автоматически. Дополнительные сведения можно найти в разделе

- [Как: Написать диагностику и исправление кода на C-код](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-C%23-Analyzer-and-Code-Fix)

- [Как: Написать visual Основные диагностики и код исправить](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-Visual-Basic-Analyzer-and-Code-Fix)

  Другие языки, такие как СЗ, также предоставляют лампочки для некоторых быстрых действий, таких как предложение создать заглушку реализации этой функции.

  Вот как выглядит лампочка. В проекте Visual Basic или Visual C, красный squiggle появляется под переменным именем, когда он недействителен. Если вы мышь над недействительным идентификатором, лампочка появляется рядом с курсором.

  ![лампочка](../extensibility/media/lightbulb.png "Лампочки")

  При нажатии на стрелку вниз по лампочке появится набор предлагаемых действий, а также предварительный просмотр выбранного действия. В этом случае он показывает изменения, внесенные в код, если вы выполняете действие.

  ![предварительная версия лампочки](../extensibility/media/lightbulbpreview.png "LightBulbPreview")

  Вы можете использовать лампочки, чтобы обеспечить свои собственные предлагаемые действия. Например, можно предоставить действия для перемещения вьющихся фигурных фигурок на новую линию или перемещения их в конец предыдущей строки. Следующее пошаговое решение показывает, как создать лампочку, которая появляется на текущем слове и имеет два предлагаемых действия: Преобразование в **верхний корпус** и **Преобразование в нижний корпус.**

## <a name="prerequisites"></a>Предварительные требования
 Начиная с Visual Studio 2015, вы не устанавливаете Visual Studio SDK из центра загрузки. Он включен в качестве дополнительной функции в Visual Studio установки. Вы также можете установить VS SDK позже. Для получения дополнительной информации, [см.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Создание проекта управляемой расширительности (MEF)

1. Создайте проект СЗ VSIX. (В **диалоге нового проекта** выберите **Visual C / Расширяемость,** затем **VSIX Project**.) Назовите решение. `LightBulbTest`

2. Добавьте шаблон элемента **классификатора редактора** в проект. Для получения дополнительной информации [см. Создать расширение с шаблоном элемента редактора](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Удалите файлы существующих классов.

4. Добавьте следующую ссылку на проект `False`и установите Copy **Local** на:

     *Microsoft.VisualStudio.Language.Intellisense*

5. Добавьте новый файл класса и назовите его **LightBulbTest.**

6. Добавьте следующие директивы using.

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

## <a name="implement-the-light-bulb-source-provider"></a>Реализация поставщика источников лампочки

1. В файле *класса LightBulbTest.cs* удалите класс LightBulbTest. Добавьте класс под названием **TestSuggestedActionsSourceProvider,** который <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>реализуется. Экспортировать его с названием тест <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> **предлагаемых действий** и "текст".

    ```csharp
    [Export(typeof(ISuggestedActionsSourceProvider))]
    [Name("Test Suggested Actions")]
    [ContentType("text")]
    internal class TestSuggestedActionsSourceProvider : ISuggestedActionsSourceProvider
    ```

2. Внутри класса поставщика исходного <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> кода импортируйте и добавляйте его в качестве свойства.

    ```csharp
    [Import(typeof(ITextStructureNavigatorSelectorService))]
    internal ITextStructureNavigatorSelectorService NavigatorService { get; set; }
    ```

3. Реализация <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider.CreateSuggestedActionsSource%2A> метода возврата <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> объекта. Источник обсуждается в следующем разделе.

    ```csharp
    public ISuggestedActionsSource CreateSuggestedActionsSource(ITextView textView, ITextBuffer textBuffer)
    {
        if (textBuffer == null || textView == null)
        {
            return null;
        }
        return new TestSuggestedActionsSource(this, textView, textBuffer);
    }
    ```

## <a name="implement-the-isuggestedactionsource"></a>Реализация ISuggestedActionSource
 Предлагаемый источник действий отвечает за сбор набора предлагаемых действий и добавление их в нужном контексте. В этом случае контекст является текущим словом, а предлагаемыми действиями являются **UpperCaseSuggestedAction** и **LowerCaseSuggestedAction**, которые обсуждаются в следующем разделе.

1. Добавить класс **TestSuggestedActionsSource,** который <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>реализуется.

    ```csharp
    internal class TestSuggestedActionsSource : ISuggestedActionsSource
    ```

2. Добавьте закрытые полей только для чтения для поставщика предлагаемых источников действий, буфер текста и текстовое представление.

    ```csharp
    private readonly TestSuggestedActionsSourceProvider m_factory;
    private readonly ITextBuffer m_textBuffer;
    private readonly ITextView m_textView;
    ```

3. Добавьте конструктор, который устанавливает частные поля.

    ```csharp
    public TestSuggestedActionsSource(TestSuggestedActionsSourceProvider testSuggestedActionsSourceProvider, ITextView textView, ITextBuffer textBuffer)
    {
        m_factory = testSuggestedActionsSourceProvider;
        m_textBuffer = textBuffer;
        m_textView = textView;
    }
    ```

4. Добавьте частный метод, который возвращает слово, которое в настоящее время находится под курсором. Следующий метод рассматривает текущее местоположение курсора и запрашивает навигатор структуры текста для степени слова. Если курсор находится на слове, <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> возвращается в из параметра; в противном случае `out` параметр есть `null` и метод возвращается. `false`

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

5. Выполните метод <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.HasSuggestedActionsAsync%2A>. Редактор называет этот метод, чтобы выяснить, следует ли отображать лампочку. Этот вызов часто делается, например, всякий раз, когда курсор перемещается от одной линии к другой, или когда мышь парит над ошибкой squiggle. Это асинхронно, чтобы позволить другим операциям uI продолжать в то время как этот метод работает. В большинстве случаев этот метод должен выполнять некоторый анализ и анализ текущей строки, поэтому обработка может занять некоторое время.

     В этой реализации он асинхронно получает <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> и определяет, является ли степень значительной, как в, есть ли у него текст, кроме белого пространства.

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

6. Реализация <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.GetSuggestedActions%2A> метода, который возвращает <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> массив объектов, содержащих различные <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction> объекты. Этот метод называется, когда лампочка расширяется.

    > [!WARNING]
    > Вы должны убедиться, что `HasSuggestedActionsAsync()` `GetSuggestedActions()` реализации и являются последовательными; то есть, `HasSuggestedActionsAsync()` `true`если `GetSuggestedActions()` возвращается, то должны иметь некоторые действия для отображения. Во многих `HasSuggestedActionsAsync()` случаях, называется как раз перед `GetSuggestedActions()`, но это не всегда так. Например, если пользователь вызывает действия лампочки, нажимая ( `GetSuggestedActions()` **CTRL** .) только вызывается.

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

8. Для завершения реализации добавьте `Dispose()` реализации для методов и `TryGetTelemetryId()` методов. Вы не хотите делать телеметрии, `false` так что просто `Empty`вернуться и установить GUID .

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

## <a name="implement-light-bulb-actions"></a>Реализация действий лампочки

1. В проекте добавьте ссылку на *Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll* и установите **Copy Local** к `False`.

2. Создайте два класса с именами `UpperCaseSuggestedAction` и `LowerCaseSuggestedAction`. В обоих классах реализован интерфейс <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction>.

    ```csharp
    internal class UpperCaseSuggestedAction : ISuggestedAction
    internal class LowerCaseSuggestedAction : ISuggestedAction
    ```

     Эти два класса похожи за тем исключением, что один из них вызывает <xref:System.String.ToUpper%2A>, а другой вызывает <xref:System.String.ToLower%2A>. В дальнейших шагах рассматривается создание класса для действия преобразования в верхний регистр, но вам необходимо реализовать оба класса. Используйте инструкции по реализации действия преобразования в верхний регистр в качестве шаблона для реализации действия преобразования в нижний регистр.

3. Добавьте следующие директивы с использованием для этих классов:

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

6. Реализация <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetPreviewAsync%2A> метода так, чтобы он отображал предварительный просмотр действия.

    ```csharp
    public Task<object> GetPreviewAsync(CancellationToken cancellationToken)
    {
        var textBlock = new TextBlock();
        textBlock.Padding = new Thickness(5);
        textBlock.Inlines.Add(new Run() { Text = m_upper });
        return Task.FromResult<object>(textBlock);
    }
    ```

7. Реализация <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetActionSetsAsync%2A> метода так, чтобы <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> он возвращал пустой перечисление.

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
    > Лампочка действий **Invoke** метод не ожидается, чтобы показать UI. Если ваше действие действительно приводит к появлению нового uI (например, диалог предварительного просмотра или выбора), не отображайте uI непосредственно из метода **Invoke,** а вместо этого планируете отобразить uI после возвращения из **Invoke.**

10. Чтобы завершить реализацию, `Dispose()` добавьте `TryGetTelemetryId()` и методы.

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

11. Не забудьте сделать то `LowerCaseSuggestedAction` же самое для изменения{0}текста дисплея на "Преобразование' в нижнем случае" и призыв <xref:System.String.ToUpper%2A> к <xref:System.String.ToLower%2A>.

## <a name="build-and-test-the-code"></a>Создание и тестирование кода
 Чтобы протестировать этот код, создайте решение LightBulbTest и запустите его в примере Experimental.

1. Создайте решение.

2. При запуске этого проекта в отладчике запускается второй экземпляр Visual Studio.

3. Создайте текстовый файл и введите любой текст. Вы должны увидеть лампочку слева от текста.

     ![тестирование лампочки](../extensibility/media/testlightbulb.png "TestLIghtBulb")

4. Направьте на лампочку. Вы должны увидеть вниз стрелка.

5. При нажатии на лампочку следует отображать два предлагаемых действия, а также предварительный просмотр выбранного действия.

     ![тестирование лампочки, расширенное](../extensibility/media/testlightbulbexpanded.gif "TestLIghtBulbРасширенный")

6. Если вы нажмете на первое действие, весь текст в текущем слове должен быть преобразован в верхний корпус. Если вы нажмете на второе действие, весь текст должен быть преобразован в нижний корпус.
