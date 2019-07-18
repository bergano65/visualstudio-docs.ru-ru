---
title: Реализация языковой службы прежних версий2 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], implementing
ms.assetid: 5bcafdc5-f922-48f6-a12e-6c8507a79a05
caps.latest.revision: 27
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1a5f419b3b4c55538e8aa46d5aefb3f7e21369be
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68192711"
---
# <a name="implementing-a-legacy-language-service"></a>Реализация языковой службы прежних версий
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Для реализации языковой службы, с помощью managed package framework (MPF), должен быть производным от класса <xref:Microsoft.VisualStudio.Package.LanguageService> класса и реализовать следующие абстрактные методы и свойства:  
  
- метод <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> ;  
  
- метод <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> ;  
  
- метод <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> ;  
  
- Свойство <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A>.  
  
  См. соответствующие разделы ниже дополнительные сведения о реализации этих методов и свойств.  
  
  Для поддержки дополнительных функций, языковой службы может потребоваться создать класс, производный от одного из классов службы языка MPF; Например, для поддержки дополнительных меню команд, необходимо создать производный класс от <xref:Microsoft.VisualStudio.Package.ViewFilter> класса и переопределить некоторые методы обработки команды (см. в разделе <xref:Microsoft.VisualStudio.Package.ViewFilter> подробные сведения). <xref:Microsoft.VisualStudio.Package.LanguageService> Класс предоставляет ряд методов, которые вызываются для создания новых экземпляров различных классов и переопределить метод соответствующие создания экземпляров класса. Например, необходимо переопределить <xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A> метод в <xref:Microsoft.VisualStudio.Package.LanguageService> класс для возврата экземпляра собственного <xref:Microsoft.VisualStudio.Package.ViewFilter> класса. См. Дополнительные сведения можно найти в разделе «Создание экземпляров специальные классы».  
  
  Языковой службы также может предоставлять свои собственные значки, которые используются во многих местах. К примеру при отображении списка завершения IntelliSense, каждый элемент в списке может иметь значок, связанный с ним, элемент будет помечен как метода, класса, пространства имен, свойств, или все, что необходимы для вашего языка. Эти значки используются во всех списках IntelliSense, **панели навигации**, а затем в **список ошибок** окно задач. См. в разделе «Язык обслуживания образов» ниже сведения.  
  
## <a name="getlanguagepreferences-method"></a>Метод GetLanguagePreferences  
 <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> Метод всегда возвращает тот же экземпляр <xref:Microsoft.VisualStudio.Package.LanguagePreferences> класса. Можно использовать базовый <xref:Microsoft.VisualStudio.Package.LanguagePreferences> , если нет необходимости любые дополнительные настройки для языковой службы. Классы MPF языковой службы предполагают наличие по крайней мере базы <xref:Microsoft.VisualStudio.Package.LanguagePreferences> класса.  
  
### <a name="example"></a>Пример  
 В этом примере показано типичное использование <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> метод. В этом примере используется базовый <xref:Microsoft.VisualStudio.Package.LanguagePreferences> класса.  
  
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
 Этот метод возвращает экземпляр <xref:Microsoft.VisualStudio.Package.IScanner> объект, реализующий интерфейс, ориентированный на строки синтаксического анализатора или сканера, используемый для получения маркеров и их типы и триггеры. После этого средство проверки используется в <xref:Microsoft.VisualStudio.Package.Colorizer> класса окраски, несмотря на то, что сканер также может использоваться для получения маркера типы и триггеры, чтобы потом для более сложные операции анализа. Необходимо указать класс, реализующий <xref:Microsoft.VisualStudio.Package.IScanner> интерфейс, поэтому должен реализовывать все методы на <xref:Microsoft.VisualStudio.Package.IScanner> интерфейс.  
  
### <a name="example"></a>Пример  
 В этом примере показано типичное использование <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> метод. `TestScanner` Класс реализует <xref:Microsoft.VisualStudio.Package.IScanner> интерфейс (не показано).  
  
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
 Выполняет синтаксический анализ исходного файла на основе ряда по разным причинам. Этот метод предоставляется <xref:Microsoft.VisualStudio.Package.ParseRequest> , описывающий поведения, ожидаемого от конкретной операции синтаксического анализа. <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Метод вызывает более сложные средства синтаксического анализа, определяющий функцию создания маркеров и область. <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Метод используется в поддержке для операции IntelliSense, а также парные фигурные скобки. Даже если вы не поддерживают такие дополнительные операции, вы по-прежнему должен возвращать допустимое <xref:Microsoft.VisualStudio.Package.AuthoringScope> объекта и что необходимо создать класс, реализующий <xref:Microsoft.VisualStudio.Package.AuthoringScope> интерфейс и реализовать все методы в этом интерфейсе. Может возвращать значения null из всех методов, но <xref:Microsoft.VisualStudio.Package.AuthoringScope> сам объект не должен иметь значение null.  
  
