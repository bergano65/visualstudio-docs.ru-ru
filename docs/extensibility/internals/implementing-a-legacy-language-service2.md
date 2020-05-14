---
title: Внедрение Службы языка наследия2 (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], implementing
ms.assetid: 5bcafdc5-f922-48f6-a12e-6c8507a79a05
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e435af68a893c923eafef744762c9da8505c3fb7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707678"
---
# <a name="implementing-a-legacy-language-service"></a>Реализация языковой службы прежних версий
Для реализации языковой службы с помощью платформы управляемого <xref:Microsoft.VisualStudio.Package.LanguageService> пакета (MPF) необходимо извлечь класс из класса и реализовать следующие абстрактные методы и свойства:

- метод <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> ;

- метод <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> ;

- метод <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> ;

- Свойство <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A>.

  Ниже приведены соответствующие разделы, подробную информацию о реализации этих методов и свойств.

  Для поддержки дополнительных функций языковой службе может потребоваться получить класс из одного из классов языковой службы MPF; например, для поддержки дополнительных команд меню необходимо <xref:Microsoft.VisualStudio.Package.ViewFilter> извлечь класс из класса и переопределить <xref:Microsoft.VisualStudio.Package.ViewFilter> несколько методов обработки команд (см. подробную информацию). Класс <xref:Microsoft.VisualStudio.Package.LanguageService> предоставляет ряд методов, которые называются для создания новых экземпляров различных классов, и вы переопределить соответствующий метод создания, чтобы обеспечить экземпляр вашего класса. Например, необходимо переопределить <xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A> метод в <xref:Microsoft.VisualStudio.Package.LanguageService> классе, чтобы вернуть <xref:Microsoft.VisualStudio.Package.ViewFilter> экземпляр вашего собственного класса. Более подробную информацию можно узнать в разделе "Мгновенные пользовательские классы".

  Ваш языковой сервис также может поставлять свои собственные значки, которые используются во многих местах. Например, при отображенном списке завершения IntelliSense каждый элемент в списке может иметь значок, связанный с ним, отмечая элемент как метод, класс, пространство имен, свойство или все, что необходимо для вашего языка. Эти значки используются во всех списках IntelliSense, **панели навигации**и в окне задачи **списка ошибок.** Ниже приведен раздел "Языковая служба изображений".

## <a name="getlanguagepreferences-method"></a>Метод GetLanguagePreferences
 Метод <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> всегда возвращает один и <xref:Microsoft.VisualStudio.Package.LanguagePreferences> тот же экземпляр класса. Вы можете использовать <xref:Microsoft.VisualStudio.Package.LanguagePreferences> базовый класс, если вам не нужны какие-либо дополнительные предпочтения для вашего языкового сервиса. Классы языкового обслуживания MPF предполагают наличие <xref:Microsoft.VisualStudio.Package.LanguagePreferences> по крайней мере базового класса.

### <a name="example"></a>Пример
 Этот пример показывает типичную реализацию метода. <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> В этом примере используется базовый <xref:Microsoft.VisualStudio.Package.LanguagePreferences> класс.

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

## <a name="getscanner-method"></a>Метод GetScanner
 Этот метод возвращает экземпляр <xref:Microsoft.VisualStudio.Package.IScanner> объекта, который реализует линейный парсер или сканер, используемый для получения токенов и их типов и триггеров. Этот сканер используется <xref:Microsoft.VisualStudio.Package.Colorizer> в классе для окраски, хотя сканер также может быть использован для получения типов токенов и триггеров в качестве прелюдии к более сложной операции разбора. Вы должны предоставить класс, <xref:Microsoft.VisualStudio.Package.IScanner> который реализует интерфейс, и вы <xref:Microsoft.VisualStudio.Package.IScanner> должны реализовать все методы на интерфейсе.

### <a name="example"></a>Пример
 Этот пример показывает типичную реализацию метода. <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> Класс `TestScanner` реализует <xref:Microsoft.VisualStudio.Package.IScanner> интерфейс (не отображается).

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

## <a name="parsesource-method"></a>Метод ParseSource
 Сравнивает исходный файл на основе ряда различных причин. Этому методу <xref:Microsoft.VisualStudio.Package.ParseRequest> дается объект, описывающий то, что ожидается от конкретной операции разбора. Метод <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> вызывает более сложный парсер, который определяет функциональность и область охвата токенов. Метод <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> используется для поддержки операций IntelliSense, а также для сопоставления скобки. Даже если вы не поддерживаете такие передовые <xref:Microsoft.VisualStudio.Package.AuthoringScope> операции, вы все равно должны вернуть <xref:Microsoft.VisualStudio.Package.AuthoringScope> допустимый объект, и это требует создания класса, который реализует интерфейс и реализует все методы на этом интерфейсе. Вы можете вернуть нулевые значения <xref:Microsoft.VisualStudio.Package.AuthoringScope> из всех методов, но сам объект не должен быть нулевая величина.

