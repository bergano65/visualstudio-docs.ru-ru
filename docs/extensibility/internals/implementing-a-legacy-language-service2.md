---
title: Реализация языка прежних версий Service2 | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], implementing
ms.assetid: 5bcafdc5-f922-48f6-a12e-6c8507a79a05
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d54572bc3b105af01ed42b01a27f363da80d58de
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="implementing-a-legacy-language-service"></a>Реализация службы языка для прежних версий
Чтобы реализовать языковую службу, с помощью платформы управляемых пакетов (MPF), должен быть производным от класса <xref:Microsoft.VisualStudio.Package.LanguageService> класса и реализовать следующие абстрактные методы и свойства:  
  
-   метод <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>;  
  
-   метод <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>;  
  
-   метод <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>;  
  
-   Свойство <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A>.  
  
 См. соответствующие разделы ниже дополнительные сведения о реализации этих методов и свойств.  
  
 Для поддержки дополнительных функций, службе языка может быть создать класс, производный от одного из классов службы языка MPF; Например, для поддержки дополнительные команды меню, необходимо создать производный класс от класса <xref:Microsoft.VisualStudio.Package.ViewFilter> класса и переопределить некоторые методы обработки команды (в разделе <xref:Microsoft.VisualStudio.Package.ViewFilter> подробные сведения). <xref:Microsoft.VisualStudio.Package.LanguageService> Класс предоставляет ряд методов, вызываемых для создания новых экземпляров различных классов и переопределить метод соответствующие создания экземпляров этого класса. Например, вам нужно переопределить <xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A> метод в <xref:Microsoft.VisualStudio.Package.LanguageService> класса, чтобы вернуть экземпляр <xref:Microsoft.VisualStudio.Package.ViewFilter> класса. Дополнительные сведения см в разделе «Создание экземпляров пользовательские классы».  
  
 Язык службы также может предоставлять свои собственные значки, которые используются во многих местах. Например при отображении списка завершения IntelliSense каждый элемент в списке может иметь значок, связанный с ним, элемент будет помечен как метод, класс, пространство имен, свойств, или любые необходимые для вашего языка. Эти значки используются во всех списках IntelliSense **панель навигации**и в **список ошибок** окно задач. В разделе «Язык обслуживания образов» ниже сведения.  
  
## <a name="getlanguagepreferences-method"></a>Метод GetLanguagePreferences  
 <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> Метод всегда возвращает тот же экземпляр <xref:Microsoft.VisualStudio.Package.LanguagePreferences> класса. Можно использовать базовый <xref:Microsoft.VisualStudio.Package.LanguagePreferences> класса, если не требуется, чтобы все дополнительные параметры для службы языка. Классы MPF языковой службы предполагается наличие по крайней мере базы <xref:Microsoft.VisualStudio.Package.LanguagePreferences> класса.  
  
### <a name="example"></a>Пример  
 В этом примере показано типичное использование <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> метода. В этом примере используется базовый <xref:Microsoft.VisualStudio.Package.LanguagePreferences> класса.  
  
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
 Этот метод возвращает экземпляр класса <xref:Microsoft.VisualStudio.Package.IScanner> объект, реализующий строк средство синтаксического анализа или сканер, использовать для получения токенов и их типы и триггеры. Этот сканер используется в <xref:Microsoft.VisualStudio.Package.Colorizer> класса окраски, несмотря на то, что сканер также может использоваться для получения типы маркеров, а триггеры как prelude для более сложных операция синтаксического анализа. Необходимо указать класс, реализующий <xref:Microsoft.VisualStudio.Package.IScanner> интерфейс и вы должны реализовать все методы на <xref:Microsoft.VisualStudio.Package.IScanner> интерфейса.  
  
### <a name="example"></a>Пример  
 В этом примере показано типичное использование <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> метода. `TestScanner` Класс реализует <xref:Microsoft.VisualStudio.Package.IScanner> интерфейса (не показано).  
  
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
 Анализирует исходный файл, в зависимости от числа различных причин. Этот метод получает <xref:Microsoft.VisualStudio.Package.ParseRequest> объекта, который описывает, что ожидается от конкретной операции синтаксического анализа. <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Метод вызывает более сложные средства синтаксического анализа, определяющий функцию создания маркеров и области. <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Метод используется в поддержке для операций IntelliSense, а также проверка соответствия фигурных скобок. Даже если не поддерживает такие расширенные операции, вы по-прежнему должен возвращать допустимое <xref:Microsoft.VisualStudio.Package.AuthoringScope> объектов, которые необходимо создать класс, реализующий <xref:Microsoft.VisualStudio.Package.AuthoringScope> интерфейс и реализовать все методы этого интерфейса. Может возвращать значения null из всех методов, но <xref:Microsoft.VisualStudio.Package.AuthoringScope> сам объект не должен иметь значение null.  
  
### <a name="example"></a>Пример  
 В этом примере показано минимальную реализацию <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод и <xref:Microsoft.VisualStudio.Package.AuthoringScope> класс, достаточны для того, служба языка для компиляции и работать без фактически поддержки более сложных функций.  
  
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
  
