---
title: "Реализация службы языка прежних версий | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Реализация языковые службы [платформа управляемых пакетов]"
ms.assetid: 5bcafdc5-f922-48f6-a12e-6c8507a79a05
caps.latest.revision: 26
caps.handback.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
---
# Реализация службы языка прежних версий
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Чтобы реализовать службу языка с помощью управляемых границы пакетов \(MPF\), необходимо создать класс из <xref:Microsoft.VisualStudio.Package.LanguageService> класс реализуется в следующих абстрактные методы и свойства:  
  
-   Метод <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>  
  
-   Метод <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>  
  
-   Метод <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>  
  
-   Свойство <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A>.  
  
 Соответствующие инструкции см. ниже дополнительные сведения о реализации этих методов и свойств.  
  
 Для поддержки дополнительных функций, служба языка может создать класс, производный от одного из классов службы языка MPF; например, для поддержки дополнительных команд меню, необходимо создать класс из <xref:Microsoft.VisualStudio.Package.ViewFilter> класс переопределяет несколько команд и методы обработки \(см.  <xref:Microsoft.VisualStudio.Package.ViewFilter> дополнительные сведения\).  <xref:Microsoft.VisualStudio.Package.LanguageService> класс содержит несколько методов, которые вызываются для создания новых экземпляров различных классов и переопределите соответствующий метод создания для предоставления экземпляр класса.  Например, необходимо переопределить <xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A> метод  <xref:Microsoft.VisualStudio.Package.LanguageService> класс для возврата экземпляра ваших  <xref:Microsoft.VisualStudio.Package.ViewFilter> класс.  См. раздел "создания пользовательских классов" для получения дополнительных сведений.  
  
 Служба языка может также предоставить свои собственные значки, которые используются во многих местах.  Например, если список завершения IntelliSense отображается каждый элемент в списке может иметь значок, связанный с ним маркирующ элемент в качестве метода, класс пространство имен, свойства или все действия, необходимые для выбранного языка.  Эти значки используются во всех списках IntelliSense **Панель переходов**и  **Список ошибок** окно задачи.  См. раздел "образов службы языка" ниже.  
  
## Метод GetLanguagePreferences  
 <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> метод всегда возвращает один и тот же экземпляр a  <xref:Microsoft.VisualStudio.Package.LanguagePreferences> класс.  Можно использовать базу <xref:Microsoft.VisualStudio.Package.LanguagePreferences> класс если не требуется никаких дополнительных параметров для службы языка.  Классы службы языка MPF принимают наличие хотя бы причины <xref:Microsoft.VisualStudio.Package.LanguagePreferences> класс.  
  
### Пример  
 В этом примере показана типичная реализация <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> метод.  В этом примере используется база <xref:Microsoft.VisualStudio.Package.LanguagePreferences> класс.  
  
```c#  
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
  
## Метод GetScanner  
 Этот метод возвращает экземпляр  <xref:Microsoft.VisualStudio.Package.IScanner> объект, реализующий линия\-ориентированные анализатор и средство чтения, используемые для получения токены и их типы и триггеры.  Используемый в данный модуль чтения <xref:Microsoft.VisualStudio.Package.Colorizer> класс для колоризации хотя средство чтения может также использоваться для получения токена, как прелюдия типы и триггеры на более сложной операции анализа.  Необходимо предоставить класс, который реализует <xref:Microsoft.VisualStudio.Package.IScanner> интерфейс и необходимо реализовать все методы  <xref:Microsoft.VisualStudio.Package.IScanner> интерфейс.  
  
### Пример  
 В этом примере показана типичная реализация <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> метод.  `TestScanner` класс реализует  <xref:Microsoft.VisualStudio.Package.IScanner> интерфейс \(не показан\).  
  
```c#  
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
  
## Метод ParseSource  
 Анализирует исходный файл на основе нескольких различных причин.  Получатель этому методу, a <xref:Microsoft.VisualStudio.Package.ParseRequest> объект, который описывает, что ожидается из указанной операции анализа.  <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод вызывается более сложное средство синтаксического анализа, который определяет функциональность и область токена.  <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод используется в поддержке операций IntelliSense, а также проверка парности фигурных скобок.  Даже если не поддерживает такие необходимые операции будет по\-прежнему должны возвращать допустимым <xref:Microsoft.VisualStudio.Package.AuthoringScope> объект, и требуется создать класс, реализующий  <xref:Microsoft.VisualStudio.Package.AuthoringScope> интерфейс и реализует все методы в этом интерфейсе.  Можно вернуть значение NULL из всех методов, но <xref:Microsoft.VisualStudio.Package.AuthoringScope> сам объект не должен иметь значение NULL.  
  
### Пример  
 В этом примере показана минимальная реализация <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод и  <xref:Microsoft.VisualStudio.Package.AuthoringScope> класс, достаточный для разрешения языковую службу для компилирования и без поддержки организации цикла по фактически любой более продвинутых функциях.  
  
