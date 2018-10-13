---
title: Поддержка фрагментов кода в языковой службе прежних версий | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snippets, supporting in language services
- code snippets, supporting in language services [managed package framework]
- language services [managed package framework], supporting code snippets
ms.assetid: 7490325b-acee-4c2d-ac56-1cd5db1a1083
caps.latest.revision: 29
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 71098c0dda7c06f446658c4970d0b6cf2e35e55e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49198514"
---
# <a name="support-for-code-snippets-in-a-legacy-language-service"></a>Поддержка фрагментов кода в языковой службе прежних версий
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Фрагмент кода — это часть кода, вставляемый в файл исходного кода. Фрагмент кода, сам является шаблон на основе XML с помощью набора полей. Эти поля будут выделены после вставки фрагмента кода, а также может иметь разные значения в зависимости от контекста, в которой вставляется фрагмент кода. Сразу после вставки фрагмента, языковой службы можно форматировать фрагмента кода.  
  
 В режиме с специальные изменение поля этого фрагмента, чтобы перейти с помощью клавиши TAB будет вставлен фрагмент кода. Поля может поддерживать стиле IntelliSense раскрывающихся меню. Пользователь фиксирует фрагмент в исходный файл, введя ввод или клавиши ESC. Дополнительные сведения о фрагментах см. в разделе [фрагменты кода](../../ide/code-snippets.md).  
  
 Устаревший языковой службы реализуются как часть пакета VSPackage, но новый способ реализовать функции языковой службы является использование расширений MEF. Дополнительные сведения см. в разделе [Пошаговое руководство: реализация фрагментов кода](../../extensibility/walkthrough-implementing-code-snippets.md).  
  
> [!NOTE]
>  Мы рекомендуем начать использовать новый редактор API как можно скорее. Это улучшит производительность службы языка и позволяют воспользоваться преимуществами новых функций редактора.  
  
## <a name="managed-package-framework-support-for-code-snippets"></a>Управляемые поддерживают Framework пакета для фрагментов кода  
 Managed package framework (MPF) поддерживает большинство функциональность фрагмента, чтение шаблона для вставки фрагмента кода и включение специальный режим правки. Поддержка осуществляется через <xref:Microsoft.VisualStudio.Package.ExpansionProvider> класса.  
  
 При <xref:Microsoft.VisualStudio.Package.Source> создается экземпляр класса, <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A> метод в <xref:Microsoft.VisualStudio.Package.LanguageService> класса вызывается для получения <xref:Microsoft.VisualStudio.Package.ExpansionProvider> объекта (Обратите внимание, что базовый <xref:Microsoft.VisualStudio.Package.LanguageService> класс всегда возвращает новый <xref:Microsoft.VisualStudio.Package.ExpansionProvider> для каждой <xref:Microsoft.VisualStudio.Package.Source> объект).  
  
 MPF не поддерживает функции расширения. Функции расширения является именованную функцию, который внедряется в шаблон фрагмента и возвращает одно или несколько значений, которые следует поместить в поле. Значения возвращаются в данном языке самой через службы <xref:Microsoft.VisualStudio.Package.ExpansionFunction> объекта. <xref:Microsoft.VisualStudio.Package.ExpansionFunction> Объект должен быть реализован языковой службы для поддержки функций расширений.  
  
## <a name="providing-support-for-code-snippets"></a>Предоставление поддержки для фрагментов кода  
 Чтобы включить поддержку для фрагментов кода, необходимо предоставить или установить фрагменты кода, и необходимо предоставить средства для вставки этих фрагментов. Существует три шага для включения возможности поддержки для фрагментов кода:  
  
1.  Установка файлы фрагментов кода.  
  
2.  Включение фрагментов кода для языковой службы.  
  
3.  Вызов <xref:Microsoft.VisualStudio.Package.ExpansionProvider> объекта.  
  
