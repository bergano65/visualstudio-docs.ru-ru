---
title: "Поддержка фрагментов кода в языковую службу для прежних версий | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "фрагменты кода, поддержки в языковые службы"
  - "фрагменты кода, поддержки в языковые службы [платформа управляемых пакетов]"
  - "Поддержка фрагментов кода языковые службы [платформа управляемых пакетов]"
ms.assetid: 7490325b-acee-4c2d-ac56-1cd5db1a1083
caps.latest.revision: 28
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 28
---
# Поддержка фрагментов кода в языковую службу для прежних версий
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Фрагмент кода — это часть кода, вставляемый в файл исходного кода. Фрагмент, сам является шаблон на основе XML с набором полей. Эти поля будут выделены после вставки фрагмента кода, а также может иметь различные значения в зависимости от контекста, в которую вставляется фрагмент. Сразу после вставки фрагмента кода, служба языка можно форматировать фрагмента кода.  
  
 При вставке фрагмента в специальных изменить режим, позволяющий полям фрагмента для перехода с помощью клавиши TAB. Поля могут поддерживать стиле IntelliSense раскрывающихся меню. Пользователь фиксирует фрагмент в исходный файл, введя ввод или клавиши ESC. Дополнительные сведения о фрагментах см. в разделе [Фрагменты кода](../../ide/code-snippets.md).  
  
 Устаревший языковые службы реализуются как частью VSPackage, но это использование расширений MEF новый способ реализации возможностей службы языка. Для получения дополнительных см [Пошаговое руководство: Реализация фрагменты кода](../../extensibility/walkthrough-implementing-code-snippets.md).  
  
> [!NOTE]
>  Мы рекомендуем начать использовать новый редактор API как можно быстрее. Это улучшает производительность службы языка и позволяют воспользоваться преимуществами новых функций редактора.  
  
## Управляемые пакета поддержки Framework фрагменты кода  
 Платформа управляемых пакетов \(MPF\) поддерживает большинство функциональность фрагмента, чтение шаблона для вставки фрагмента и включение специальный режим редактирования. Поддержка осуществляется с помощью <xref:Microsoft.VisualStudio.Package.ExpansionProvider> класса.  
  
 При <xref:Microsoft.VisualStudio.Package.Source> создается экземпляр класса, <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A> метод <xref:Microsoft.VisualStudio.Package.LanguageService> класса вызывается для получения <xref:Microsoft.VisualStudio.Package.ExpansionProvider> объекта \(Обратите внимание, что базовый <xref:Microsoft.VisualStudio.Package.LanguageService> класс всегда возвращает новый <xref:Microsoft.VisualStudio.Package.ExpansionProvider> объекта для каждого <xref:Microsoft.VisualStudio.Package.Source> объекта\).  
  
 MPF не поддерживает функции расширения. Функция расширения является именованным, внедренных в шаблоне фрагмент и возвращает одно или несколько значений, которые следует поместить в поле. Значения возвращаются в языке собственно через службу <xref:Microsoft.VisualStudio.Package.ExpansionFunction> объекта.<xref:Microsoft.VisualStudio.Package.ExpansionFunction> Объект должен быть реализован языковую службу для поддержки функций расширения.  
  
## Предоставление поддержки для фрагментов кода  
 Чтобы включить поддержку для фрагментов кода, необходимо предоставить или установить фрагменты кода и необходимо предоставить средства для вставки этих фрагментов. Существует поддержка фрагментов кода на три этапа:  
  
1.  Установка файлов фрагментов.  
  
2.  Включение фрагменты кода для службы языка.  
  
3.  Вызов <xref:Microsoft.VisualStudio.Package.ExpansionProvider> объекта.  
  
