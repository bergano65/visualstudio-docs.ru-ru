---
title: Поддержка фрагментов кода в службе языка Legacy (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- snippets, supporting in language services
- code snippets, supporting in language services [managed package framework]
- language services [managed package framework], supporting code snippets
ms.assetid: 7490325b-acee-4c2d-ac56-1cd5db1a1083
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ad871eb73341f6ab87229687e2a6df898ffda32d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704914"
---
# <a name="support-for-code-snippets-in-a-legacy-language-service"></a>Поддержка фрагментов кода в языковой службе прежних версий
Фрагмент кода — это часть кода, вставляемый в исходный файл. Фрагмент сам по себе представляет собой шаблон на основе XML с набором полей. Эти поля выделены после вставки фрагмента и могут иметь различные значения в зависимости от контекста, в который вставляется фрагмент. Сразу после ввода фрагмента языковая служба может отформатировать фрагмент.

 Фрагмент вставляется в специальный режим репетиторства, который позволяет перемещаться по полям фрагмента с помощью ключа TAB. Поля могут поддерживать меню в стиле IntelliSense. Пользователь фиксирует фрагмент исходного файла, введя либо ENTER, либо ключ ESC. Чтобы узнать больше о фрагментах, пожалуйста, смотрите [фрагменты кода](../../ide/code-snippets.md).

 Устаревшие языковые службы реализуются как часть VSPackage, но новый способ реализации функций языкового сервиса заключается в использовании расширений MEF. Чтобы узнать больше, смотрите [Walkthrough: Реализация фрагментов кода](../../extensibility/walkthrough-implementing-code-snippets.md).

> [!NOTE]
> Мы рекомендуем вам начать использовать новый API редактора как можно скорее. Это повысит производительность вашего языкового сервиса и позволит вам воспользоваться новыми функциями редактора.

## <a name="managed-package-framework-support-for-code-snippets"></a>Управляемая пакетная поддержка фрагментов кода
 Платформа управляемого пакета (MPF) поддерживает большинство функций фрагмента, от чтения шаблона до вставки фрагмента и включения специального режима отодкивания. Поддержка управляется <xref:Microsoft.VisualStudio.Package.ExpansionProvider> через класс.

 При <xref:Microsoft.VisualStudio.Package.Source> мгновенном воспроизведении класса <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A> вызывается <xref:Microsoft.VisualStudio.Package.LanguageService> метод в классе <xref:Microsoft.VisualStudio.Package.ExpansionProvider> для получения объекта <xref:Microsoft.VisualStudio.Package.LanguageService> (обратите внимание, что базовый класс всегда возвращает новый <xref:Microsoft.VisualStudio.Package.ExpansionProvider> объект для каждого <xref:Microsoft.VisualStudio.Package.Source> объекта).

 MPF не поддерживает функции расширения. Функция расширения — это функция, названная в шаблонфрагмента и возвращающая одно или несколько значений, которые должны быть помещены в поле. Значения возвращаются самой языковой службой <xref:Microsoft.VisualStudio.Package.ExpansionFunction> через объект. Объект <xref:Microsoft.VisualStudio.Package.ExpansionFunction> должен быть реализован языковой службой для поддержки функций расширения.

## <a name="providing-support-for-code-snippets"></a>Оказание поддержки фрагментам кода
 Для поддержки фрагментов кода необходимо предоставить или установить фрагменты, а также предоставить пользователю средства для вставки этих фрагментов. Существует три шага, позволяющих поддерживать фрагменты кода:

1. Установка файлов фрагментов.

2. Включение фрагментов кода для языковой службы.

3. Ссылаясь на <xref:Microsoft.VisualStudio.Package.ExpansionProvider> объект.

### <a name="installing-the-snippet-files"></a>Установка фрагментных файлов
 Все фрагменты для языка хранятся в виде шаблонов в файлах XML, обычно один шаблон фрагмента на файл. Подробную информацию о схеме XML, используемой для [Code Snippets Schema Reference](../../ide/code-snippets-schema-reference.md)шаблонов фрагментов фрагментов кода, см. Каждый шаблон фрагмента идентифицируется с идентификатором языка. Этот идентификатор языка указан в `Language` реестре \<и вводится в атрибут Кода> тегва в шаблоне.

 Обычно существуют два места, где хранятся файлы шаблонов фрагментов: 1), где был установлен ваш язык, и 2) в папке пользователя. Эти места добавляются в реестр, так что Visual Studio **код фрагменты менеджер** может найти фрагменты. В папке пользователя хранятся фрагменты, созданные пользователем.

 Типичная компоновка папок для установленных файлов шаблонов фрагментов выглядит следующим образом: *«InstallRoot»*\\ *(TestLanguage)*«Snippets»\\ *(SnipPETS)*(Фрагменты).

 *«InstallRoot»* — это папка, в котором установлен ваш язык.

 *«TestLanguage»* — это название вашего языка как имя папки.

 *«LCID»* — это идентификатор локализации. Таким образом хранятся локализованные версии фрагментов. Например, идентификатор языка для английского языка составляет 1033, поэтому *«LCID»* заменяется 1033.

 Один дополнительный файл должен быть поставлен, и это файл индекса, обычно называемый SnippetsIndex.xml или ExpansionsIndex.xml (вы можете использовать любое действительное имя файла, заканчивающийся в .xml). Этот файл обычно хранится в папке *«InstallRoot»*\\ *(TestLanguage)* и определяет точное местоположение папки фрагментов, а также идентификатор языка и GUID языковой службы, использующей фрагменты. Точный путь индексного файла внегоризуемого реестра, как описано позднее в "Установка записей реестра". Вот пример файла SnippetsIndex.xml:

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

 В \<теге Language> указаний `Lang` идентификатор языка (атрибут) и языковая служба GUID.

 Этот пример предполагает, что вы установили языковую службу в папке установки Visual Studio. %LCID% заменяется текущим идентификатором локализации пользователя. Несколько \<меток SnippetDir> могут быть добавлены, по одному для каждого другого каталога и локализации. Кроме того, папка фрагмента может содержать субфайдеры, каждая из \<которых идентифицируется в индексном \<файле с тегом SnippetSubDir>, встроенным в тег SnippetDir>.

 Пользователи также могут создавать свои собственные фрагменты для вашего языка. Они обычно хранятся в папке настроек пользователя, например, *«TestDocs»*(Code\\Snippets)*«TestLanguage» (TestCode*Snippets), где *«TestDocs»* — это расположение папки настроек пользователя для Visual Studio.

 Следующие элементы замены могут быть \<помещены в путь, хранящийся в теге DirPath> в файле индекса.