### <a name="example"></a>Пример  
 В этом примере показано минимальную реализацию <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод и <xref:Microsoft.VisualStudio.Package.AuthoringScope> класс, достаточны для того, языковой службы для компиляции и работать без фактически поддержки более сложных функций.  
  
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
 Это свойство возвращает имя языковой службы. Это должен быть тем же именем, учитывая при регистрации языковой службы. Это имя будет использоваться в нескольких местах, самым важным из которых является <xref:Microsoft.VisualStudio.Package.LanguagePreferences> класса, где имя используется для доступа к реестру. Имя, возвращаемый этим свойством не должно быть локализовано, так как он используется в реестре для реестра и имена ключей.  
  
### <a name="example"></a>Пример  
 В этом примере показана одна возможная реализация из <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A> свойство. Обратите внимание, что имя, жестко: фактическое имя должны быть получены из файла ресурсов, поэтому он может использоваться в регистрация языковой службы (см. в разделе [регистрация языковой службы прежних](../../extensibility/internals/registering-a-legacy-language-service1.md)).  
  
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
  
## <a name="instantiating-custom-classes"></a>Создание экземпляра пользовательские классы  
 Следующие методы в указанные классы могут переопределяться для предоставления экземпляров собственные версии каждого класса.  
  
### <a name="in-the-languageservice-class"></a>В классе LanguageService  
  
|Метод|Возвращается|Описание|  
|------------|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateCodeWindowManager%2A>|<xref:Microsoft.VisualStudio.Package.CodeWindowManager>|Для поддержки пользовательских дополнения к текстовому представлению.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A>|<xref:Microsoft.VisualStudio.Package.DocumentProperties>|Для поддержки настраиваемых свойств документа.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>|<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>|Для поддержки **панель навигации**.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionFunction>|Для поддержки функций в шаблоны фрагментов кода.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionProvider>|Поддержка фрагментов кода (этот метод обычно не переопределяется).|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateParseRequest%2A>|<xref:Microsoft.VisualStudio.Package.ParseRequest>|Для поддержки настройки из <xref:Microsoft.VisualStudio.Package.ParseRequest> структуры (этот метод обычно не переопределяется).|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateSource%2A>|<xref:Microsoft.VisualStudio.Package.Source>|Для поддержки форматирования исходный код, указав символы комментария и настройка сигнатур методов.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A>|<xref:Microsoft.VisualStudio.Package.ViewFilter>|Для поддержки дополнительных меню команд.|  
|<xref:Microsoft.VisualStudio.Package.Source.GetColorizer%2A>|<xref:Microsoft.VisualStudio.Package.Colorizer>|Для поддержки выделения синтаксиса (этот метод обычно не переопределяется).|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>|<xref:Microsoft.VisualStudio.Package.LanguagePreferences>|Для поддержки доступа к языковые параметры. Этот метод должен быть реализован, но можно возвратить экземпляр базового класса.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>|<xref:Microsoft.VisualStudio.Package.IScanner>|Для предоставления средство синтаксического анализа, используемый для идентификации типов токенов в строке. Этот метод должен быть реализован и <xref:Microsoft.VisualStudio.Package.IScanner> должен быть производным от.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringScope>|Для предоставления средство синтаксического анализа, используемый для идентификации функциональные возможности и область действия всему исходному файлу. Этот метод должен быть реализован и должен возвращать экземпляр версии <xref:Microsoft.VisualStudio.Package.AuthoringScope> класса. Если все, что требуется для поддержки является выделение синтаксиса (что требует <xref:Microsoft.VisualStudio.Package.IScanner> синтаксического анализа вернуло из <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> метод), можно сделать ничего в этот метод, отличный от возвращаемого версию <xref:Microsoft.VisualStudio.Package.AuthoringScope> класс, методы которого все возвращаемые значения null.|  
  
### <a name="in-the-source-class"></a>В классе источника  
  
|Метод|Возвращается|Описание|  
|------------|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A>|<xref:Microsoft.VisualStudio.Package.CompletionSet>|Для настройки внешнего вида списки завершения IntelliSense (этот метод обычно не переопределяется).|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A>|<xref:Microsoft.VisualStudio.Package.DocumentTask>|Для поддержки маркеров в списке задач Список ошибок; в частности поддержка возможности, недоступные при открытии файла и переход к строке, которая вызвала ошибку.|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateMethodData%2A>|<xref:Microsoft.VisualStudio.Package.MethodData>|Для настройки внешнего вида отображение кратких сведений IntelliSense параметра.|  
|<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>|<xref:Microsoft.VisualStudio.Package.CommentInfo>|Для поддержки комментирование кода.|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateAuthoringSink%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringSink>|Для сбора информации во время операции синтаксического анализа.|  
  
### <a name="in-the-authoringscope-class"></a>В классе AuthoringScope  
  
|Метод|Возвращается|Описание|  
|------------|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A>|<xref:Microsoft.VisualStudio.Package.Declarations>|Список объявлений, такие как члены или типы. Этот метод должен быть реализован, но также может возвращать значение null. Если этот метод возвращает допустимый объект, объект должен представлять собой экземпляр версии <xref:Microsoft.VisualStudio.Package.Declarations> класса.|  
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetMethods%2A>|<xref:Microsoft.VisualStudio.Package.Methods>|Предоставляет список сигнатур метода в данном контексте. Этот метод должен быть реализован, но также может возвращать значение null. Если этот метод возвращает допустимый объект, объект должен представлять собой экземпляр версии <xref:Microsoft.VisualStudio.Package.Methods> класса.|  
  