## <a name="name-property"></a>Имя свойства  
 Это свойство возвращает имя языковой службы. Это должен быть тем же именем, заданным при регистрации языковой службы. Это имя используется в нескольких местах, самым важным из которых является <xref:Microsoft.VisualStudio.Package.LanguagePreferences> класса, где имя используется для доступа к реестру. Имя, возвращаемый этим свойством не должны быть переведены, как он используется в реестре для записи реестра и имена ключей.  
  
### <a name="example"></a>Пример  
 В этом примере показан один из возможных вариантов реализации <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A> свойство. Обратите внимание, что здесь имя жестко: фактическое имя должны происходить из файла ресурсов, чтобы можно было использовать при регистрации языковую службу (см. [регистрации службы языка для прежних версий](../../extensibility/internals/registering-a-legacy-language-service1.md)).  
  
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
  
## <a name="instantiating-custom-classes"></a>При создании пользовательских классов  
 Можно переопределить следующие методы в классах, указанный для предоставления экземпляров версий каждого класса.  
  
### <a name="in-the-languageservice-class"></a>В классе LanguageService  
  
|Метод|Возвращаемый класс|Описание|  
|------------|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateCodeWindowManager%2A>|<xref:Microsoft.VisualStudio.Package.CodeWindowManager>|Для поддержки пользовательских дополнения для представления текста.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A>|<xref:Microsoft.VisualStudio.Package.DocumentProperties>|Для поддержки настраиваемых свойств документа.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>|<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>|Для поддержки **панель навигации**.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionFunction>|Для поддержки функций в шаблоны фрагментов кода.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionProvider>|Для поддержки фрагменты кода (этот метод обычно не переопределяется).|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateParseRequest%2A>|<xref:Microsoft.VisualStudio.Package.ParseRequest>|Для поддержки настройки <xref:Microsoft.VisualStudio.Package.ParseRequest> структуры (этот метод обычно не переопределяется).|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateSource%2A>|<xref:Microsoft.VisualStudio.Package.Source>|Для поддержки форматирования исходный код, указав символы комментариев и настройка сигнатуры метода.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A>|<xref:Microsoft.VisualStudio.Package.ViewFilter>|Для поддержки дополнительные команды меню.|  
|<xref:Microsoft.VisualStudio.Package.Source.GetColorizer%2A>|<xref:Microsoft.VisualStudio.Package.Colorizer>|Для поддержки выделения синтаксиса (этот метод обычно не переопределяется).|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>|<xref:Microsoft.VisualStudio.Package.LanguagePreferences>|Для поддержки доступа к языковые параметры. Этот метод должен быть реализован, но может возвращать экземпляр базового класса.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>|<xref:Microsoft.VisualStudio.Package.IScanner>|Чтобы обеспечить средство синтаксического анализа используется для определения типов токенов в строке. Этот метод должен быть реализован и <xref:Microsoft.VisualStudio.Package.IScanner> должен быть производным от.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringScope>|Чтобы обеспечить средство синтаксического анализа используется для идентификации функциональные возможности и область действия всему исходному файлу. Этот метод должен быть реализован и должен возвращать экземпляр вашей версии <xref:Microsoft.VisualStudio.Package.AuthoringScope> класса. Если вам требуется поддерживать выделение синтаксиса (что требует <xref:Microsoft.VisualStudio.Package.IScanner> синтаксического анализа вернуло из <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> метод), может ничего делать в этом методе, отличном от возвращаемого версии <xref:Microsoft.VisualStudio.Package.AuthoringScope> класса, все методы возвращают значение null.|  
  
### <a name="in-the-source-class"></a>В классе источника  
  
|Метод|Возвращаемый класс|Описание|  
|------------|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A>|<xref:Microsoft.VisualStudio.Package.CompletionSet>|Для настройки внешнего вида списки завершения IntelliSense (этот метод обычно не переопределяется).|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A>|<xref:Microsoft.VisualStudio.Package.DocumentTask>|Для поддержки маркеров в список ошибок список задач; в частности поддержка функций за рамками при открытии файла и перехода к строке, вызвавшего ошибку.|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateMethodData%2A>|<xref:Microsoft.VisualStudio.Package.MethodData>|Для настройки внешнего вида отображение кратких сведений IntelliSense параметра.|  
|<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>|<xref:Microsoft.VisualStudio.Package.CommentInfo>|Для поддержки комментирования кода.|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateAuthoringSink%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringSink>|Для сбора данных в ходе операции синтаксического анализа.|  
  
### <a name="in-the-authoringscope-class"></a>В классе AuthoringScope  
  
|Метод|Возвращаемый класс|Описание|  
|------------|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A>|<xref:Microsoft.VisualStudio.Package.Declarations>|Список объявлений, например члены или типы. Этот метод должен быть реализован, но может возвращать значение null. Если этот метод возвращает допустимый объект, объект должен быть экземпляр вашей версии <xref:Microsoft.VisualStudio.Package.Declarations> класса.|  
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetMethods%2A>|<xref:Microsoft.VisualStudio.Package.Methods>|Предоставляет список сигнатур методов в данном контексте. Этот метод должен быть реализован, но может возвращать значение null. Если этот метод возвращает допустимый объект, объект должен быть экземпляр вашей версии <xref:Microsoft.VisualStudio.Package.Methods> класса.|  
  
