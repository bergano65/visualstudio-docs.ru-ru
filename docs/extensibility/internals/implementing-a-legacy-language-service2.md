---
title: Реализация устаревшего языка S2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], implementing
ms.assetid: 5bcafdc5-f922-48f6-a12e-6c8507a79a05
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 053ca367776c811dd1192814c5f928bb294eefb4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72727241"
---
# <a name="implementing-a-legacy-language-service"></a>Реализация устаревшей языковой службы
Для реализации языковой службы с помощью управляемой платформы пакетов (MPF) необходимо создать производный класс от класса <xref:Microsoft.VisualStudio.Package.LanguageService> и реализовать следующие абстрактные методы и свойства:

- метод <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> ;

- метод <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> ;

- метод <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> ;

- Свойство <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A>.

  Дополнительные сведения о реализации этих методов и свойств см. в соответствующих разделах ниже.

  Для поддержки дополнительных функций языковой службе может потребоваться создать производный класс от одного из классов языковой службы MPF. Например, для поддержки дополнительных команд меню необходимо создать класс, производный от класса <xref:Microsoft.VisualStudio.Package.ViewFilter>, и переопределить несколько методов обработки команд (Дополнительные сведения см. в разделе <xref:Microsoft.VisualStudio.Package.ViewFilter>). Класс <xref:Microsoft.VisualStudio.Package.LanguageService> предоставляет ряд методов, которые вызываются для создания новых экземпляров различных классов, и вы переопределяете соответствующий метод создания, чтобы предоставить экземпляр класса. Например, необходимо переопределить метод <xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A> в классе <xref:Microsoft.VisualStudio.Package.LanguageService>, чтобы он возвращал экземпляр собственного класса <xref:Microsoft.VisualStudio.Package.ViewFilter>. Дополнительные сведения см. в разделе "создание экземпляров пользовательских классов".

  Языковая служба также может предоставлять собственные значки, которые используются во многих местах. Например, при отображении списка завершения IntelliSense каждый элемент в списке может иметь связанный с ним значок, помечая элемент как метод, класс, пространство имен, свойство или любое необходимое для вашего языка. Эти значки используются во всех списках IntelliSense, в **панели навигации**и в окне **Список ошибок** задач. Дополнительные сведения см. в разделе "образы языковой службы" ниже.

## <a name="getlanguagepreferences-method"></a>Метод Жетлангуажепреференцес
 Метод <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> всегда возвращает один и тот же экземпляр класса <xref:Microsoft.VisualStudio.Package.LanguagePreferences>. Базовый класс <xref:Microsoft.VisualStudio.Package.LanguagePreferences> можно использовать, если для языковой службы не требуются дополнительные параметры. Классы языковой службы MPF предполагают наличие по крайней мере базового класса <xref:Microsoft.VisualStudio.Package.LanguagePreferences>.

### <a name="example"></a>Пример
 В этом примере показана типичная реализация метода <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>. В этом примере используется базовый класс <xref:Microsoft.VisualStudio.Package.LanguagePreferences>.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        private LanguagePreferences m_preferences;

        public override LanguagePreferences GetLanguagePreferences()
        {
            if (m_preferences == null)
            {
                m_preferences = new LanguagePreferences(this.Site,
                                                        typeof(TestLanguageService).GUID,
                                                        this.Name );
                m_preferences.Init();
            }
            return m_preferences;
        }
    }
}
```

## <a name="getscanner-method"></a>Метод Scanner
 Этот метод возвращает экземпляр объекта <xref:Microsoft.VisualStudio.Package.IScanner>, который реализует синтаксический анализатор или сканер, используемый для получения маркеров и их типов и триггеров. Этот сканер используется в классе <xref:Microsoft.VisualStudio.Package.Colorizer> для выделения цветом, хотя сканер также можно использовать для получения типов токенов и триггеров в качестве версионного к более сложной операции синтаксического анализа. Необходимо предоставить класс, реализующий интерфейс <xref:Microsoft.VisualStudio.Package.IScanner>, и необходимо реализовать все методы интерфейса <xref:Microsoft.VisualStudio.Package.IScanner>.

### <a name="example"></a>Пример
 В этом примере показана типичная реализация метода <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>. Класс `TestScanner` реализует интерфейс <xref:Microsoft.VisualStudio.Package.IScanner> (не показан).

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        private TestScanner m_scanner;

        public override IScanner GetScanner(IVsTextLines buffer)
        {
            if (m_scanner == null)
            {
                m_scanner = new TestScanner(buffer);
            }
            return m_scanner;
        }
    }
}
    internal class TestScanner : IScanner
    {
        private IVsTextBuffer m_buffer;
        string m_source;

        public TestScanner(IVsTextBuffer buffer)
        {
            m_buffer = buffer;
        }

        bool IScanner.ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo, ref int state)
        {
            tokenInfo.Type = TokenType.Unknown;
            tokenInfo.Color = TokenColor.Text;
            return true;
        }

        void IScanner.SetSource(string source, int offset)
        {
            m_source = source.Substring(offset);
        }
    }

```

