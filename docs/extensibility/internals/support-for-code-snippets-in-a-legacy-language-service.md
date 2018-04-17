---
title: Поддержка фрагментов кода в языковую службу прежних версий | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- snippets, supporting in language services
- code snippets, supporting in language services [managed package framework]
- language services [managed package framework], supporting code snippets
ms.assetid: 7490325b-acee-4c2d-ac56-1cd5db1a1083
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: eb62481b9ba2c42ed067275480ba137b151a483b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="support-for-code-snippets-in-a-legacy-language-service"></a>Поддержка фрагментов кода в языковую службу прежних версий
Фрагмент кода — это часть кода, вставляемый в файл исходного кода. Самого фрагмента является шаблоном на основе XML с набором полей. Эти поля будут выделены после вставки фрагмента кода, а также могут иметь разные значения в зависимости от контекста, в которую вставляется фрагмент. Сразу после вставки фрагмента кода, служба языка можно форматировать фрагмента кода.  
  
 В режиме с специальные редактирование полей фрагмента кода, осуществлять переходы с помощью клавиши TAB вставляется фрагмент. Поля могут поддерживать раскрывающихся меню IntelliSense стиля. Пользователь фиксирует фрагмент в исходный файл, введя ввод или клавиши ESC. Дополнительные сведения о фрагментах см. в разделе [фрагменты кода](../../ide/code-snippets.md).  
  
 Прежних версий языка службы реализованы как часть пакета VSPackage, но новой реализации возможностей службы языка можно выполнить с помощью расширений MEF. Подробнее см. в разделе [Пошаговое руководство: реализация фрагменты кода](../../extensibility/walkthrough-implementing-code-snippets.md).  
  
> [!NOTE]
>  Мы рекомендуем начать использовать новый редактор API, как можно быстрее. Это повысит быстродействие языковой службы и позволяют воспользоваться преимуществами новых функций редактора.  
  
## <a name="managed-package-framework-support-for-code-snippets"></a>Управляемые пакета поддержки Framework фрагменты кода  
 Managed package framework (MPF) поддерживает большинство функций фрагмент, считывать шаблона для вставки фрагмента кода и включение специальный режим редактирования. Поддержка осуществляется с помощью <xref:Microsoft.VisualStudio.Package.ExpansionProvider> класса.  
  
 При <xref:Microsoft.VisualStudio.Package.Source> создается экземпляр класса, <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A> метод в <xref:Microsoft.VisualStudio.Package.LanguageService> класса вызывается для получения <xref:Microsoft.VisualStudio.Package.ExpansionProvider> объекта (Обратите внимание, что базовый <xref:Microsoft.VisualStudio.Package.LanguageService> класс всегда возвращает новый <xref:Microsoft.VisualStudio.Package.ExpansionProvider> объекта для каждого <xref:Microsoft.VisualStudio.Package.Source> объект).  
  
 MPF не поддерживает функции расширения. Функция расширения является именованную функцию, внедренного в шаблоне фрагмент и возвращает одно или несколько значений, которые следует поместить в поле. Значения возвращаются в языке самой через службы <xref:Microsoft.VisualStudio.Package.ExpansionFunction> объекта. <xref:Microsoft.VisualStudio.Package.ExpansionFunction> Объект должен быть реализован для поддержки функций расширения языковой службы.  
  
## <a name="providing-support-for-code-snippets"></a>Предоставление поддержки для фрагментов кода  
 Чтобы включить поддержку для фрагментов кода, необходимо предоставить или установить фрагменты кода, и вы должны предоставить средства для вставки этих фрагментов. Существует три шага для включения функции поддержки для фрагментов кода.  
  
1.  Установка файлов фрагментов.  
  
2.  Включение фрагменты кода для службы языка.  
  
3.  Вызов <xref:Microsoft.VisualStudio.Package.ExpansionProvider> объекта.  
  