### <a name="example"></a>Пример
 В этом примере показана минимальная реализация <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метода и <xref:Microsoft.VisualStudio.Package.AuthoringScope> класса, достаточная для того, чтобы языковая служба компилировать и функционировать без фактической поддержки каких-либо более продвинутых функций.

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

## <a name="name-property"></a>Свойство Name
 Это свойство возвращает название языковой службы. Это должно быть то же имя, данное при регистрации языковой службы. Это имя используется в ряде мест, наиболее <xref:Microsoft.VisualStudio.Package.LanguagePreferences> известным из которых является класс, где имя используется для доступа к реестру. Имя, возвращенное этим свойством, не должно быть локализовано, так как оно используется в реестре для регистрации реестра и ключевых имен.

### <a name="example"></a>Пример
 Этот пример показывает одну <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A> возможную реализацию свойства. Обратите внимание, что имя здесь жестко закодировано: фактическое имя должно быть получено из файла ресурса, чтобы его можно было использовать при регистрации языковой службы [(см. Регистрация Службы Языка Наследия).](../../extensibility/internals/registering-a-legacy-language-service1.md)

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

## <a name="instantiating-custom-classes"></a>Мгновенное пользовательские классы
 Следующие методы в указанных классах могут быть переопределены, чтобы предоставить экземпляры ваших собственных версий каждого класса.

### <a name="in-the-languageservice-class"></a>В классе LanguageService

|Метод|Возврат класса|Описание|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateCodeWindowManager%2A>|<xref:Microsoft.VisualStudio.Package.CodeWindowManager>|Для поддержки пользовательских дополнений к текстовому представлению.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A>|<xref:Microsoft.VisualStudio.Package.DocumentProperties>|Для поддержки свойств пользовательских документов.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>|<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>|Для поддержки **панели навигации**.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionFunction>|Для поддержки функций в шаблонах фрагментов фрагмента кода.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionProvider>|Для поддержки фрагментов кода (этот метод, как правило, не переопределяется).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateParseRequest%2A>|<xref:Microsoft.VisualStudio.Package.ParseRequest>|Для поддержки настройки <xref:Microsoft.VisualStudio.Package.ParseRequest> структуры (этот метод, как правило, не переопределяется).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateSource%2A>|<xref:Microsoft.VisualStudio.Package.Source>|Для поддержки форматирования исходного кода, указания символов комментариев и настройки подписей метода.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A>|<xref:Microsoft.VisualStudio.Package.ViewFilter>|Для поддержки дополнительных команд меню.|
|<xref:Microsoft.VisualStudio.Package.Source.GetColorizer%2A>|<xref:Microsoft.VisualStudio.Package.Colorizer>|Для поддержки выделения синтаксиса (этот метод, как правило, не переопределяется).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>|<xref:Microsoft.VisualStudio.Package.LanguagePreferences>|Для поддержки доступа к языковым предпочтениям. Этот метод должен быть реализован, но может вернуть экземпляр базового класса.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>|<xref:Microsoft.VisualStudio.Package.IScanner>|Предоставить парсер, используемый для идентификации типов токенов на линии. Этот метод должен <xref:Microsoft.VisualStudio.Package.IScanner> быть реализован и должен быть выведен из.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringScope>|Предоставить парсер, используемый для идентификации функциональности и сферы охвата всего исходного файла. Этот метод должен быть реализован и должен вернуть <xref:Microsoft.VisualStudio.Package.AuthoringScope> экземпляр вашей версии класса. Если все, что вы хотите поддержать, <xref:Microsoft.VisualStudio.Package.IScanner> это выделение <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> синтаксиса (для чего требуется возврат <xref:Microsoft.VisualStudio.Package.AuthoringScope> парора из метода), вы ничего не можете сделать в этом методе, кроме возврата версии класса, методы которого возвращают нулевые значения.|

### <a name="in-the-source-class"></a>В классе исходных источников

|Метод|Возврат класса|Описание|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A>|<xref:Microsoft.VisualStudio.Package.CompletionSet>|Для настройки отображения списков завершений IntelliSense (этот метод, как правило, не переопределяется).|
|<xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A>|<xref:Microsoft.VisualStudio.Package.DocumentTask>|Для поддержки маркеров в списке задач списка ошибок; в частности, поддержка функций, помимо открытия файла и прыжков к линии, которая вызвала ошибку.|
|<xref:Microsoft.VisualStudio.Package.Source.CreateMethodData%2A>|<xref:Microsoft.VisualStudio.Package.MethodData>|Для настройки отображения IntelliSense Параметр Информация ToolTips.|
|<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>|<xref:Microsoft.VisualStudio.Package.CommentInfo>|Для поддержки комментируя код.|
|<xref:Microsoft.VisualStudio.Package.Source.CreateAuthoringSink%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringSink>|Для сбора информации во время операции разбора.|

### <a name="in-the-authoringscope-class"></a>В классе AuthoringScope