## <a name="parsesource-method"></a>Метод Парсесаурце
 Анализирует исходный файл по ряду различных причин. Этому методу предоставляется объект <xref:Microsoft.VisualStudio.Package.ParseRequest>, который описывает, что ожидается из определенной операции синтаксического анализа. Метод <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> вызывает более сложное средство синтаксического анализа, определяющее функциональность и область действия токена. Метод <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> используется для поддержки операций IntelliSense, а также для сопоставления фигурных скобок. Даже если вы не поддерживаете такие расширенные операции, необходимо возвратить допустимый объект <xref:Microsoft.VisualStudio.Package.AuthoringScope>, который требует создания класса, реализующего интерфейс <xref:Microsoft.VisualStudio.Package.AuthoringScope>, и реализации всех методов в этом интерфейсе. Можно вернуть значения NULL из всех методов, но сам объект <xref:Microsoft.VisualStudio.Package.AuthoringScope> не должен иметь значение null.

### <a name="example"></a>Пример
 В этом примере показана минимальная реализация метода <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> и класса <xref:Microsoft.VisualStudio.Package.AuthoringScope>, достаточного для того, чтобы языковая служба была скомпилирована и функционировать без поддержки каких-либо дополнительных функций.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        public override AuthoringScope ParseSource(ParseRequest req)
        {
            return new TestAuthoringScope();
        }
    }

    internal class TestAuthoringScope : AuthoringScope
    {
        public override string GetDataTipText(int line, int col, out TextSpan span)
        {
            span = new TextSpan();
            return null;
        }

        public override Declarations GetDeclarations(IVsTextView view,
                                                     int line,
                                                     int col,
                                                     TokenInfo info,
                                                     ParseReason reason)
        {
            return null;
        }

        public override string Goto(VSConstants.VSStd97CmdID cmd, IVsTextView textView, int line, int col, out TextSpan span)
        {
            span = new TextSpan();
            return null;
        }

        public override Methods GetMethods(int line, int col, string name)
        {
            return null;
        }
}
```

## <a name="name-property"></a>Имя, свойство
 Это свойство возвращает имя языковой службы. Это имя должно совпадать с именем, заданным при регистрации языковой службы. Это имя используется в нескольких местах, самым заметным является класс <xref:Microsoft.VisualStudio.Package.LanguagePreferences>, в котором имя используется для доступа к реестру. Имя, возвращаемое этим свойством, не должно быть локализовано, так как оно используется в реестре для записи реестра и имен ключей.

### <a name="example"></a>Пример
 В этом примере показана одна возможная реализация свойства <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A>. Обратите внимание, что имя здесь жестко запрограммировано: фактическое имя должно быть получено из файла ресурсов, чтобы его можно было использовать при регистрации языковой службы (см. раздел [Регистрация устаревшей языковой службы](../../extensibility/internals/registering-a-legacy-language-service1.md)).

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        public override string Name
        {
            get { return "Test Language"; }
        }
    }
}
```

## <a name="instantiating-custom-classes"></a>Создание экземпляров пользовательских классов
 Следующие методы в указанных классах могут быть переопределены для предоставления экземпляров собственных версий каждого класса.