### <a name="installing-the-snippet-files"></a>Установка файлов фрагментов  
 Все фрагменты кода для языка, сохраняются как шаблоны в XML-файлы, обычно один фрагмент шаблон каждого файла. Дополнительные сведения о схеме XML, используемый для шаблоны фрагментов кода в разделе [Справочник по схеме фрагментов кода](../../ide/code-snippets-schema-reference.md). Каждый шаблон идентифицируется с идентификатором языка. Этот язык, идентификатор, указанный в разделе реестра и помещается в `Language` атрибут \<кода > тега в шаблоне.  
  
 Обычно есть два места, где хранятся файлы фрагментов шаблона: (1) где был установлен язык и (2) в папки. Эти расположения добавляются в реестр таким образом, Visual Studio **Диспетчер фрагментов кода** может найти фрагменты кода. Папки является которых хранятся фрагменты кода, созданных пользователем.  
  
 Макет обычно папку для файлов шаблонов установленных фрагмент выглядит следующим образом: *[Корневого_каталога_установки]*\\*[TestLanguage]*\Snippets\\*[LCID]*\Snippets.  
  
 *[Корневого_каталога_установки]*  является язык устанавливается в папку.  
  
 *[TestLanguage]*  является имя языка, как имя папки.  
  
 *[LCID]*  идентификатор языкового стандарта. Это локализованных версий собственные фрагменты, сохраняются. Например, код языка для английского языка — 1033, поэтому *[LCID]* заменяется 1033.  
  
 Необходимо указать один дополнительный файл и файл индекса, обычно называемый SnippetsIndex.xml или ExpansionsIndex.xml (можно использовать любое допустимое имя файла, в которых заканчиваются .xml). Этот файл обычно хранится в *[Корневого_каталога_установки]*\\*[TestLanguage]* папки и указывает точное расположение папки фрагментов а также идентификатор языка и идентификатор GUID языка Служба, которая использует фрагменты кода. Точный путь файла индекса переводится в реестр, как описано ниже в «Установка записи реестра». Ниже приведен пример файла SnippetsIndex.xml:  
  
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
  
 \<Языка > тег указывает код языка ( `Lang` атрибут) и идентификатор GUID языковой службы.  
  
 В этом примере предполагается, что вы установили языковой службы в папке установки Visual Studio. % LCID % заменяется идентификатор пользователя текущего языкового стандарта. Несколько \<SnippetDir > теги можно добавлять, один для каждого другой каталог и языковой стандарт. Кроме того, папки фрагментов может содержать вложенные папки, каждый из которых определяется в файле индекса с \<SnippetSubDir > тег, который внедряется в \<SnippetDir > тег.  
  
 Пользователи также могут создавать свои собственные фрагменты кода для конкретного языка. Они обычно хранятся в папке параметров пользователя, например *[TestDocs]*\Code фрагменты\\*[TestLanguage]*\Test фрагменты кода, где *[TestDocs]* расположение папки параметры для Visual Studio.  
  
 Следующие элементы подстановки может быть помещен в путь, хранящийся в \<DirPath > тег в файле индекса.  
  
|Элемент|Описание|  
|-------------|-----------------|  
|% LCID %|Идентификатор языка.|  
|% Корневого_каталога_установки %|Корневой каталог установки для Visual Studio, например, C:\Program Files\Microsoft Visual Studio 8.|  
|% ProjDir %|Папка, содержащая текущий проект.|  
|% ProjItem %|Папка, содержащая элемента текущего проекта.|  
|% TestDocs %|В папку пользователя параметры, например, C:\Documents and Settings\\*[username]*\My Documents\Visual Studio\8.|  
  
### <a name="enabling-code-snippets-for-your-language-service"></a>Включение фрагменты кода для службы языка  
 Фрагменты кода можно включить для службы языка, добавив <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> атрибут VSPackage (см. [регистрации службы языка для прежних версий](../../extensibility/internals/registering-a-legacy-language-service1.md) подробные сведения). <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.ShowRoots%2A> И <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.SearchPaths%2A> являются необязательными, однако следует включить `SearchPaths` именованный параметр, чтобы вы могли **Диспетчер фрагментов кода** расположения собственные фрагменты.  
  
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
 Языковая служба управляет вставку все фрагменты кода, а также способ вставки вызывается.  
  
## <a name="calling-the-expansion-provider-for-code-snippets"></a>Вызов поставщика расширения для фрагментов кода  
 Существует два способа вызова поставщика расширения: с помощью команды меню или с помощью клавиш из списка завершения.  
  
### <a name="inserting-a-code-snippet-by-using-a-menu-command"></a>Вставка фрагмента кода с помощью команды меню  
 Использовать команду меню для отображения обозревателя фрагмент кода, добавьте команду меню и затем вызвать <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> метод в <xref:Microsoft.VisualStudio.Package.ExpansionProvider> интерфейс в ответ для этой команды меню.  
  