### <a name="installing-the-snippet-files"></a>Установка файлы фрагментов кода  
 Все фрагменты кода для языка, хранятся как шаблоны в XML-файлов, обычно один шаблон фрагмента каждого файла. Дополнительные сведения о схеме XML, используемый для шаблоны фрагментов кода, см. в разделе [Справочник по схеме фрагментов кода](../../ide/code-snippets-schema-reference.md). Каждый шаблон фрагмента идентифицируется с идентификатором языка. Этот язык, идентификатор, указанный в реестре и помещается в `Language` атрибут \<кода > тега в шаблоне.  
  
 Обычно есть два места, где хранятся файлы фрагментов шаблона: 1) там, где был установлен язык и (2) в папки. Эти расположения добавляются в реестр таким образом, Visual Studio **Диспетчер фрагментов кода** можно найти фрагменты кода. Папки является местом хранения фрагментов, созданных пользователем.  
  
 Макет типичная папка для файлов шаблонов установленных фрагмент кода выглядит следующим образом: *[InstallRoot]*\\ *[TestLanguage]* \Snippets\\ *[кодязыка]* \Snippets.  
  
 *[InstallRoot]*  является язык устанавливается в папку.  
  
 *[TestLanguage]*  — это имя вашего языка, как имя папки.  
  
 *[LCID]*  идентификатор языкового стандарта. Это локализованных версиях собственные фрагменты хранятся. Например, код языка для английского языка — 1033, таким образом *[LCID]* заменяется 1033.  
  
 Указывается одним дополнительным файлом и файлом индекса, обычно называется SnippetsIndex.xml или ExpansionsIndex.xml (можно использовать любое допустимое имя файла, заканчивающиеся на .xml). Этот файл обычно хранятся в *[InstallRoot]*\\ *[TestLanguage]* папки и указывает точное местоположение папки фрагменты как и идентификатор языка и идентификатор GUID языка Служба, которая использует фрагменты кода. Точный путь к файлу индекса помещается в реестр, как описано далее в «Установка записи реестра». Ниже приведен пример файла SnippetsIndex.xml:  
  
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
  
 \<Языка > тег указывает код языка ( `Lang` атрибут) и GUID языковой службы.  
  
 В этом примере предполагается, что вы установили службы вашего языка в папке установки Visual Studio. % LCID % заменяется идентификатор пользователя текущего языкового стандарта. Несколько \<SnippetDir > теги могут добавляться, один для каждого другой каталог и языковой стандарт. Кроме того, папке фрагментов кода может содержать вложенные папки, каждый из которых определяется в файле индекса с \<SnippetSubDir > тег, который внедряется в \<SnippetDir > тег.  
  
 Пользователи также могут создавать свои собственные фрагменты кода для вашего языка. Эти значения обычно хранятся в папке параметры пользователя, например *[TestDocs]* \Code фрагменты\\ *[TestLanguage]* \Test фрагменты кода, где *[TestDocs]* расположение папки параметры для Visual Studio.  
  
 Следующие элементы подстановки может быть помещен в пути, сохраненному в \<DirPath > тег в файл индекса.  
  
|Элемент|Описание|  
|-------------|-----------------|  
|% LCID %|Идентификатор языка.|  
|% InstallRoot %|Корневой каталог установки для Visual Studio, например, C:\Program Files\Microsoft Visual Studio 8.|  
|% ProjDir %|Папка, содержащая текущий проект.|  
|% ProjItem %|Папка, содержащая текущий элемент проекта.|  
|% TestDocs %|Папка в папке параметры пользователя, например, C:\Documents and Settings\\ *[username]* Мои \My Documents\Visual Studio\8.|  
  