### <a name="in-the-languageservice-class"></a>В классе Лангуажесервице

|Метод|Возвращаемый класс|Описание|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateCodeWindowManager%2A>|<xref:Microsoft.VisualStudio.Package.CodeWindowManager>|Для поддержки пользовательских дополнений к текстовому представлению.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A>|<xref:Microsoft.VisualStudio.Package.DocumentProperties>|Для поддержки пользовательских свойств документа.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>|<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>|Для поддержки **панели навигации**.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionFunction>|Для поддержки функций в шаблонах фрагментов кода.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionProvider>|Для поддержки фрагментов кода (этот метод обычно не переопределен).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateParseRequest%2A>|<xref:Microsoft.VisualStudio.Package.ParseRequest>|Для поддержки настройки структуры <xref:Microsoft.VisualStudio.Package.ParseRequest> (этот метод обычно не переопределен).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateSource%2A>|<xref:Microsoft.VisualStudio.Package.Source>|Для поддержки форматирования исходного кода, указания символов комментария и настройки сигнатур методов.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A>|<xref:Microsoft.VisualStudio.Package.ViewFilter>|Для поддержки дополнительных команд меню.|
|<xref:Microsoft.VisualStudio.Package.Source.GetColorizer%2A>|<xref:Microsoft.VisualStudio.Package.Colorizer>|Для поддержки выделения синтаксиса (этот метод обычно не переопределен).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>|<xref:Microsoft.VisualStudio.Package.LanguagePreferences>|Для поддержки доступа к параметрам языка. Этот метод должен быть реализован, но может возвращать экземпляр базового класса.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>|<xref:Microsoft.VisualStudio.Package.IScanner>|Для предоставления синтаксического анализатора, используемого для идентификации типов токенов в строке. Этот метод должен быть реализован и <xref:Microsoft.VisualStudio.Package.IScanner> должен быть производным от.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringScope>|Для предоставления средства синтаксического анализа, используемого для определения функциональности и области действия во всем исходном файле. Этот метод должен быть реализован и должен возвращать экземпляр версии класса <xref:Microsoft.VisualStudio.Package.AuthoringScope>. Если бы все, что требуется поддерживать, — выделение синтаксиса (которое требует, чтобы <xref:Microsoft.VisualStudio.Package.IScanner> средство синтаксического анализа возвращалось из метода <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>), можно не выполнять никаких действий в этом методе, кроме возврата версии класса <xref:Microsoft.VisualStudio.Package.AuthoringScope>, методы которого возвращают значения NULL.|

### <a name="in-the-source-class"></a>В классе исходного кода

|Метод|Возвращаемый класс|Описание|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A>|<xref:Microsoft.VisualStudio.Package.CompletionSet>|Для настройки вывода списков завершения IntelliSense (этот метод обычно не переопределен).|
|<xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A>|<xref:Microsoft.VisualStudio.Package.DocumentTask>|Для поддержки маркеров в списке задач Список ошибок; в частности, поддержка функций перед открытием файла и переходом к строке, вызвавшей ошибку.|
|<xref:Microsoft.VisualStudio.Package.Source.CreateMethodData%2A>|<xref:Microsoft.VisualStudio.Package.MethodData>|Для настройки вывода всплывающих подсказок параметров IntelliSense.|
|<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>|<xref:Microsoft.VisualStudio.Package.CommentInfo>|Для поддержки комментирования кода.|
|<xref:Microsoft.VisualStudio.Package.Source.CreateAuthoringSink%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringSink>|Для сбора сведений во время операции синтаксического анализа.|

### <a name="in-the-authoringscope-class"></a>В классе Аусорингскопе

|Метод|Возвращаемый класс|Описание|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A>|<xref:Microsoft.VisualStudio.Package.Declarations>|Предоставляет список объявлений, таких как члены или типы. Этот метод должен быть реализован, но может возвращать значение null. Если этот метод возвращает допустимый объект, то объект должен быть экземпляром вашей версии класса <xref:Microsoft.VisualStudio.Package.Declarations>.|
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetMethods%2A>|<xref:Microsoft.VisualStudio.Package.Methods>|Предоставляет список сигнатур методов для данного контекста. Этот метод должен быть реализован, но может возвращать значение null. Если этот метод возвращает допустимый объект, то объект должен быть экземпляром вашей версии класса <xref:Microsoft.VisualStudio.Package.Methods>.|