1.  Добавьте команды и кнопку в vsct-файл. Можно найти в инструкции [создания расширения с помощью команды меню](../../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Производный класс <xref:Microsoft.VisualStudio.Package.ViewFilter> класса и переопределить <xref:Microsoft.VisualStudio.Package.ViewFilter.QueryCommandStatus%2A> метод, чтобы указать поддержку для новой команды меню. Этот пример всегда включает команду меню.  
  
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
  
     Следующие методы в <xref:Microsoft.VisualStudio.Package.ExpansionProvider> класса вызываются средой Visual Studio в определенном порядке во время вставки фрагмента кода:  
  
4.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnItemChosen%2A>  
  
5.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>  
  
6.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>  
  
7.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>  
  
8.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>  
  
     После <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A> вызывается метод, вставленного фрагмента и <xref:Microsoft.VisualStudio.Package.ExpansionProvider> объект находится в режиме редактирования специальные, используется для изменения только что вставленный фрагмент.  
  
### <a name="inserting-a-code-snippet-by-using-a-shortcut"></a>Вставка фрагмента кода с помощью ярлыка  
 Реализация ярлыки из списка завершения работает гораздо сложнее, чем реализуются команды меню. Сначала необходимо добавить Shortcut фрагментов кода в списке предложений IntelliSense. Затем необходимо обнаружить, когда имя ярлыка фрагмент был вставлен в результате завершения. Наконец, необходимо получить фрагмент заголовок и путь, с помощью сокращенных имен и передать эту информацию для <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> метод <xref:Microsoft.VisualStudio.Package.ExpansionProvider> метод.  
  
 Чтобы добавить Shortcut фрагментов кода в списке завершения слова, добавьте их в <xref:Microsoft.VisualStudio.Package.Declarations> объект в вашей <xref:Microsoft.VisualStudio.Package.AuthoringScope> класса. Необходимо убедиться, что сочетание клавиш для имени фрагмент можно определить. Пример см. в разделе [Пошаговое руководство: получение списка из установлен фрагменты кода (реализации прежних версий)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md).  
  
 Можно обнаружить вставку ярлык фрагмента кода в <xref:Microsoft.VisualStudio.Package.Declarations.OnAutoComplete%2A> метод <xref:Microsoft.VisualStudio.Package.Declarations> класса. Так как имя фрагмента уже вставлен в файл исходного кода, его необходимо удалить развертывание при вставке. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> Метод принимает интервал, который описывает вставляемого фрагмента; Если диапазон включает имя весь фрагмент кода в исходном файле, это имя заменяется фрагмента кода.  
  
 Здесь — это версия <xref:Microsoft.VisualStudio.Package.Declarations> класс, который обрабатывает вставки фрагмент кода получает имя ярлыка. Другие методы <xref:Microsoft.VisualStudio.Package.Declarations> класс опущены для ясности. Обратите внимание, что конструктор этого класса принимает <xref:Microsoft.VisualStudio.Package.LanguageService> объекта. Это может быть передан в вашей версии <xref:Microsoft.VisualStudio.Package.AuthoringScope> объекта (например, реализация <xref:Microsoft.VisualStudio.Package.AuthoringScope> может принимать <xref:Microsoft.VisualStudio.Package.LanguageService> объекта в конструкторе и передать этот объект в вашей `TestDeclarations` конструктор класса).  
  
```csharp  
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
  
 Если языковая служба возвращает имя ярлыка, он вызывает <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FindExpansionByShortcut%2A> для получения заголовка фрагмент имени файла и кода. Языковая служба вызывает <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> метод <xref:Microsoft.VisualStudio.Package.ExpansionProvider> класса для вставки фрагмента кода. Следующие методы вызываются средой Visual Studio в определенном порядке, в <xref:Microsoft.VisualStudio.Package.ExpansionProvider> класс во время вставки фрагмента кода:  
  
1.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>  
  
2.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>  
  
3.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>  
  
4.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>  
  
 Дополнительные сведения о получении списка фрагментов кода, установленные для службы языка. в разделе [Пошаговое руководство: получение списка из установлен фрагменты кода (реализации прежних версий)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md).  
  
## <a name="implementing-the-expansionfunction-class"></a>Реализация класса ExpansionFunction  
 Функция расширения является именованную функцию, внедренного в шаблоне фрагмент и возвращает одно или несколько значений, которые следует поместить в поле. Чтобы обеспечить поддержку функции расширения в службе языка, должен быть производным от класса <xref:Microsoft.VisualStudio.Package.ExpansionFunction> класса и реализовать <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetCurrentValue%2A> метод. Необходимо переопределить <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A> метод в <xref:Microsoft.VisualStudio.Package.LanguageService> класса для возврата нового экземпляра вашей версии <xref:Microsoft.VisualStudio.Package.ExpansionFunction> класса для каждой функции расширения, которые вы поддерживаете. Если требуется поддержка список возможных значений из функции расширения, необходимо также переопределить <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetIntellisenseList%2A> метод <xref:Microsoft.VisualStudio.Package.ExpansionFunction> класса, чтобы получить список этих значений.  
  
 Это расширение функция, которая принимает аргументы или нужен доступ к другие поля не должен быть связан с полем редактирования, как поставщика расширения не может полностью инициализировать к моменту вызова функции расширения. В результате функции расширения не могут получать значения аргументов или любого другого поля.  
  
### <a name="example"></a>Пример  
 Ниже приведен пример, как вызвать функцию простого расширения `GetName` могут быть реализованы. Эта функция расширения добавляют номер к имени базового класса при каждом экземпляров функции расширения (который соответствует каждый раз фрагмент кода вставляется).  
  
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
 [Возможности службы прежних версий языка](../../extensibility/internals/legacy-language-service-features1.md)   
 [Регистрация службы языка для прежних версий](../../extensibility/internals/registering-a-legacy-language-service1.md)   
 [Фрагменты кода](../../ide/code-snippets.md)   
 [Пошаговое руководство. Получение списка фрагментов кода (реализация прежних версий)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)