|Метод|Возврат класса|Описание|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A>|<xref:Microsoft.VisualStudio.Package.Declarations>|Предоставляет список деклараций, таких как члены или типы. Этот метод должен быть реализован, но может вернуть нулевую стоимость. Если этот метод возвращает допустимый объект, объект должен <xref:Microsoft.VisualStudio.Package.Declarations> быть экземпляром вашей версии класса.|
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetMethods%2A>|<xref:Microsoft.VisualStudio.Package.Methods>|Предоставляет список подписей метода для данного контекста. Этот метод должен быть реализован, но может вернуть нулевую стоимость. Если этот метод возвращает допустимый объект, объект должен <xref:Microsoft.VisualStudio.Package.Methods> быть экземпляром вашей версии класса.|

## <a name="language-service-images"></a>Изображения языковой службы
 Чтобы предоставить список иконок, которые будут использоваться <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> во всей языковой службе, переопределить метод в <xref:Microsoft.VisualStudio.Package.LanguageService> классе и вернуть <xref:System.Windows.Forms.ImageList> содержащий значки. Базовый <xref:Microsoft.VisualStudio.Package.LanguageService> класс загружает набор иконок по умолчанию. Поскольку вы указываете точный индекс изображения в тех местах, которые нуждаются в значках, то, как вы организуете свой собственный список изображений, полностью зависит от вас.

### <a name="images-used-in-intellisense-completion-lists"></a>Изображения, используемые в списках завершения IntelliSense
 Для списков завершения IntelliSense индекс изображения указан <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> для каждого <xref:Microsoft.VisualStudio.Package.Declarations> элемента в методе класса, который необходимо переопределить, если вы хотите предоставить индекс изображения. <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> Значение, возвращенное из метода, — это <xref:Microsoft.VisualStudio.Package.CompletionSet> индекс в список изображений, поставляемый конструктору класса, и это тот же список изображений, возвращенный из <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> метода в <xref:Microsoft.VisualStudio.Package.LanguageService> классе (можно изменить список изображений, который следует использовать для <xref:Microsoft.VisualStudio.Package.CompletionSet> того, если вы переопределяете <xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A> метод в <xref:Microsoft.VisualStudio.Package.Source> классе для предоставления другого списка изображений).

### <a name="images-used-in-the-navigation-bar"></a>Изображения, используемые в панели навигации
 Панель **навигации** отображает списки типов и участников и используется для быстрой навигации, может отображать значки. Эти значки получены <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> из <xref:Microsoft.VisualStudio.Package.LanguageService> метода в классе и не могут быть переопределены специально для **панели навигации.** Индексы, используемые для каждого элемента в комбо-боксах, определяются при заполнении списков, представляющих комбо-боксы в <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> классе (см. [Поддержку панели навигации в языковой службе Legacy).](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md) Эти индексы изображения получены как-то из парсера, <xref:Microsoft.VisualStudio.Package.Declarations> как правило, через версию класса. Способ получения индексов зависит от вас.

### <a name="images-used-in-the-error-list-task-window"></a>Изображения, используемые в окне списка ошибок
 Всякий <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> раз, когда парсер метода (см. [Наследие Языковая служба Parser и Scanner)](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)сталкивается с ошибкой и передает эту ошибку <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> методу в <xref:Microsoft.VisualStudio.Package.AuthoringSink> классе, ошибка сообщается в окне задачи списка **ошибок.** Значок может быть связан с каждым элементом, который появляется в окне <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> задачи, <xref:Microsoft.VisualStudio.Package.LanguageService> и этот значок исходит от того же списка изображений, возвращенного из метода в классе. Поведение классов MPF по умолчанию заключается в том, чтобы не показывать изображение с сообщением об ошибке. Однако это поведение можно переопределить, выдвивая класс из <xref:Microsoft.VisualStudio.Package.Source> класса и переопределяя <xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A> метод. В этом методе создается новый <xref:Microsoft.VisualStudio.Package.DocumentTask> объект. Перед возвращением этого объекта <xref:Microsoft.VisualStudio.Shell.Task.ImageIndex%2A> можно использовать <xref:Microsoft.VisualStudio.Package.DocumentTask> свойство на объекте для установки индекса изображения. Это будет выглядеть примерно в следующем примере. Обратите `TestIconImageIndex` внимание, что это перечисление, которое перечисляет все значки и специфичен для этого примера. Вы можете иметь другой способ идентификации иконок в вашей языковой службы.

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
 Список изображений по умолчанию, поставляемый базовыми классами языковой службы MPF, содержит ряд значков, связанных с более распространенными элементами языка. Основная часть этих иконок расположена в наборах из шести вариаций, соответствующих концепциям доступа общественности, внутренних, друзей, защищенных, частных и ярлыков. Например, вы можете иметь различные значки для метода в зависимости от того, является ли он общедоступным, защищенным или закрытым.

 В следующем перечислении указаны типичные имена для каждого набора значков и указывается связанный индекс. Например, на основе перечисления можно указать индекс изображения для `(int)IconImageIndex.Method + (int)IconImageIndex.AccessProtected`защищенного метода как. Вы можете изменить имена в этом перечислении по желанию.

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