## <a name="language-service-images"></a>Образы языковой службы
 Чтобы предоставить список значков, используемых в языковой службе, переопределите метод <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> в классе <xref:Microsoft.VisualStudio.Package.LanguageService> и возвратите <xref:System.Windows.Forms.ImageList>, содержащее значки. Базовый класс <xref:Microsoft.VisualStudio.Package.LanguageService> загружает набор значков по умолчанию. Так как вы указываете точный индекс изображения в тех местах, которым требуются значки, способ организации собственного списка изображений полностью зависит от вас.

### <a name="images-used-in-intellisense-completion-lists"></a>Изображения, используемые в списках завершения IntelliSense
 Для списков завершения IntelliSense указывается индекс изображения для каждого элемента в методе <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> класса <xref:Microsoft.VisualStudio.Package.Declarations>, который необходимо переопределить, если необходимо указать индекс изображения. Значение, возвращаемое методом <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A>, является индексом в списке изображений, предоставляемом конструктору класса <xref:Microsoft.VisualStudio.Package.CompletionSet> и который является тем же списком изображений, возвращенным методом <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> в классе <xref:Microsoft.VisualStudio.Package.LanguageService> (можно изменить список изображений, который будет использоваться для @no__ T_4 при переопределении метода <xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A> в классе <xref:Microsoft.VisualStudio.Package.Source> для предоставления другого списка изображений).

### <a name="images-used-in-the-navigation-bar"></a>Изображения, используемые на панели навигации
 На **панели навигации** отображаются списки типов и членов, которые используются для быстрой навигации, а также для отображения значков. Эти значки получаются из метода <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> в классе <xref:Microsoft.VisualStudio.Package.LanguageService> и не могут быть переопределены специально для **панели навигации**. Индексы, используемые для каждого элемента в полях со списком, задаются, когда списки, представляющие поля со списками, заполняются в методе <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> в классе <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> (см. раздел [Поддержка панели навигации в языковой службе прежних версий](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)). Эти индексы изображений получаются каким-либо образом из средства синтаксического анализа, как правило, с помощью версии класса <xref:Microsoft.VisualStudio.Package.Declarations>. Способ получения индексов полностью зависит от вас.