```c#  
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
  
## Свойство name  
 Это свойство возвращает имя языковой службы.  Это должен быть тот же указанному имени, когда служба языка была зарегистрирована.  Это имя используется в нескольких местах, что видно <xref:Microsoft.VisualStudio.Package.LanguagePreferences> класс, где имя используется для доступа к реестру.  Имя, возвращаемое этим свойством, необходимо локализовать, так как он используется в реестре для записи реестра и ключевых имен.  
  
### Пример  
 Данный пример иллюстрирует одну возможную реализацию <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A> свойство.  Обратите внимание, что здесь имя задано жестко. фактическое имя должно быть получено из файла ресурсов, поэтому его можно использовать в зарегистрировать службу языка \(см. [Регистрация службы языка](../../extensibility/internals/registering-a-legacy-language-service1.md)\).  
  
```c#  
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
  
## Создав пользовательские классы  
 Следующие методы в отдельных классах можно переопределить, чтобы обеспечить экземпляры ваших собственных версий каждого класса.  
  
### в классе LanguageService  
  
|Метод|Возвращаемый класс|Описание|  
|-----------|------------------------|--------------|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateCodeWindowManager%2A>|<xref:Microsoft.VisualStudio.Package.CodeWindowManager>|Для поддержки пользовательских дополнения к представлению текста.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A>|<xref:Microsoft.VisualStudio.Package.DocumentProperties>|Для поддержки настраиваемых свойств документа.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>|<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>|Поддержка **Панель переходов**.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionFunction>|Поддержка функции в шаблонах фрагмента кода.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionProvider>|Поддерживать фрагменты кода \(обычно этот метод не переопределен\).|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateParseRequest%2A>|<xref:Microsoft.VisualStudio.Package.ParseRequest>|Поддержка настройку <xref:Microsoft.VisualStudio.Package.ParseRequest> структура \(обычно этот метод не переопределен\).|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateSource%2A>|<xref:Microsoft.VisualStudio.Package.Source>|Поддержка исходный код форматирования, определяющий символов выделения комментариев и настройка сигнатурой метода.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A>|<xref:Microsoft.VisualStudio.Package.ViewFilter>|Дополнительные команды меню поддержки.|  
|<xref:Microsoft.VisualStudio.Package.Source.GetColorizer%2A>|<xref:Microsoft.VisualStudio.Package.Colorizer>|Для поддержки выбора синтаксиса этот метод обычно не переопределен\).|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>|<xref:Microsoft.VisualStudio.Package.LanguagePreferences>|Для поддержки доступа к предпочтениям языка.  Этот метод необходимо реализовывать но может возвращать экземпляр базового класса.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>|<xref:Microsoft.VisualStudio.Package.IScanner>|Предоставить анализатор, используемое для определения типов маркеров на линии.  Этот метод необходимо реализовывать и <xref:Microsoft.VisualStudio.Package.IScanner> из.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringScope>|Предоставить анализатор, используемое для определения возможностей и область в пределах всего исходный файл.  Этот метод необходимо реализовывать и должен возвращать экземпляр данной версии <xref:Microsoft.VisualStudio.Package.AuthoringScope> класс.  Если требуется поддержка выбрать, синтаксиса, который требует <xref:Microsoft.VisualStudio.Package.IScanner> средство синтаксического анализа, возвращенное  <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> метод\), можно выполнять никаких действий в этом методе, кроме извлечения версия  <xref:Microsoft.VisualStudio.Package.AuthoringScope> класс методам, все они возвращают значение NULL.|  
  
### в классе источника  
  
|Метод|Возвращаемый класс|Описание|  
|-----------|------------------------|--------------|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A>|<xref:Microsoft.VisualStudio.Package.CompletionSet>|Для настройки отображения завершения IntelliSense перечисляются \(обычно этот метод не переопределен\).|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A>|<xref:Microsoft.VisualStudio.Package.DocumentTask>|Для поддержки метки в списке задач список ошибок; в частности, поддержка функций, открыв файл и переходе к линии, которая вызвала ошибку.|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateMethodData%2A>|<xref:Microsoft.VisualStudio.Package.MethodData>|Для настройки отображения подсказок сведения о параметрах IntelliSense.|  
|<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>|<xref:Microsoft.VisualStudio.Package.CommentInfo>|Для поддержки выделения комментариев кода.|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateAuthoringSink%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringSink>|Для сбора сведений во время операции анализа.|  
  
### в классе AuthoringScope  
  
|Метод|Возвращаемый класс|Описание|  
|-----------|------------------------|--------------|  
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A>|<xref:Microsoft.VisualStudio.Package.Declarations>|Предоставляет список объявлений как элементы или типы.  Этот метод необходимо реализовывать но может возвращать значение NULL.  Если этот метод возвращает значение допустимого объекта, то объект должен быть экземпляром вашей версии <xref:Microsoft.VisualStudio.Package.Declarations> класс.|  
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetMethods%2A>|<xref:Microsoft.VisualStudio.Package.Methods>|Предоставляет список сигнатур метода для заданного контекста.  Этот метод необходимо реализовывать но может возвращать значение NULL.  Если этот метод возвращает значение допустимого объекта, то объект должен быть экземпляром вашей версии <xref:Microsoft.VisualStudio.Package.Methods> класс.|  
  