## <a name="language-service-images"></a>Язык обслуживания образов  
 Чтобы предоставить список значков, используемая в службе языка, переопределить <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> метод в <xref:Microsoft.VisualStudio.Package.LanguageService> и возвращать <xref:System.Windows.Forms.ImageList> содержащий значки. Базовый <xref:Microsoft.VisualStudio.Package.LanguageService> класс загружает набора значков по умолчанию. Так как индекс изображения точно указать в места, которые нужно создать значки, размещения собственного списка изображений — полностью на ваше усмотрение.  
  
### <a name="images-used-in-intellisense-completion-lists"></a>Образы, используемые в списки завершения IntelliSense  
 Для списки завершения IntelliSense, индекс изображения должно быть указано для каждого элемента в <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> метод <xref:Microsoft.VisualStudio.Package.Declarations> класс, который необходимо переопределить, если вы хотите указать индекс изображения. Значение, возвращаемое из <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> метод — это индекс в списке изображений, передаваемое <xref:Microsoft.VisualStudio.Package.CompletionSet> конструктора класса и т. е один список изображений возвращается из <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> метод в <xref:Microsoft.VisualStudio.Package.LanguageService> (можно изменить какой список изображений для класса Используйте для <xref:Microsoft.VisualStudio.Package.CompletionSet> при переопределении <xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A> метод в <xref:Microsoft.VisualStudio.Package.Source> классе, чтобы предоставить другой образ из списка).  
  
### <a name="images-used-in-the-navigation-bar"></a>Образы, используемые на панели навигации  
 **Панель навигации** отображает список типов и членов и используется для быстрой навигации могут отображать значки. Эти значки будут получены с <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> метод в <xref:Microsoft.VisualStudio.Package.LanguageService> класса и не может быть переопределен специально для **панель навигации**. При заполнении списки, представляющий поля со списком указанных индексов, используемых для каждого элемента в полях со списками <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> метод в <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> класса (см. в разделе [поддержка панели навигации в языковой службе прежних версий](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)). Эти индексы образа каким-либо образом получаются из синтаксического анализатора, обычно с помощью вашей версии <xref:Microsoft.VisualStudio.Package.Declarations> класса. Каким образом получаются индексы — полностью на ваше усмотрение.  
  
### <a name="images-used-in-the-error-list-task-window"></a>Образы, используемые в окне ошибок список задач  
 Каждый раз, когда <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> средство синтаксического анализа метод (см. в разделе [средства синтаксического анализа службы языка для прежних версий и сканер](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)) обнаруживает ошибку и передает эту ошибку для <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> метод в <xref:Microsoft.VisualStudio.Package.AuthoringSink> класс, возникла ошибка в  **Список ошибок** окно задач. Значок может быть связан с каждым элементом, который отображается в окне задач, и этот значок поступает из один список изображений, возвращенные <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> метод в <xref:Microsoft.VisualStudio.Package.LanguageService> класса. По умолчанию классы MPF — не Показать изображение с сообщением об ошибке. Тем не менее, это поведение можно переопределить путем наследования от класса <xref:Microsoft.VisualStudio.Package.Source> и переопределение <xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A> метод. В этом методе создается новый <xref:Microsoft.VisualStudio.Package.DocumentTask> объекта. Перед возвратом этот объект, можно использовать <xref:Microsoft.VisualStudio.Shell.Task.ImageIndex%2A> свойство <xref:Microsoft.VisualStudio.Package.DocumentTask> объекта, чтобы задать индекс изображения. Это будет выглядеть примерно как в следующем примере. Обратите внимание, что `TestIconImageIndex` представляет собой перечисление, в которой перечислены все значки относятся к этому примеру. Существует другой способ идентификации значки в службе языка.  
  
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
 Список изображений по умолчанию, в состав базовые классы MPF языковой службы содержит ряд значки, связанные с более общими элементами языка. Основная часть этих значков, расположены в наборы шесть вариантов, соответствующий концепции доступа public, внутренний, friend, protected, private и сочетание клавиш. Например может иметь разные значки для метода, в зависимости от того, является ли это открытый, защищенный или закрытый.  
  
 Следующее перечисление задает обычно имена для каждого набора значков и указывает связанный индекс. Например, исходя из перечисления, можно указать индекс изображения для защищенного метода как `(int)IconImageIndex.Method + (int)IconImageIndex.AccessProtected`. Имена, в этом перечислении, при необходимости можно изменить.  
  
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
 [Реализация языковой службы прежних версий](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [Общие сведения о службе устаревшего языка](../../extensibility/internals/legacy-language-service-overview.md)   
 [Регистрация языковой службы прежних версий](../../extensibility/internals/registering-a-legacy-language-service1.md)   
 [Средство синтаксического анализа и сканер языковой службы прежних версий](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)