### <a name="enabling-code-snippets-for-your-language-service"></a>Включение фрагментов кода для языковой службы  
 Вы можете включить фрагменты кода для языковой службы, добавив <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> атрибута к VSPackage (см. в разделе [регистрация языковой службы прежних](../../extensibility/internals/registering-a-legacy-language-service1.md) сведения). <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.ShowRoots%2A> И <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.SearchPaths%2A> параметры являются необязательными, но должен включать `SearchPaths` именованный параметр, чтобы проинформировать **Диспетчер фрагментов кода** расположения собственные фрагменты.  
  
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
  
### <a name="calling-the-expansion-provider"></a>Вызов поставщика расширения  
 Языковая служба управляет вставку любой фрагмент кода, а также способ вставки вызывается.  
  
## <a name="calling-the-expansion-provider-for-code-snippets"></a>Вызов поставщика расширения для фрагментов кода  
 Существует два способа для вызова поставщика расширения: с помощью команды меню или с помощью ярлыка в списке завершения.  
  
### <a name="inserting-a-code-snippet-by-using-a-menu-command"></a>Вставка фрагмента кода с помощью команды меню  
 Чтобы использовать команды меню для отображения обозревателя на фрагмент кода, добавьте команду меню, а затем вызвать <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> метод в <xref:Microsoft.VisualStudio.Package.ExpansionProvider> интерфейс в ответ для этой команды меню.  
  