## Образы службы языка  
 Чтобы предоставить список значков, который будет использоваться на протяжении языковой службы, переопределите <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> метод  <xref:Microsoft.VisualStudio.Package.LanguageService> класс, и возвращает  <xref:System.Windows.Forms.ImageList> содержать значки.  Base <xref:Microsoft.VisualStudio.Package.LanguageService> загрузки класса по умолчанию набор значков.  Поскольку можно задать явный индекс образа в тех местах, которым нужны значки, как размещаются в собственный список образа до полностью автоматически.  
  
### Образы, используемые в списках завершения IntelliSense  
 Для завершения IntelliSense перечисляются индекс образа определяет для каждого элемента <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> метод   <xref:Microsoft.VisualStudio.Package.Declarations> класс, который необходимо переопределить, если требуется указать индекс образа.  Значение, возвращенное <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> метод индекс в списке, предоставленного для образа  <xref:Microsoft.VisualStudio.Package.CompletionSet> конструктор класса и тот же список, возвращаемый из образа  <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> метод  <xref:Microsoft.VisualStudio.Package.LanguageService> класс \(можно изменить, список, используемый для образа  <xref:Microsoft.VisualStudio.Package.CompletionSet> при переопределении  <xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A> метод  <xref:Microsoft.VisualStudio.Package.Source> класс, чтобы указать другой список образа\).  
  
### Образы, используемые в панели переходов  
 **Панель переходов** отображает списки типов и членов и используются для быстрой навигации могут отображаться значки.  Эти значки получаются из <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> метод  <xref:Microsoft.VisualStudio.Package.LanguageService> и не может быть переопределен в частности, класс  **Панель переходов**.  Указанные индексы, используемые для каждого элемента в полях со списком, если списки, представляющий поля со списком заполненные in <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> метод  <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> класс \(см.  [Поддержка панели навигации в языковую службу для прежних версий](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)\).  Эти индексы образа каким\-либо образом получаются из средства синтаксического анализа, обычно в версию <xref:Microsoft.VisualStudio.Package.Declarations> класс.  Как получаются все индексы до вас.  
  
### Образы, используемые в окне список ошибок задач  
 После <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> средство синтаксического анализа метода \(см.  <xref:Microsoft.VisualStudio.Package.AuthoringSink> \) встречает ошибку и передает эту ошибку в  **Список ошибок** метод  [Средство синтаксического анализа языка прежних версий службы и сканера](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)класс ошибки сообщается в  <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> окно задачи.  Значок могут быть связаны с каждым элементом, отображаются в окне задач и значка поступает из одного списка, возвращаемого из образа <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> метод  <xref:Microsoft.VisualStudio.Package.LanguageService> класс.  По умолчанию функциональности классов MPF не отображать образ с сообщением об ошибке.  Однако можно переопределить эту расширения функциональности путем наследования от класса <xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A> класс и переопределение  <xref:Microsoft.VisualStudio.Package.Source> метод.  В этом методе создании новой <xref:Microsoft.VisualStudio.Package.DocumentTask> объект.  Перед возвратом этот объект можно воспользоваться <xref:Microsoft.VisualStudio.Shell.Task.ImageIndex%2A> свойство  <xref:Microsoft.VisualStudio.Package.DocumentTask> объект, для которого задается индекс образа.  Это посмотрело бы что\-то, как в следующем примере.  Обратите внимание, что `TestIconImageIndex` перечисление, в котором перечислены все значки и относится к данному примеру.  Можно использовать различные способы указания значки в службе языка.  
  
```c#  
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
  
## По умолчанию список завершения образа для службы языка  
 По умолчанию список образа предоставленный с классами службы языка базы MPF содержит несколько значков, связанных с элементами общего языка.  Большая часть этих значки располагаются в наборах 6 изменений, соответствующий открытый, внутренний, принципах доступа, закрытыми, защищенными и ярлыка.  Например, можно иметь различные значки для метода в зависимости от того, является ли она открытыми, защищенными или закрыто.  
  
 Следующее перечисление определяет стандартные имена для каждого набора значка и задает соответствующий индекс.  Например, согласно перечислении, можно указать индекс образа для защищенного метода как `(int)IconImageIndex.Method + (int)IconImageIndex.AccessProtected`.  Можно изменить имена в этом перечислении нужным образом.  
  
```c#  
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
  
## См. также  
 [Реализация службы языка прежних версий](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [Общие сведения о службе устаревших языка](../../extensibility/internals/legacy-language-service-overview.md)   
 [Регистрация службы языка](../../extensibility/internals/registering-a-legacy-language-service1.md)   
 [Средство синтаксического анализа языка прежних версий службы и сканера](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)