|Элемент|Описание|
|-------------|-----------------|
|%LCID%|Код языка.|
|%УстановкаКорне%|Корневая папка установки для Visual Studio, например, C: «Программные файлы»Microsoft Visual Studio 8.|
|%ProjDir%|Фолдер, содержащий текущий проект.|
|%ProjItem%|Фолдер, содержащий текущий элемент проекта.|
|%TestDocs%|Например, в папке настроек пользователя, например, C:«Документы и настройки\\ *(имя пользователя)*«Мои документы» (Visual Studio) 8.|

### <a name="enabling-code-snippets-for-your-language-service"></a>Включение фрагментов кода для вашей языковой службы
 Фрагменты кода можно включить для своей <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> языковой службы, добавив атрибут в свой VSPackage (подробнее см. [Регистрация языковой службы Legacy).](../../extensibility/internals/registering-a-legacy-language-service1.md) Параметры <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.ShowRoots%2A> <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.SearchPaths%2A> и параметры неявляются, но `SearchPaths` вы должны включить указанный параметр, чтобы сообщить **менеджеру фрагментов кода** о местонахождении фрагментов.

 Ниже приводится пример того, как использовать этот атрибут:

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
 Языковая служба контролирует вставку любого фрагмента кода, а также способ вызова вставки.

## <a name="calling-the-expansion-provider-for-code-snippets"></a>Вызов поставщика расширения для фрагментов кода
 Существует два способа вызвать поставщика расширения: с помощью команды меню или с помощью ярлыка из списка завершения.

### <a name="inserting-a-code-snippet-by-using-a-menu-command"></a>Вставка фрагмента кода с помощью команды меню
 Чтобы использовать команду меню для отображения фрагмента браузера, <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> вы <xref:Microsoft.VisualStudio.Package.ExpansionProvider> добавляете команду меню, а затем вызовите метод в интерфейсе в ответ на эту команду меню.

1. Добавьте команду и кнопку в файл .vsct. Вы можете найти инструкции для этого при [создании расширения с командой меню.](../../extensibility/creating-an-extension-with-a-menu-command.md)

2. Вывести класс <xref:Microsoft.VisualStudio.Package.ViewFilter> из класса и <xref:Microsoft.VisualStudio.Package.ViewFilter.QueryCommandStatus%2A> переопределить метод, чтобы указать поддержку новой команды меню. Этот пример всегда позволяет командовать меню.

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

3. Переопределить <xref:Microsoft.VisualStudio.Package.ViewFilter.HandlePreExec%2A> метод в <xref:Microsoft.VisualStudio.Package.ViewFilter> классе, <xref:Microsoft.VisualStudio.Package.ExpansionProvider> чтобы получить <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> объект и вызвать метод на этом объекте.

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

     Следующие методы <xref:Microsoft.VisualStudio.Package.ExpansionProvider> в классе называются Visual Studio в заданном порядке в процессе вставки фрагмента:

4. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnItemChosen%2A>

5. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>

6. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>

7. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>

8. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>

     После <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A> вызова метода фрагмент был вставлен и <xref:Microsoft.VisualStudio.Package.ExpansionProvider> объект находится в специальном режиме изменения, используемом для изменения только что вставленного фрагмента.