### <a name="images-used-in-the-error-list-task-window"></a>Изображения, используемые в окне задачи Список ошибок
 Всякий раз, когда средство синтаксического анализа <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> методов (см. раздел средство [синтаксического анализа и проверки службы прежних версий](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)) обнаруживает ошибку и передает эту ошибку методу <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> в классе <xref:Microsoft.VisualStudio.Package.AuthoringSink>, в окне задачи **Список ошибок** отображается сообщение об ошибке. Значок может быть связан с каждым элементом, отображаемым в окне задачи, и этот значок поступает из того же списка изображений, который возвращается из метода <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> в классе <xref:Microsoft.VisualStudio.Package.LanguageService>. Поведение по умолчанию для классов MPF — не показывать изображение с сообщением об ошибке. Однако это поведение можно переопределить, создав производный класс от класса <xref:Microsoft.VisualStudio.Package.Source> и переопределив метод <xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A>. В этом методе создается новый объект <xref:Microsoft.VisualStudio.Package.DocumentTask>. Перед возвратом этого объекта можно использовать свойство <xref:Microsoft.VisualStudio.Shell.Task.ImageIndex%2A> объекта <xref:Microsoft.VisualStudio.Package.DocumentTask>, чтобы задать индекс изображения. Это будет выглядеть примерно так, как показано в следующем примере. Обратите внимание, что `TestIconImageIndex` является перечислением, в котором перечислены все значки, и оно относится только к этому примеру. У вас может быть другой способ идентификации значков в языковой службе.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    class TestSource : Source
    {
        public override DocumentTask CreateErrorTaskItem(
            TextSpan          span,
            string            filename,
            string            message,
            TaskPriority      priority,
            TaskCategory      category,
            MARKERTYPE        markerType,
            TaskErrorCategory errorCategory)
        {
            DocumentTask taskItem = base.CreateErrorTaskItem(
                                           span,
                                           filename,
                                           message,
                                           priority,
                                           category,
                                           markerType,
                                           errorCategory);
            if (errorCategory == TaskErrorCategory.Error)
            {
                taskItem.ImageIndex = TestIconImageIndex.Error;
            }
            return taskItem;
        }
    }
}
```

## <a name="the-default-image-list-for-a-language-service"></a>Список изображений по умолчанию для языковой службы
 Список изображений по умолчанию, поставляемый с базовыми классами языковой службы MPF, содержит несколько значков, связанных с более распространенными элементами языка. Основная часть этих значков упорядочена в наборах из шести вариантов, соответствующих концепциям доступа Public, internal, Friend, protected, private и shortcut. Например, можно иметь разные значки для метода в зависимости от того, является ли он открытым, защищенным или закрытым.

 Следующее перечисление указывает типичные имена для каждого набора значков и указывает связанный индекс. Например, на основе перечисления можно указать индекс изображения для защищенного метода как `(int)IconImageIndex.Method + (int)IconImageIndex.AccessProtected`. При необходимости можно изменить имена в этом перечислении.

```csharp
public enum IconImageIndex
        {
            // access types
            AccessPublic = 0,
            AccessInternal = 1,
            AccessFriend = 2,
            AccessProtected = 3,
            AccessPrivate = 4,
            AccessShortcut = 5,

            Base = 6,
            // Each of the following icon type has 6 versions,
            //corresponding to the access types
            Class = Base + 0,
            Constant = Base + 1,
            Delegate = Base + 2,
            Enumeration = Base + 3,
            EnumMember = Base + 4,
            Event = Base + 5,
            Exception = Base + 6,
            Field = Base + 7,
            Interface = Base + 8,
            Macro = Base + 9,
            Map = Base + 10,
            MapItem = Base + 11,
            Method = Base + 12,
            OverloadedMethod = Base + 13,
            Module = Base + 14,
            Namespace = Base + 15,
            Operator = Base + 16,
            Property = Base + 17,
            Struct = Base + 18,
            Template = Base + 19,
            Typedef = Base + 20,
            Type = Base + 21,
            Union = Base + 22,
            Variable = Base + 23,
            ValueType = Base + 24,
            Intrinsic = Base + 25,
            JavaMethod = Base + 26,
            JavaField = Base + 27,
            JavaClass = Base + 28,
            JavaNamespace = Base + 29,
            JavaInterface = Base + 30,
            // Miscellaneous icons with one icon for each type.
            Error = 187,
            GreyedClass = 188,
            GreyedPrivateMethod = 189,
            GreyedProtectedMethod = 190,
            GreyedPublicMethod = 191,
            BrowseResourceFile = 192,
            Reference = 193,
            Library = 194,
            VBProject = 195,
            VBWebProject = 196,
            CSProject = 197,
            CSWebProject = 198,
            VB6Project = 199,
            CPlusProject = 200,
            Form = 201,
            OpenFolder = 202,
            ClosedFolder = 203,
            Arrow = 204,
            CSClass = 205,
            Snippet = 206,
            Keyword = 207,
            Info = 208,
            CallBrowserCall = 209,
            CallBrowserCallRecursive = 210,
            XMLEditor = 211,
            VJProject = 212,
            VJClass = 213,
            ForwardedType = 214,
            CallsTo = 215,
            CallsFrom = 216,
            Warning = 217,
        }
```

## <a name="see-also"></a>См. также
- [Реализация языковой службы прежних версий](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [Обзор языковой службы прежних версий](../../extensibility/internals/legacy-language-service-overview.md)
- [Регистрация языковой службы прежних версий](../../extensibility/internals/registering-a-legacy-language-service1.md)
- [Средство синтаксического анализа и сканер языковой службы прежних версий](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)