---
title: Завершение участников в языковой службе прежних версий | Документация Майкрософт
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
- IntelliSense, Member Completion tool tip
- Member Completion, supporting in language services [managed package framework]
- language services [managed package framework], IntelliSense Member Completion
ms.assetid: 500f718d-9028-49a4-8615-ba95cf47fc52
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4e375cc8d314163b277cc20685ae19f134236b0a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49240816"
---
# <a name="member-completion-in-a-legacy-language-service"></a>Завершение участников в языковой службе прежних версий
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Завершения члена IntelliSense можно всплывающей подсказки, которая отображает список возможных членов в конкретной области, например класс, структуру, перечисление или пространства имен. Например в C#, если пользователь вводит «this» через точку список всех членов класса или структуры в текущей области представлены в список, из которого пользователь может выбрать.  
  
 Managed package framework (MPF) предоставляет поддержку всплывающей подсказки и управления списком в подсказке; все, что нужно — сотрудничество из синтаксического анализатора для предоставления данных, отображаемых в списке.  
  
 Устаревший языковой службы реализуются как часть пакета VSPackage, но новый способ реализовать функции языковой службы является использование расширений MEF. Дополнительные сведения см. в разделе [расширение редактора и языковых служб](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Мы рекомендуем начать использовать новый редактор API как можно скорее. Это улучшит производительность службы языка и позволяют воспользоваться преимуществами новых функций редактора.  
  
## <a name="how-it-works"></a>Принцип работы  
 Ниже приведены два способа, в которых показан список членов, используя классы MPF:  
  
-   Позиционирование курсора на идентификатор, или после символа завершения члена и выбрав **отображать список членов** из **IntelliSense** меню.  
  
-   <xref:Microsoft.VisualStudio.Package.IScanner> Сканера обнаруживает знака завершения элемента и задает триггер токена для <xref:Microsoft.VisualStudio.Package.TokenTriggers> этого символа.  
  
 Символ завершения элемента показывает, что является членом класса, структуры или перечисления выполните. Например, в C# или Visual Basic символ завершения член является `.`, тогда как в C++ символ является `.` или `->`. Триггер имеет значение при сканировании выберите символ члена.  
  
### <a name="the-intellisense-member-list-command"></a>Команда List членов технологией IntelliSense  
 <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> Команда инициирует вызов <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> метод <xref:Microsoft.VisualStudio.Package.Source> класс и <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> метод, в свою очередь, вызывает <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод синтаксического анализа с причиной по синтаксического анализа <xref:Microsoft.VisualStudio.Package.ParseReason>.  
  
 Средство синтаксического анализа определяет контекст текущей позиции, а также маркер в группе или непосредственно перед текущей позиции. Исходя из этого маркера, появится список объявлений. Например, в C#, при наведении курсора на член класса и выберите **отображать список членов**, получение списка всех членов класса. Если вы поместите курсор после точку после переменной объекта, отобразится список всех членов класса, которые представляет объект. Обратите внимание, что если курсор находится на члене, при отображении списка членов, выбора элемента из списка заменяет член, на которой находится курсор с одним из списка.  
  
### <a name="the-token-trigger"></a>Токен триггера  
 <xref:Microsoft.VisualStudio.Package.TokenTriggers> Триггер инициирует вызов <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> метод <xref:Microsoft.VisualStudio.Package.Source> класс и <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> метод, в свою очередь, вызывает средство синтаксического анализа с причиной по синтаксического анализа <xref:Microsoft.VisualStudio.Package.ParseReason> (если включена маркера триггер <xref:Microsoft.VisualStudio.Package.TokenTriggers> флаг, Это связано с синтаксического анализа <xref:Microsoft.VisualStudio.Package.ParseReason> который объединяет в себе Выбор членов и выделение скобок).  
  
 Средство синтаксического анализа определяет контекст текущего размещения, а также что такое типизированные, прежде чем элемент будет выбрать символ. Владея этими сведениями он создает список всех членов запрошенной области. Этот список объявлений хранится в <xref:Microsoft.VisualStudio.Package.AuthoringScope> объект, возвращаемый из <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод. Если возвращаются все объявления, отображается всплывающая подсказка элемента завершения. Всплывающая подсказка управляется экземпляром <xref:Microsoft.VisualStudio.Package.CompletionSet> класса.  
  
## <a name="enabling-support-for-member-completion"></a>Включение поддержки для автозавершение элементов  
 Необходимо иметь `CodeSense` запись реестра значение 1, поддерживает любые операции IntelliSense. Этот параметр реестра можно задать именованный параметр, передаваемый <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> атрибут пользователя, связанные с данным пакетом языка. Классы службы языка прочитать значение этой записи реестра из <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> свойство <xref:Microsoft.VisualStudio.Package.LanguagePreferences> класса.  
  
 Если сканер возвращает токен активации <xref:Microsoft.VisualStudio.Package.TokenTriggers>и ваш анализатор возвращает список объявлений, а затем отображается список завершения члена.  
  
## <a name="supporting-member-completion-in-the-scanner"></a>Поддержка автозавершение элементов в средства проверки  
 Сканер должен иметь возможность определить символ завершения члена и установить токена активации <xref:Microsoft.VisualStudio.Package.TokenTriggers> при синтаксическом анализе этого символа.  
  
### <a name="example"></a>Пример  
 Ниже приведен упрощенный пример того, обнаружение символ завершения члена и задав соответствующую <xref:Microsoft.VisualStudio.Package.TokenTriggers> флаг. Данный пример является только для иллюстративных целей. Предполагается, что сканер содержит метод `GetNextToken` идентификации и возвращает токены из строки текста. В примере кода просто задает триггер при каждом обнаружении правильный тип символа.  
  
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
  
## <a name="supporting-member-completion-in-the-parser"></a>Поддержка автозавершение элементов в средстве синтаксического анализа  
 Для завершения члена <xref:Microsoft.VisualStudio.Package.Source> вызываемый классом <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> метод. Необходимо реализовать в классе, который является производным от списка <xref:Microsoft.VisualStudio.Package.Declarations> класса. См. в разделе <xref:Microsoft.VisualStudio.Package.Declarations> класс подробные сведения о методах, необходимо реализовать.  
  
 Средство синтаксического анализа вызывается с <xref:Microsoft.VisualStudio.Package.ParseReason> или <xref:Microsoft.VisualStudio.Package.ParseReason> когда вводится знака выбора элемента. Расположение, указанное <xref:Microsoft.VisualStudio.Package.ParseRequest> объект находится сразу после элемента выберите символ. Средство синтаксического анализа необходимо собрать имена всех элементов, которые могут присутствовать в списке членов в определенный момент в исходном коде. Затем средство синтаксического анализа должно проанализировать текущую строку, чтобы определить область, которую пользователь хочет связанный со знаком выберите член.  
  
 Эта область основан на тип идентификатора, прежде чем элемент будет выбрать символ. Например, в C#, если переменная-член `languageService` , с типом `LanguageService`, введите **languageService.** Создает список всех членов `LanguageService` класса. Также в C# введя **это.** Создает список всех членов класса в текущей области.  
  
### <a name="example"></a>Пример  
 В примере показан один из способов заполнения <xref:Microsoft.VisualStudio.Package.Declarations> списка. Этот код предполагает, что синтаксический анализатор создает объявление и добавляет его в список путем вызова `AddDeclaration` метод `TestAuthoringScope` класса.  
  
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

