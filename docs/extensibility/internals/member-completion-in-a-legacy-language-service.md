---
title: Завершение члена в языковую службу прежних версий | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense, Member Completion tool tip
- Member Completion, supporting in language services [managed package framework]
- language services [managed package framework], IntelliSense Member Completion
ms.assetid: 500f718d-9028-49a4-8615-ba95cf47fc52
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0cc22190c9228d2e166be94ed0d5cc78105e2404
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31134036"
---
# <a name="member-completion-in-a-legacy-language-service"></a>Завершение члена в языковую службу прежних версий
Завершение IntelliSense член является всплывающей подсказки, которая отображает список возможных элементов в конкретной области, например класс, структуру, перечисление или пространства имен. Например в C#, если пользователь вводит «this» последующей точкой, список всех членов класса или структуры в текущей области представлены в список, из которого пользователь может выбрать.  
  
 Managed package framework (MPF) предоставляет поддержку всплывающей подсказки и работа с перечнем в подсказке; все, что нужно — взаимодействие от средства синтаксического анализа в качестве источника данных, который отображается в списке.  
  
 Прежних версий языка службы реализованы как часть пакета VSPackage, но новой реализации возможностей службы языка можно выполнить с помощью расширений MEF. Подробнее см. в разделе [расширение редактора и языковые службы](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Мы рекомендуем начать использовать новый редактор API, как можно быстрее. Это повысит быстродействие языковой службы и позволяют воспользоваться преимуществами новых функций редактора.  
  
## <a name="how-it-works"></a>Принцип работы  
 Ниже приведены два способа, в которых отображается список элементов с помощью MPF классов.  
  
-   Позиционирования курсора на идентификаторе или после знака завершения элемента и выбрав **список членов** из **IntelliSense** меню.  
  
-   <xref:Microsoft.VisualStudio.Package.IScanner> Сканера обнаруживает знака завершения элемента и задает триггер маркера для <xref:Microsoft.VisualStudio.Package.TokenTriggers> этого символа.  
  
 Символ завершения члена указывает членом класса, структуры или перечисления следовать. Например, в C# или Visual Basic — символ завершения член `.`, тогда как в C++ символ является `.` или `->`. Значение триггера при сканировании символ выберите член.  
  
### <a name="the-intellisense-member-list-command"></a>Команда List член IntelliSense  
 <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> Команда инициирует вызов <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> метод <xref:Microsoft.VisualStudio.Package.Source> класса и <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> метод, в свою очередь, вызывает <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод синтаксического анализа с причиной по синтаксического анализа <xref:Microsoft.VisualStudio.Package.ParseReason>.  
  
 Средство синтаксического анализа определяет контекст текущей позиции, а также токен в группе или непосредственно перед текущей позиции. На основе этого токена, выводится список объявлений. Например, в C#, при наведении курсора на член класса и выберите **список членов**, получить список всех членов класса. Если навести курсор после периода, следующее за переменной объекта, отображается список всех членов класса, которые представляет. Обратите внимание, если курсор находится в элементе при отображении списка членов, выбрав элемент из списка заменяет член, в которой находится курсор на одно из списка.  
  
### <a name="the-token-trigger"></a>Токен триггера  
 <xref:Microsoft.VisualStudio.Package.TokenTriggers> Триггер инициирует вызов <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> метод <xref:Microsoft.VisualStudio.Package.Source> класса и <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> метод, в свою очередь, вызывает средство синтаксического анализа с причиной по синтаксического анализа <xref:Microsoft.VisualStudio.Package.ParseReason> (если токен триггер также включены <xref:Microsoft.VisualStudio.Package.TokenTriggers> флаг, синтаксический анализ причина заключается в <xref:Microsoft.VisualStudio.Package.ParseReason> объединяющие Выбор членов и выделение фигурная скобка).  
  
 Средство синтаксического анализа определяет контекст текущей позиции, а также введенную до знак выберите элемент. На основе данных он создает список всех членов запрошенной области. Этот список объявлений хранится в <xref:Microsoft.VisualStudio.Package.AuthoringScope> объект, возвращаемый из <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод. Если возвращаются все объявления, отображается всплывающая подсказка завершения члена. Подсказка управляется экземпляром <xref:Microsoft.VisualStudio.Package.CompletionSet> класса.  
  
## <a name="enabling-support-for-member-completion"></a>Включение поддержки для завершения члена  
 Необходимо иметь `CodeSense` запись реестра значение 1, поддерживают все операции IntelliSense. Эта запись реестра можно задать именованный параметр, передаваемый <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> атрибута пользователя, связанного с языкового пакета. Классы службы языка прочесть значение этой записи реестра из <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> свойство <xref:Microsoft.VisualStudio.Package.LanguagePreferences> класса.  
  
 Если сканер возвращает токен активации <xref:Microsoft.VisualStudio.Package.TokenTriggers>, программу parser возвращает список объявлений, затем отображается элемент списка завершения.  
  
## <a name="supporting-member-completion-in-the-scanner"></a>Поддержка завершения члена в сканера  
 Сканер должен иметь возможность определить знака завершения элемента и установить токена активации <xref:Microsoft.VisualStudio.Package.TokenTriggers> при синтаксическом анализе этим символом.  
  
### <a name="example"></a>Пример  
 Ниже приведен упрощенный пример обнаруживать символ завершения члена и задав соответствующую <xref:Microsoft.VisualStudio.Package.TokenTriggers> флаг. Данный пример является исключительно для демонстрационных целей. Предполагается, что сканер содержит метод `GetNextToken` , определяет и возвращает токенов из текстовой строки. В примере кода просто устанавливает триггер при каждом обнаружении правильный тип символа.  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestScanner : IScanner  
    {  
        private Lexer lex;  
        private const char memberSelectChar = '.';  
  
        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,  
                                                   ref int state)  
        {  
            bool foundToken = false  
            string token = lex.GetNextToken();  
            if (token != null)  
            {  
                foundToken = true;  
                char c = token[0];  
                if (c == memberSelectChar)  
                {  
                        tokenInfo.Trigger |= TokenTriggers.MemberSelect;  
                }  
            }  
            return foundToken;  
        }  
    }  
}  
```  
  
## <a name="supporting-member-completion-in-the-parser"></a>Поддержка завершения члена в средстве синтаксического анализа  
 Для завершения член <xref:Microsoft.VisualStudio.Package.Source> класса вызывает <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> метод. Список необходимо реализовать в классе, который является производным от <xref:Microsoft.VisualStudio.Package.Declarations> класса. В разделе <xref:Microsoft.VisualStudio.Package.Declarations> класс подробные сведения о методах, которые необходимо реализовать.  
  
 Средство синтаксического анализа вызывается с <xref:Microsoft.VisualStudio.Package.ParseReason> или <xref:Microsoft.VisualStudio.Package.ParseReason> при типизированных знака выбора элемента. Расположение, заданное в <xref:Microsoft.VisualStudio.Package.ParseRequest> объект находится сразу после элемента выберите символ. Средство синтаксического анализа необходимо собирать имена всех элементов, которые могут присутствовать в списке членов в этой конкретной точке в исходном коде. Затем средство синтаксического анализа необходимо выделить текущую строку для определения области, которые требуются пользователю, связанным с символом выберите член.  
  
 Этой области основан на тип идентификатора до знак выберите элемент. Например, в C#, если переменная-член `languageService` , имеет тип `LanguageService`, введите **languageService.** Создает список всех членов `LanguageService` класса. Также в C# введя **это.** Создает список всех членов класса в текущей области.  
  
### <a name="example"></a>Пример  
 В примере показан один из способов заполнения <xref:Microsoft.VisualStudio.Package.Declarations> списка. Предполагается, что средство синтаксического анализа объявление создает и добавляет его в список путем вызова `AddDeclaration` метод `TestAuthoringScope` класса.  
  
```csharp  
using System.Collections;  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    internal class TestDeclaration  
    {  
        public string Name;            // Name of declaration  
        public int     TypeImageIndex; // Glyph index  
        public string Description;     // Description of declaration  
  
        public TestDeclaration(string name, int typeImageIndex, string description)  
        {  
            this.Name = name;  
            this.TypeImageIndex = typeImageIndex;  
            this.Description = description;  
        }  
    }  
  
    //===================================================  
    internal class TestDeclarations : Declarations  
    {  
        private ArrayList declarations;  
  
        public TestDeclarations()  
            : base()  
        {  
            declarations = new ArrayList();  
        }  
  
        public void AddDeclaration(TestDeclaration declaration)  
        {  
            declarations.Add(declaration);  
        }  
  
        //////////////////////////////////////////////////////////////////////  
        // Declarations of class methods that must be implemented.  
        public override int GetCount()  
        {  
            // Return the number of declarations to show.  
            return declarations.Count;  
        }  
  
        public override string GetDescription(int index)  
        {  
            // Return the description of the specified item.  
            string description = "";  
            if (index >= 0 && index < declarations.Count)  
            {  
                description = ((TestDeclaration)declarations[index]).Description;  
            }  
            return description;  
        }  
  
        public override string GetDisplayText(int index)  
        {  
            // Determine what is displayed in the tool tip list.  
            string text = null;  
            if (index >= 0 && index < declarations.Count)  
            {  
                text = ((TestDeclaration)declarations[index]).Name;  
            }  
            return text;  
        }  
  
        public override int GetGlyph(int index)  
        {  
            // Return index of image to display next to the display text.  
            int imageIndex = -1;  
            if (index >= 0 && index < declarations.Count)  
            {  
                imageIndex = ((TestDeclaration)declarations[index]).TypeImageIndex;  
            }  
            return imageIndex;  
        }  
  
        public override string GetName(int index)  
        {  
            string name = null;  
            if (index >= 0 && index < declarations.Count)  
            {  
                name = ((TestDeclaration)declarations[index]).Name;  
            }  
            return name;  
        }  
    }  
  
    //===================================================  
    public class TestAuthoringScope : AuthoringScope  
    {  
        private TestDeclarations declarationsList;  
  
        public void AddDeclaration(TestDeclaration declaration)  
        {  
            if (declaration != null)  
            {  
                if (declarationsList == null)  
                {  
                    declarationsList = new TestDeclarations();  
                }  
                declarationsList.AddDeclaration(declaration);  
            }  
        }  
  
        public override Declarations GetDeclarations(IVsTextView view,  
                                                     int line,  
                                                     int col,  
                                                     TokenInfo info,  
                                                     ParseReason reason)  
        {  
            return declarationsList;  
        }  
  
        /////////////////////////////////////////////////  
        // Remainder of AuthoringScope methods not shown.  
        /////////////////////////////////////////////////  
    }  
  
    //===================================================  
    class TestLanguageService : LanguageService  
    {  
        public override AuthoringScope ParseSource(ParseRequest req)  
        {  
            TestAuthoringScope scope = new TestAuthoringScope();  
            if (req.Reason == ParseReason.MemberSelect ||  
                req.Reason == ParseReason.MemberSelectAndHighlightBraces)  
            {  
                // Gather list of declarations based on what the user  
                // has typed so far. In this example, this list is an array of  
                // MemberDeclaration objects (a helper class you might implement  
                // to hold member declarations).  
                // How this list is gathered is dependent on the parser  
                // and is not shown here.  
                MemberDeclarations memberDeclarations;  
                memberDeclarations = GetDeclarationsForScope();  
  
                // Now populate the Declarations list in the authoring scope.  
                // GetImageIndexBasedOnType() is a helper method you  
                // might implement to convert a member type to an index into  
                // the image list returned from the language service.  
                foreach (MemberDeclaration dec in memberDeclarations)  
                {  
                    scope.AddDeclaration(new TestDeclaration(  
                                             dec.Name,  
                                             GetImageIndexBasedOnType(dec.Type),  
                                             dec.Description));  
                }  
            }  
            return scope;  
        }  
    }  
}  
```