### Установка файлов фрагментов  
 Все фрагменты кода для языка, сохраняются как шаблоны в XML\-файлы, обычно один фрагмент шаблон каждого файла. Дополнительные сведения о схеме XML для шаблонов фрагмент кода в разделе [Справочник по схеме фрагментов кода](../../ide/code-snippets-schema-reference.md). Каждый фрагмент шаблона определяется с идентификатором языка. Этот язык, идентификатор, указанный в реестре и помещается в `Language` атрибут тег \< Code \> в шаблоне.  
  
 Обычно есть два места, где хранятся файлы фрагментов кода шаблона: \(1\) там, где был установлен язык и \(2\) в папку пользователя. Эти расположения добавляются в реестр таким образом, Visual Studio **Диспетчер фрагментов кода** можно найти фрагменты кода. Созданные пользователем фрагменты кода хранятся папки пользователя.  
  
 Макет обычно папки для файлов шаблонов установленных фрагмент выглядит следующим образом: *\[Корневого\_каталога\_установки\]*\\*\[TestLanguage\]*\\Snippets\\*\[LCID\]*\\Snippets.  
  
 *\[Корневого\_каталога\_установки\]* является язык устанавливается в папку.  
  
 *\[TestLanguage\]* является имя языка, как имя папки.  
  
 *\[LCID\]* идентификатор языкового стандарта. Это локализованных версий собственные фрагменты сохраняются. Например, код языка для английского языка — 1033, поэтому *\[LCID\]* заменяется 1033.  
  
 Необходимо указать один дополнительный файл, и это индексный файл, обычно называется SnippetsIndex.xml или ExpansionsIndex.xml \(можно использовать любой допустимый с расширением .xml\). Обычно этот файл хранится в *\[Корневого\_каталога\_установки\]*\\*\[TestLanguage\]* папки и указывает точное местоположение папки фрагментов а также идентификатор языка и идентификатор GUID языковой службы, которую использует фрагменты кода. Точный путь файла индекса записываются в реестр, как описано ниже в «Установка записи реестра». Ниже приведен пример файла SnippetsIndex.xml:  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<SnippetCollection>  
    <Language Lang="Testlanguage" Guid="{b614a40a-80d9-4fac-a6ad-fc2868fff7cd}">  
        <SnippetDir>  
            <OnOff>On</OnOff>  
            <Installed>true</Installed>  
            <Locale>1033</Locale>  
            <DirPath>%InstallRoot%\TestLanguage\Snippets\%LCID%\Snippets\</DirPath>  
            <LocalizedName>Snippets</LocalizedName>  
        </SnippetDir>  
    </Language>  