1.  Добавьте команды и кнопки в файл .vsct. Инструкции по выполнению этого [Пошаговое руководство: Создание меню команды с использованием шаблона пакета Visual Studio](http://msdn.microsoft.com/library/1985fa7d-aad4-4866-b356-a125b6a246de).  
  
2.  Наследуйте класс от <xref:Microsoft.VisualStudio.Package.ViewFilter> класса и переопределить <xref:Microsoft.VisualStudio.Package.ViewFilter.QueryCommandStatus%2A> метод, чтобы указать поддержку для новой команды меню. В этом примере включается всегда команду меню.  
  
    ```csharp  
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
  
3.  Переопределить <xref:Microsoft.VisualStudio.Package.ViewFilter.HandlePreExec%2A> метод в <xref:Microsoft.VisualStudio.Package.ViewFilter> для получения <xref:Microsoft.VisualStudio.Package.ExpansionProvider> и вызовите <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> метод для этого объекта.  
  
    ```csharp  
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
  
     Следующие методы в <xref:Microsoft.VisualStudio.Package.ExpansionProvider> класса вызываются средой Visual Studio в указанном порядке во время вставки фрагмента кода:  
  
4.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnItemChosen%2A>  
  
5.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>  
  
6.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>  
  
7.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>  
  
8.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>  
  
     После <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A> вызывается метод, фрагмента и <xref:Microsoft.VisualStudio.Package.ExpansionProvider> объект находится в режиме редактирования специальные, используемая для изменения фрагмент кода, который только что был вставлен.  
  
### <a name="inserting-a-code-snippet-by-using-a-shortcut"></a>Вставка фрагмента кода с помощью ярлыка  
 Ярлык в списке завершения реализуется гораздо больше усилий, чем реализация команды меню. Ярлыков фрагментов кода необходимо сначала добавить в список завершения слов IntelliSense. Затем необходимо обнаружить, когда в результате завершения была введена имя ярлыка фрагмента. Наконец, необходимо получить название фрагмента и пути, используя имя ярлыка и передать эту информацию <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> метод <xref:Microsoft.VisualStudio.Package.ExpansionProvider> метод.  
  
 Чтобы добавить ярлыков фрагментов кода в список завершения слова, добавьте их в <xref:Microsoft.VisualStudio.Package.Declarations> объект в вашей <xref:Microsoft.VisualStudio.Package.AuthoringScope> класса. Необходимо убедиться в том, можно указать, ярлык имени фрагмента кода. Например, см. в разделе [Пошаговое руководство: получение списка из установки фрагментов кода (реализация прежних версий)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md).  
  
 Можно обнаружить вставку ярлык фрагмента кода в <xref:Microsoft.VisualStudio.Package.Declarations.OnAutoComplete%2A> метод <xref:Microsoft.VisualStudio.Package.Declarations> класса. Так как уже был вставлен имени фрагмента в файл исходного кода, его необходимо удалить при вставке расширения. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> Метод принимает область, которая описывает точку вставки для фрагмента; Если диапазон включает в себя имя весь фрагмент кода в исходном файле, это имя заменяется фрагмента кода.  
  
 Здесь — это версия <xref:Microsoft.VisualStudio.Package.Declarations> класс, обрабатывающий Вставка фрагментов, получает имя ярлыка. Другие методы в <xref:Microsoft.VisualStudio.Package.Declarations> класс опущены для ясности. Обратите внимание, что конструктор этого класса принимает <xref:Microsoft.VisualStudio.Package.LanguageService> объекта. Может быть передан в из версии <xref:Microsoft.VisualStudio.Package.AuthoringScope> объекта (например, реализация <xref:Microsoft.VisualStudio.Package.AuthoringScope> может принимать <xref:Microsoft.VisualStudio.Package.LanguageService> объекта в конструкторе и передайте этот объект в вашей `TestDeclarations` конструктор класса).  
  
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
  
 Когда языковая служба возвращает имя ярлыка, она вызывает <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FindExpansionByShortcut%2A> метод, чтобы получить имя файла и кода заголовок фрагмента. Языковая служба затем вызывает <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> метод в <xref:Microsoft.VisualStudio.Package.ExpansionProvider> для вставки фрагмента кода. Следующие методы вызываются средой Visual Studio в заданном порядке в <xref:Microsoft.VisualStudio.Package.ExpansionProvider> класса во время вставки фрагмента кода:  
  
1.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>  
  
2.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>  
  
3.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>  
  
4.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>  
  
 Дополнительные сведения о получении списка фрагментов кода для языковой службы, см. в разделе [Пошаговое руководство: получение списка из установки фрагментов кода (реализация прежних версий)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md).  
  
## <a name="implementing-the-expansionfunction-class"></a>Реализация класса ExpansionFunction  
 Функции расширения является именованную функцию, который внедряется в шаблон фрагмента и возвращает одно или несколько значений, которые следует поместить в поле. Чтобы обеспечить поддержку функций расширений в службе языка, должен быть производным от класса <xref:Microsoft.VisualStudio.Package.ExpansionFunction> класса и реализуйте <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetCurrentValue%2A> метод. Необходимо переопределить <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A> метод в <xref:Microsoft.VisualStudio.Package.LanguageService> класса для возвращения нового экземпляра версии <xref:Microsoft.VisualStudio.Package.ExpansionFunction> класс для каждой функции расширения, вы поддерживаете. Если вы поддерживаете список возможных значений из функции расширения, необходимо также переопределить <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetIntellisenseList%2A> метод в <xref:Microsoft.VisualStudio.Package.ExpansionFunction> класса для возвращения списка этих значений.  
  
 Функции расширения, принимающие аргументы или требуется доступ к другие поля не должен быть связан с полем редактирования, как поставщик расширения не может полностью инициализировать моменту, когда вызывается функция расширения. Таким образом функции расширения не может получить значение аргументов или любое другое поле.  
  
### <a name="example"></a>Пример  
 Ниже приведен пример способ вызова функции простого расширения `GetName` могут быть реализованы. Данная функция расширения добавляет номер к имени базового класса при каждом создании экземпляра функции расширения (что соответствует каждый раз в фрагменте кода вставляется).  
  
```csharp  
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
  
## <a name="see-also"></a>См. также  
 [Функции службы устаревшего языка](../../extensibility/internals/legacy-language-service-features1.md)   
 [Регистрация языковой службы прежних версий](../../extensibility/internals/registering-a-legacy-language-service1.md)   
 [Фрагменты кода](../../ide/code-snippets.md)   
 [Пошаговое руководство. Получение списка фрагментов кода (реализация прежних версий)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)

