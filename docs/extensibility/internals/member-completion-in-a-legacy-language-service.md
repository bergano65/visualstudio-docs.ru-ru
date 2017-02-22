---
title: "Завершение члена в языковую службу для прежних версий | Microsoft Docs"
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
  - "Технология IntelliSense, завершение член всплывающей подсказки"
  - "Завершение члена, поддержка в языковые службы [платформа управляемых пакетов]"
  - "языковые службы [платформа управляемых пакетов] член завершения IntelliSense"
ms.assetid: 500f718d-9028-49a4-8615-ba95cf47fc52
caps.latest.revision: 21
caps.handback.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
---
# Завершение члена в языковую службу для прежних версий
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Завершение IntelliSense член является всплывающей подсказки, которая отображает список возможных членов определенной области, например класса, структуры, перечисления или пространства имен. Например в C\# при вводе «this» ставится точка, список всех членов класса или структуры в текущей области представлены в список, из которого пользователь может выбрать.  
  
 Платформа управляемых пакетов \(MPF\) обеспечивает поддержку всплывающую подсказку и управление списком в подсказке; все, что требуется — взаимодействие от средства синтаксического анализа в качестве источника данных, который отображается в списке.  
  
 Устаревший языковые службы реализуются как частью VSPackage, но это использование расширений MEF новый способ реализации возможностей службы языка. Для получения дополнительных см [Расширение редактора и языковые службы](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Мы рекомендуем начать использовать новый редактор API как можно быстрее. Это улучшает производительность службы языка и позволяют воспользоваться преимуществами новых функций редактора.  
  
## Принцип работы  
 Ниже можно двумя способами, в которых отображается список членов с помощью классов MPF.  
  
-   Позиционирование курсора на идентификаторе или после завершения знака элемента и выбрав **список членов** из **IntelliSense** меню.  
  
-   <xref:Microsoft.VisualStudio.Package.IScanner> Сканер определяет символ завершения члена и задает токен триггера <xref:Microsoft.VisualStudio.Package.TokenTriggers> этого символа.  
  
 Символ завершения элемент указывает, что является членом класса, структуры или перечисления является следовать. Например, в C\# или Visual Basic является символ завершения член `.`, тогда как в C\+\+ символ является `.` или `->`. Триггер имеет значение при сканировании символов выберите член.  
  
### Команда List членов IntelliSense  
 <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> Команда инициирует вызов <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> метод <xref:Microsoft.VisualStudio.Package.Source> класса и <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> метод, в свою очередь, вызывает <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод синтаксического анализа с причиной синтаксического анализа <xref:Microsoft.VisualStudio.Package.ParseReason>.  
  
 Средство синтаксического анализа определяет контекст текущей позиции, а также маркер в группе или непосредственно перед текущей позиции. Исходя из этого маркера, выводится список объявлений. Например, в C\# при наведении курсора на член класса и выберите **список членов**, получить список всех членов класса. Если поместите курсор после точку после переменной объекта, можно получить список всех членов класса, которые представляет. Обратите внимание, что если точка вставки находится над элементом при отображении списка членов, выбора элемента из списка заменяет член, на которой находится курсор с одним из списка.  
  
### Токен триггера  
 <xref:Microsoft.VisualStudio.Package.TokenTriggers> Триггер инициирует вызов <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> метод <xref:Microsoft.VisualStudio.Package.Source> класса и <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> метод, в свою очередь, вызывает метод синтаксического анализа с причиной синтаксического анализа <xref:Microsoft.VisualStudio.Package.ParseReason> \(если маркера триггер также включены <xref:Microsoft.VisualStudio.Package.TokenTriggers> флаг, синтаксического анализа причина заключается в <xref:Microsoft.VisualStudio.Package.ParseReason> объединяющие Выбор элемента и выделение скобок\).  
  
 Средство синтаксического анализа определяет контекст текущей позиции, а также что вводилось прежде, чем элемент выберите символ. На основе данных он создает список всех членов запрошенной области. Этот список объявлений хранится в <xref:Microsoft.VisualStudio.Package.AuthoringScope> объект, возвращаемый из <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод. Если возвращаются все объявления, отображается всплывающая подсказка элемента завершения. Подсказка управляется экземпляром <xref:Microsoft.VisualStudio.Package.CompletionSet> класса.  
  
## Включение поддержки для завершения члена  
 Необходимо иметь `CodeSense` реестра значение 1, поддерживают любые операции IntelliSense. Этот параметр реестра можно задать именованный параметр, передаваемый <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> атрибута пользователя, связанного с языковой пакет. Классы службы языка прочитать значение этой записи реестра из <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> свойство <xref:Microsoft.VisualStudio.Package.LanguagePreferences> класса.  
  
 Если сканер возвращает токен активации <xref:Microsoft.VisualStudio.Package.TokenTriggers>, и ваш анализатор возвращает список объявлений, а затем отображается список завершения члена.  
  
## Поддержка завершения члена в программе поиска вирусов  
 Сканер должен иметь возможность символ завершения члена и установите маркера активации <xref:Microsoft.VisualStudio.Package.TokenTriggers> при синтаксическом анализе этого знака.  
  
### Пример  
 Ниже приведен упрощенный пример того, обнаружение символ завершения члена и задав соответствующую <xref:Microsoft.VisualStudio.Package.TokenTriggers> флаг. Данный пример является только для иллюстративных целей. Предполагается, что сканер содержит метод `GetNextToken` определяет и возвращает маркеры из строки текста. Пример кода просто устанавливает триггер при каждом обнаружении правильный тип символа.  
  
```c#  
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
  
## Поддержка завершения члена в средстве синтаксического анализа  
 Для завершения член <xref:Microsoft.VisualStudio.Package.Source> класса вызывает <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> метод. Список необходимо реализовать в классе, который является производным от <xref:Microsoft.VisualStudio.Package.Declarations> класса. В разделе <xref:Microsoft.VisualStudio.Package.Declarations> класс подробные сведения о методах, которые необходимо реализовать.  
  
 Средство синтаксического анализа вызывается с <xref:Microsoft.VisualStudio.Package.ParseReason> или <xref:Microsoft.VisualStudio.Package.ParseReason> при типизированных знака выбора элемента. Расположение, заданное в <xref:Microsoft.VisualStudio.Package.ParseRequest> объект находится сразу после элемента выберите символ. Средство синтаксического анализа необходимо собирать имена всех элементов, которые могут присутствовать в списке членов в этой конкретной точке в исходном коде. Затем средство синтаксического анализа необходимо выполнить синтаксический анализ текущей строки, чтобы определить область, которую пользователь хочет связанным с символом выберите член.  
  
 Эта область основан на тип идентификатора до знак выбора элемента. Например, в C\# для переменной\-члена `languageService` имеет тип `LanguageService`, введите **languageService.** создает список всех членов `LanguageService` класса. Также в C\# введя **это.** создает список всех членов класса в текущей области.  
  
### Пример  
 Следующий пример показывает один из способов заполнения <xref:Microsoft.VisualStudio.Package.Declarations> списка. Этот код предполагает, что синтаксический анализатор создает объявление и добавляет его в список путем вызова `AddDeclaration` метод `TestAuthoringScope` класса.  
  
```c#  
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