</SnippetCollection>  
```  
  
 Тег \< язык \> указывает код языка \( `Lang` атрибут\) и идентификатор GUID языковой службы.  
  
 В этом примере предполагается, что службе языка установлен в папке установки Visual Studio. LCID % заменяется идентификатора пользователя текущего языкового стандарта. Несколько тегов \< SnippetDir \> можно добавить, один для каждого другой каталог и языкового стандарта. Кроме того папка фрагмент может содержать вложенные папки, каждый из которых определяется в файле индекса с тегом \< SnippetSubDir \>, который внедряется в тег \< SnippetDir \>.  
  
 Пользователи также могут создавать собственные фрагменты кода для вашего языка. Они обычно хранятся в папке параметров пользователя, например *\[TestDocs\]*\\Code Snippets\\*\[TestLanguage\]*\\Test фрагменты кода, где *\[TestDocs\]* расположение папки параметры пользователя для Visual Studio.  
  
 Следующие элементы подстановки можно поместить в пути, сохраненному в теге \< DirPath \> в файле индекса.  
  
|Элемент|Описание|  
|-------------|--------------|  
|% LCID %|Идентификатор языка.|  
|% Корневого\_каталога\_установки|Корневой каталог установки для Visual Studio, например, C:\\Program Files\\Microsoft Visual Studio 8.|  
|% ProjDir %|Папка, содержащая текущий проект.|  
|% ProjItem %|Папка, содержащая текущий элемент проекта.|  
|% TestDocs %|Папки в папке параметров пользователя, например, C:\\Documents and Settings\\*\[имя\_пользователя\]*Мои \\My Documents\\Visual Studio\\8.|  
  
### Включение фрагменты кода для службы языка  
 Фрагменты кода можно включить для службы языка, добавив <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> атрибут VSPackage \(в разделе [Регистрация службы языка](../../extensibility/internals/registering-a-legacy-language-service1.md) Подробные сведения\).<xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.ShowRoots%2A> И <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.SearchPaths%2A> параметры необязательны, но должно включать `SearchPaths` именованный параметр, чтобы проинформировать **Диспетчер фрагментов кода** расположения собственные фрагменты.  
  
 Ниже приведен пример использования этого атрибута:  
  
```  
[ProvideLanguageCodeExpansion(  
         typeof(TestSnippetLanguageService),  
         "Test Snippet Language",          // Name of language used as registry key  
         0,                               // Resource ID of localized name of language service  
         "Test Snippet Language",        // Name of Language attribute in snippet template  
         @"%InstallRoot%\Test Snippet Language\Snippets\%LCID%\SnippetsIndex.xml",  // Path to snippets index  
         SearchPaths = @"%InstallRoot%\Test Snippet Language\Snippets\%LCID%\")]    // Path to snippets  
```  
  
### Вызов поставщика расширения  
 Языковая служба управляет вставки любой фрагмент кода, а также способ вставки вызывается.  
  
## Вызов поставщика расширения для фрагментов кода  
 Существует два способа вызова поставщика расширения: с помощью команды меню или с помощью клавиш из списка завершения.  
  
### Вставка фрагмента кода с помощью команды меню  
 Чтобы использовать команду меню для отображения обозревателя фрагмент, добавить команду меню, а затем вызовите <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> метод <xref:Microsoft.VisualStudio.Package.ExpansionProvider> интерфейс в ответ, команды меню.  
  
1.  Добавьте команды и кнопки файл .vsct. Можно найти в инструкции [Пошаговое руководство. Создание команды меню с помощью шаблона пакета Visual Studio](../Topic/Walkthrough:%20Creating%20a%20Menu%20Command%20By%20Using%20the%20Visual%20Studio%20Package%20Template.md).  
  
2.  Производный класс от <xref:Microsoft.VisualStudio.Package.ViewFilter> класса и переопределить <xref:Microsoft.VisualStudio.Package.ViewFilter.QueryCommandStatus%2A> для указания поддержки для новой команды меню. В этом примере всегда включает команду меню.  
  
    ```c#  
    using Microsoft.VisualStudio.Package;  
  
    namespace TestLanguagePackage  
    {  
        class TestViewFilter : ViewFilter  
        {  
            public TestViewFilter(CodeWindowManager mgr, IVsTextView view)  
                : base(mgr, view)  
            {  
            }  
  
            protected override int QueryCommandStatus(ref Guid guidCmdGroup,  
                                                      uint nCmdId)  
            {  
                int hr = base.QueryCommandStatus(ref guidCmdGroup, nCmdId);  
                // If the base class did not recognize the command then  
                // see if we can handle the command.  
                if (hr == (int)Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_UNKNOWNGROUP)  
                {  
                    if (guidCmdGroup == GuidList.guidTestLanguagePackageCmdSet)  
                    {  
                        if (nCmdId == PkgCmdIDList.InvokeCodeSnippetsBrowser)  
                        {  
                            hr = (int)(OLECMDF.OLECMDF_SUPPORTED | OLECMDF.OLECMDF_ENABLED);  
                        }  
                    }  
                }  
                return hr;  
            }  
        }  
    }  
    ```  
  
3.  Переопределение <xref:Microsoft.VisualStudio.Package.ViewFilter.HandlePreExec%2A> метод <xref:Microsoft.VisualStudio.Package.ViewFilter> для получения <xref:Microsoft.VisualStudio.Package.ExpansionProvider> и вызовите <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> метод для этого объекта.  
  
    ```c#  
    using Microsoft.VisualStudio.Package;  
  
    namespace TestLanguagePackage  
    {  
        class TestViewFilter : ViewFilter  
        {  
            public override bool HandlePreExec(ref Guid guidCmdGroup,  
                                               uint nCmdId,  
                                               uint nCmdexecopt,  
                                               IntPtr pvaIn,  
                                               IntPtr pvaOut)  
            {  
                if (base.HandlePreExec(ref guidCmdGroup,  
                                       nCmdId,  
                                       nCmdexecopt,  
                                       pvaIn,  
                                       pvaOut))  
                {  
                    // Base class handled the command.  Do nothing more here.  
                    return true;  
                }  
  
                if (guidCmdGroup == GuidList.guidTestLanguagePackageCmdSet)  
                {  
                    if (nCmdId == PkgCmdIDList.InvokeCodeSnippetsBrowser)  
                    {  
                        ExpansionProvider ep = this.GetExpansionProvider();  
                        if (this.TextView != null && ep != null)  
                        {  
                            bool bDisplayed = ep.DisplayExpansionBrowser(  
                                this.TextView,  
                                "TestLanguagePackage Snippet:",  
                                null,  
                                false,  
                                null,  
                                false);  
                        }  
                        return true;   // Handled the command.  
                    }  
                }  
                return false;   // Did not handle the command.  
            }  
        }  
    }  
  
    ```  
  
     Следующие методы в <xref:Microsoft.VisualStudio.Package.ExpansionProvider> класса вызываются средой Visual Studio в данном порядке во время вставки фрагмента:  
  
4.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnItemChosen%2A>  
  
5.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>  
  
6.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>  
  
7.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>  
  
8.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>  
  
     После <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A> вызывается метод, вставленного фрагмента и <xref:Microsoft.VisualStudio.Package.ExpansionProvider> объект находится в режиме специальные редактирования, используемая для изменения фрагмент, который только что добавили.  
  
### Вставка фрагмента кода с помощью ярлыка  
 Реализация ярлык из списка завершения гораздо сложнее, чем реализация команды меню. Сначала необходимо добавить Shortcut фрагментов кода в список завершения IntelliSense. Затем необходимо обнаружить, когда имя ярлыка фрагмент был вставлен в результате завершения. Наконец, необходимо получить заголовок фрагмента и пути с помощью сочетания имени и передать эти данные в <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> метод <xref:Microsoft.VisualStudio.Package.ExpansionProvider> метод.  
  
 Чтобы добавить фрагмент ярлыки в список завершения слова, добавьте их в <xref:Microsoft.VisualStudio.Package.Declarations> объекта в своей <xref:Microsoft.VisualStudio.Package.AuthoringScope> класса. Необходимо убедиться, можно указать сочетание имени фрагмента. Пример см. в разделе [Пошаговое руководство: Получение списка установленных текстов \(реализация прежних версий\)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md).  
  
 Можно определить вставки сочетание клавиш для фрагмента кода в <xref:Microsoft.VisualStudio.Package.Declarations.OnAutoComplete%2A> метод <xref:Microsoft.VisualStudio.Package.Declarations> класса. Поскольку имя фрагмента уже вставлен в файл исходного кода, его необходимо удалить при вставке расширение.<xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> Метод принимает интервал, который описывает точку вставки фрагмента, если диапазон включает имя весь фрагмент кода в исходном файле, это имя заменяется фрагмента кода.  
  
 Ниже приведена версия <xref:Microsoft.VisualStudio.Package.Declarations> класс, обрабатывающий вставки фрагмента заданное имя ярлыка. Другие методы в <xref:Microsoft.VisualStudio.Package.Declarations> класса опущены для ясности. Обратите внимание, что конструктор этого класса принимает <xref:Microsoft.VisualStudio.Package.LanguageService> объекта. Может быть передан в вашей версии <xref:Microsoft.VisualStudio.Package.AuthoringScope> объекта \(например, реализация <xref:Microsoft.VisualStudio.Package.AuthoringScope> может принимать <xref:Microsoft.VisualStudio.Package.LanguageService> объекта в конструкторе и передайте этот объект в вашей `TestDeclarations` конструктор класса\).  
  
```  
[C#]  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    internal class TestDeclarations : Declarations  
    {  
        private ArrayList       declarations;  
        private LanguageService languageService;  
        private TextSpan        commitSpan;  
  
        public TestDeclarations(LanguageService langService)  
            : base()  
        {  
            languageService = langService;  
            declarations = new ArrayList();  
        }  
  
        // This method is used to add declarations to the internal list.  
        public void AddDeclaration(TestDeclaration declaration)  
        {  
            declarations.Add(declaration);  
        }  
  
        // This method is called to get the string to commit to the source buffer.  
        // Note that the initial extent is only what the user has typed so far.  
        public override string OnCommit(IVsTextView textView,  
                                        string textSoFar,  
                                        char commitCharacter,  
                                        int index,  
                                        ref TextSpan initialExtent)  
        {  
            // We intercept this call only to get the initial extent  
            // of what was committed to the source buffer.  
            commitSpan = initialExtent;  
  
            return base.OnCommit(textView,  
                                 textSoFar,  
                                 commitCharacter,  
                                 index,  
                                 ref initialExtent);  
        }  
  
        // This method is called after the string has been committed to the source buffer.  
        public override char OnAutoComplete(IVsTextView textView,  
                                            string committedText,  
                                            char commitCharacter,  
                                            int index)  
        {  
            TestDeclaration item = declarations[index] as TestDeclaration;  
            if (item != null)  
            {  
                // In this example, TestDeclaration identifies types with a string.  
                // You can choose a different approach.  
                if (item.Type == "snippet")  
                {  
                    Source src = languageService.GetSource(textView);  
                    if (src != null)  
                    {  
                        ExpansionProvider ep = src.GetExpansionProvider();  
                        if (ep != null)  
                        {  
                            string title;  
                            string path;  
                            int commitLength = commitSpan.iEndIndex - commitSpan.iStartIndex;  
                            if (commitLength < committedText.Length)  
                            {  
                                // Replace everything that was inserted  
                                // so calculate the span of the full  
                                // insertion, taking into account what  
                                // was inserted when the commitSpan  
                                // was obtained in the first place.  
                                commitSpan.iEndIndex += (committedText.Length - commitLength);  
                            }  
  
                            if (ep.FindExpansionByShortcut(textView,  
                                                           committedText,  
                                                           commitSpan,  
                                                           true,  
                                                           out title,  
                                                           out path))  
                            {  
                                ep.InsertNamedExpansion(textView,  
                                                        title,  
                                                        path,  
                                                        commitSpan,  
                                                        false);  
                            }  
                        }  
                    }  
                }  
            }  
            return '\0';  
        }  
    }  
}  
```  
  
 Если языковая служба возвращает сокращенное имя, он вызывает <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FindExpansionByShortcut%2A> метод, чтобы получить заголовок фрагмент файла и кода. Языковая служба вызывает <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> метод <xref:Microsoft.VisualStudio.Package.ExpansionProvider> класса для вставки фрагмента кода. Следующие методы вызываются средой Visual Studio в определенном порядке в <xref:Microsoft.VisualStudio.Package.ExpansionProvider> класса во время вставки этого фрагмента кода:  
  
1.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>  
  
2.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>  
  
3.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>  
  
4.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>  
  
 Дополнительные сведения о получении списка фрагментов кода, установленного для службы языка в разделе [Пошаговое руководство: Получение списка установленных текстов \(реализация прежних версий\)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md).  
  
## Реализация класса ExpansionFunction  
 Функция расширения является именованным, внедренных в шаблоне фрагмент и возвращает одно или несколько значений, которые следует поместить в поле. Для поддержки функций расширения в службе языка, должен быть производным от класса <xref:Microsoft.VisualStudio.Package.ExpansionFunction> класса и реализовать <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetCurrentValue%2A> метод. Необходимо переопределить <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A> метод <xref:Microsoft.VisualStudio.Package.LanguageService> класса для возврата нового экземпляра версии <xref:Microsoft.VisualStudio.Package.ExpansionFunction> класс для каждой функции расширения, которые вы поддерживаете. Если требуется поддержка список возможных значений из функции расширения, необходимо также переопределить <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetIntellisenseList%2A> метод <xref:Microsoft.VisualStudio.Package.ExpansionFunction> класса, чтобы получить список этих значений.  
  
 Функции расширения, принимающие аргументы или нужен доступ к другие поля не должен быть связан с редактируемое поле, как расширения поставщика может не быть инициализирован полностью к моменту вызова функции расширения. В результате функция расширения не могут получать значения аргументов или любому другому полю.  
  
### Пример  
 Ниже приведен пример способ вызова функции простого расширения `GetName` могут быть реализованы. Эта функция расширения добавляет номер к имени базового класса каждый раз экземпляров функции расширения \(соответствующее при каждом фрагменте кода вставляется\).  
  
```c#  
using Microsoft.VisualStudio.Package;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        private int classNameCounter = 0;  
  
        public override ExpansionFunction CreateExpansionFunction(  
            ExpansionProvider provider,  
            string functionName)  
        {  
            ExpansionFunction function = null;  
            if (functionName == "GetName")  
            {  
                ++classNameCounter;  
                function = new TestGetNameExpansionFunction(provider, classNameCounter);  
            }  
            return function;  
        }  
    }  
  
    internal class TestGetNameExpansionFunction : ExpansionFunction  
    {  
        private int nameCount;  
  
        TestGetNameExpansionFunction(ExpansionProvider provider, int counter)  
            : base(provider)  
        {  
            nameCount = counter;  
        }  
  
        public override string GetCurrentValue()  
        {  
            string name = "TestClass";  
            name += nameCount.ToString();  
            return name;  
        }  
    }  
}  
```  
  
## См. также  
 [Компоненты прежних версий языка службы](../../extensibility/internals/legacy-language-service-features1.md)   
 [Регистрация службы языка](../../extensibility/internals/registering-a-legacy-language-service1.md)   
 [Фрагменты кода](../../ide/code-snippets.md)   
 [Пошаговое руководство: Получение списка установленных текстов \(реализация прежних версий\)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)