## <a name="language-service-images"></a>Язык обслуживания образов  
 Чтобы предоставить список значков, которые будут использоваться всеми языковой службы, необходимо переопределить <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> метод в <xref:Microsoft.VisualStudio.Package.LanguageService> и возвращать <xref:System.Windows.Forms.ImageList> содержащий значки. Базовый <xref:Microsoft.VisualStudio.Package.LanguageService> класс загружает стандартный набор значков. Поскольку указать индекс точное образа в места, которые требуется значки, как упорядочить список изображений возлагается полностью.  
  
### <a name="images-used-in-intellisense-completion-lists"></a>Изображения, используемые в списки завершения IntelliSense  
 Индекс изображения для списки завершения IntelliSense, указано для каждого элемента в <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> метод <xref:Microsoft.VisualStudio.Package.Declarations> класса, который необходимо переопределить, если вы хотите указать индекс изображения. Значение, возвращаемое из <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> метод — это индекс в списке изображений, предоставленный для <xref:Microsoft.VisualStudio.Package.CompletionSet> конструктора класса и именно тот же набор изображений, возвращенные <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> метод в <xref:Microsoft.VisualStudio.Package.LanguageService> класса (можно изменить какого списка изображений Используйте для <xref:Microsoft.VisualStudio.Package.CompletionSet> при переопределении <xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A> метод в <xref:Microsoft.VisualStudio.Package.Source> класс, чтобы предоставить другое изображение список).  
  
### <a name="images-used-in-the-navigation-bar"></a>Изображения, используемые на панели навигации  
 **Панель навигации** отображает списки типов и членов и используется для быстрых переходов можно отображать значки. Эти значки будут получены с <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> метод в <xref:Microsoft.VisualStudio.Package.LanguageService> класса и не может быть переопределен специально для **панель навигации**. Индексов, используемых для каждого элемента в полях с раскрывающимися списками указываются при заполнении списки, представляющий полях с раскрывающимися списками <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> метод в <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> класса (см. [поддержка панели навигации в языковую службупрежнихверсий](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)). Эти индексы изображения каким-либо образом извлекаются из средства синтаксического анализа, обычно через вашей версии <xref:Microsoft.VisualStudio.Package.Declarations> класса. Каким образом получаются индексы возлагается полностью.  
  
### <a name="images-used-in-the-error-list-task-window"></a>Изображения, используемые в окне ошибок список задач  
 Всякий раз, когда <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод синтаксического анализа (см. [средство синтаксического анализа службы языка для прежних версий и сканер](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)), возникает ошибка и передает эту ошибку для <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> метод в <xref:Microsoft.VisualStudio.Package.AuthoringSink> класса, возникла ошибка в  **Список ошибок** окно задач. Значок может быть связан с каждым элементом, который отображается в окне задач, и этот значок, поступают из один список изображений, возвращенные <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> метод <xref:Microsoft.VisualStudio.Package.LanguageService> класса. По умолчанию классы MPF выполняется вывод изображения появляется сообщение об ошибке. Однако можно переопределить это поведение путем наследования от класса <xref:Microsoft.VisualStudio.Package.Source> и переопределения <xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A> метод. В этом методе вы создаете новый <xref:Microsoft.VisualStudio.Package.DocumentTask> объекта. Перед возвратом этот объект, можно использовать <xref:Microsoft.VisualStudio.Shell.Task.ImageIndex%2A> свойство <xref:Microsoft.VisualStudio.Package.DocumentTask> объекта, чтобы задать индекс изображения. Это будет выглядеть примерно как в следующем примере. Обратите внимание, что `TestIconImageIndex` является перечислением, где перечислены все значки, а также относятся к этому примеру. Существует другой способ идентификации значки в службе языка.  
  
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
            TastPriority      priority,  
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
 Список изображений по умолчанию, поставляемых вместе с базовые классы MPF языковой службы содержит несколько значков, связанных с более распространенными элементы языка. Большая часть этих значков организованы в наборы шесть вариантов, соответствующий основные понятия доступа public, внутренняя, friend, protected, private и ярлык. Например может иметь разные значки для метода, в зависимости от того, является ли открытый, защищенный или закрытый.  
  
 Следующее перечисление определяет стандартные имена для каждого набора значков и указывает связанный индекс. Например, исходя из перечисления, можно указать индекс образа для защищенного метода в качестве `(int)IconImageIndex.Method + (int)IconImageIndex.AccessProtected`. Можно изменить имена в этом перечислении в случае необходимости.  
  
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
 [Реализация службы языка для прежних версий](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [Общие сведения о службе языка прежних версий](../../extensibility/internals/legacy-language-service-overview.md)   
 [Регистрация службы языка для прежних версий](../../extensibility/internals/registering-a-legacy-language-service1.md)   
 [Средство синтаксического анализа и сканер языковой службы прежних версий](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)