### <a name="inserting-a-code-snippet-by-using-a-shortcut"></a>Вставка фрагмента кода с помощью ярлыка
 Реализация ярлыка из списка завершения гораздо более вовлечена, чем реализация команды меню. Сначала необходимо добавить фрагментные ярлыки в список завершения слов IntelliSense. Затем необходимо определить, когда в результате завершения было вставлено имя фрагмента ярлыка. Наконец, необходимо получить название фрагмента и путь, используя имя ярлыка, и передать эту информацию методу <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> метода. <xref:Microsoft.VisualStudio.Package.ExpansionProvider>

 Чтобы добавить фрагментные ярлыки в список завершения <xref:Microsoft.VisualStudio.Package.Declarations> слов, <xref:Microsoft.VisualStudio.Package.AuthoringScope> добавьте их к объекту в классе. Вы должны убедиться, что вы можете определить ярлык как фрагмент имя. Например, [см. Walkthrough: Получение списка установленных фрагментов кода (Наследие реализации)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md).

 Можно обнаружить вставку фрагмента кода в <xref:Microsoft.VisualStudio.Package.Declarations.OnAutoComplete%2A> методе <xref:Microsoft.VisualStudio.Package.Declarations> класса. Поскольку имя фрагмента уже было вставлено в исходный файл, оно должно быть удалено при вставке расширения. Метод <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> занимает промежуток, который описывает точку вставки для фрагмента; если пролет включает в себя все имя фрагмента в исходном файле, это имя заменяется фрагментом.

 Вот версия <xref:Microsoft.VisualStudio.Package.Declarations> класса, который обрабатывает фрагмент вставки с учетом ярлыка имя. Другие методы <xref:Microsoft.VisualStudio.Package.Declarations> в классе были опущены для ясности. Обратите внимание, что конструктор этого <xref:Microsoft.VisualStudio.Package.LanguageService> класса берет объект. Это может быть передано из <xref:Microsoft.VisualStudio.Package.AuthoringScope> вашей версии объекта <xref:Microsoft.VisualStudio.Package.AuthoringScope> (например, <xref:Microsoft.VisualStudio.Package.LanguageService> реализация класса может привести объект в `TestDeclarations` свой конструктор и передать объект на ваш конструктор класса).

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

 Когда языковая служба получает имя ярлыка, она называет <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FindExpansionByShortcut%2A> метод получения имени файла и заголовка фрагмента кода. Затем языковая служба <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> вызывает <xref:Microsoft.VisualStudio.Package.ExpansionProvider> метод в классе для вставки фрагмента кода. Следующие методы называются Visual Studio в <xref:Microsoft.VisualStudio.Package.ExpansionProvider> данном порядке в классе в процессе вставки фрагмента:

1. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>

2. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>

3. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>

4. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>

   Для получения дополнительной информации о получении списка установленных фрагментов кода для вашей языковой службы, [см.](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)

## <a name="implementing-the-expansionfunction-class"></a>Внедрение класса ExpansionFunction
 Функция расширения — это функция, названная в шаблонфрагмента и возвращающая одно или несколько значений, которые должны быть помещены в поле. Для поддержки функций расширения в языковой службе <xref:Microsoft.VisualStudio.Package.ExpansionFunction> необходимо извлечь <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetCurrentValue%2A> из класса класс и реализовать метод. Затем необходимо переопределить <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A> метод <xref:Microsoft.VisualStudio.Package.LanguageService> в классе, чтобы вернуть новое мгновенное <xref:Microsoft.VisualStudio.Package.ExpansionFunction> воспроизведение вашей версии класса для каждой функции расширения, поддерживаемой вами. Если вы поддерживаете список возможных значений из функции <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetIntellisenseList%2A> расширения, <xref:Microsoft.VisualStudio.Package.ExpansionFunction> необходимо также переопределить метод в классе, чтобы вернуть список этих значений.

 Функция расширения, которая требует аргументов или должна получить доступ к другим полям, не должна быть связана с исходируемым полем, поскольку поставщик расширения может быть не полностью инициализирован к моменту вызова функции расширения. В результате функция расширения не может получить значение своих аргументов или любого другого поля.

### <a name="example"></a>Пример
 Вот пример того, как может `GetName` быть реализована простая функция расширения, называемая. Эта функция расширения прикладывает число к названию базового класса каждый раз, когда функция расширения мгновенно (что соответствует каждому моменту вставки связанного фрагмента кода).

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
- [Функции языковой службы прежних версий](../../extensibility/internals/legacy-language-service-features1.md)
- [Регистрация языковой службы прежних версий](../../extensibility/internals/registering-a-legacy-language-service1.md)
- [Фрагменты кода](../../ide/code-snippets.md)
- [Пошаговое руководство. Получение списка фрагментов кода (реализация прежних версий)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)
