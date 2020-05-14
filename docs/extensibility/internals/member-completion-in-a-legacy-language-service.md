---
title: Завершение работы в службе обучения языку (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense, Member Completion tool tip
- Member Completion, supporting in language services [managed package framework]
- language services [managed package framework], IntelliSense Member Completion
ms.assetid: 500f718d-9028-49a4-8615-ba95cf47fc52
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b6445aec4954590e4d361189f053592eebe7767e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707200"
---
# <a name="member-completion-in-a-legacy-language-service"></a>Завершение участников в языковой службе прежних версий

Завершение членского состава IntelliSense — это наконечник инструмента, который отображает список возможных участников определенной области, таких как класс, структура, перечисление или пространство имен. Например, в C,, если пользователь вводит "это", за которым следует период, список всех членов класса или структуры в текущем объеме представлен в списке, из которого пользователь может выбрать.

Платформа управляемого пакета (MPF) обеспечивает поддержку наконечника инструмента и управление списком в наконечнике инструмента; все, что необходимо, это сотрудничество с парсером для предоставления данных, которые фигурирует в списке.

Устаревшие языковые службы реализуются как часть VSPackage, но новый способ реализации функций языкового сервиса заключается в использовании расширений MEF. Чтобы узнать больше, смотрите [Расширение редактора и языковых служб](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Мы рекомендуем вам начать использовать новый API редактора как можно скорее. Это повысит производительность вашего языкового сервиса и позволит вам воспользоваться новыми функциями редактора.

## <a name="how-it-works"></a>Как это работает

Ниже приведены два способа отображаются с помощью классов MPF:

- Позиционирование caret на идентификаторе или после завершения участника персонажа и выбор **участников списка** из меню **IntelliSense.**

- Сканер <xref:Microsoft.VisualStudio.Package.IScanner> обнаруживает символ завершения участника и устанавливает маркерный триггер [TokenTriggers.MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) для этого символа.

Символ завершения участника указывает, что за ним должен следовать член класса, структура или перечисление. Например, в C- или Visual Basic `.`символ завершения участника является , в `.` то `->`время как в C» символ является либо или . Значение триггера устанавливается при сканировании символа, выбранного членом.

### <a name="the-intellisense-member-list-command"></a>Командование списка членов IntelliSense

Команда <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> инициирует вызов <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> к <xref:Microsoft.VisualStudio.Package.Source> методу <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> на классе и метод, в свою очередь, вызывает <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод парсер с разбором причине [ParseReason.DisplayMemberList](<xref:Microsoft.VisualStudio.Package.ParseReason.DisplayMemberList>).

Парсер определяет контекст текущего положения, а также токен под или непосредственно перед текущей позицией. На основе этого токена представлен список деклараций. Например, в C q, если вы размещаете внимательность на участника класса и выбираете **участников списка,** вы получаете список всех членов класса. Если вы расположили внимательность после периода, следующего за переменной объекта, вы получите список всех членов класса, который представляет объект. Обратите внимание, что если карет аурет расположен на участнике, когда отображается список участников, выбор участника из списка заменяет участника, на который находится каретна на тот, на который входит список.

### <a name="the-token-trigger"></a>Триггер токенов

[Триггер TokenTriggers.MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) инициирует <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> вызов к <xref:Microsoft.VisualStudio.Package.Source> методу <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> на классе, а метод, в свою очередь, вызывает парсер с причиной разбора [ParseReason.MemberSelect](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelect>). Если маркер триггера также [включены TokenTriggers.MatchBraces](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MatchBraces>) флаг, разбор причине [ParseReason.MemberSelectAndHighlightBraces](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelectAndHighlightBraces>), который сочетает в себе выбор членов и скобки выделения.

Парсер определяет контекст текущего положения, а также то, что было набрано до выбора символа участника. Из этой информации парсер создает список всех членов запрашиваемого объема. Этот список деклараций хранится в объекте, <xref:Microsoft.VisualStudio.Package.AuthoringScope> который возвращается из метода. <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> При возврате каких-либо деклараций отображается наконечник инструмента завершения участника. Наконечник инструмента управляется экземпляром <xref:Microsoft.VisualStudio.Package.CompletionSet> класса.

## <a name="enable-support-for-member-completion"></a>Включить поддержку завершения участника

Вы должны `CodeSense` иметь регистрационный набор до 1 для поддержки любой операции IntelliSense. Эта запись реестра может быть установлена с <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> именованным параметром, передаваемым атрибуту пользователя, связанному с пакетом языка. Классы языковых служб считываем значение этого входа в реестр из <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> свойства в <xref:Microsoft.VisualStudio.Package.LanguagePreferences> классе.

Если ваш сканер возвращает маркерный триггер [TokenTriggers.MemberSelect,](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>)а ваш парсер возвращает список деклараций, то отображается список завершения участников.

## <a name="support-member-completion-in-the-scanner"></a>Завершение выполнения программы поддержки в сканере

Сканер должен быть в состоянии обнаружить символ завершения участника и установить маркерный триггер [TokenTriggers.MemberSelect,](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) когда этот символ будет разобрана.

### <a name="scanner-example"></a>Пример сканера

Вот упрощенный пример обнаружения символа завершения участника <xref:Microsoft.VisualStudio.Package.TokenTriggers> и установки соответствующего флага. Этот пример предназначен только для иллюстративных целей. Предполагается, что ваш сканер `GetNextToken` содержит метод, который идентифицирует и возвращает токены из строки текста. Пример кода просто устанавливает триггер всякий раз, когда он видит правильный вид символа.

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

## <a name="support-member-completion-in-the-parser"></a>Завершение работы участника программы поддержки в Parser

Для завершения участника <xref:Microsoft.VisualStudio.Package.Source> класс <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> вызывает метод. Необходимо реализовать список в классе, который <xref:Microsoft.VisualStudio.Package.Declarations> происходит из класса. Просмотрите <xref:Microsoft.VisualStudio.Package.Declarations> класс для получения подробной информации о методах, которые необходимо реализовать.

Парсер называется [parseReason.MemberSelect](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelect>) или [ParseReason.MemberSelectAndHighlightBraces](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelectAndHighlightBraces>) при найме персонажа. Место, данное <xref:Microsoft.VisualStudio.Package.ParseRequest> в объекте, сразу после выбора символа участника. Парсер должен собирать имена всех участников, которые могут отображаться в списке участников в этот конкретный момент в исходном коде. Затем парсер должен разогнать текущую строку, чтобы определить область, которая пользователь хочет, связанный с выбранным символом пользователя.

Эта область основана на типе идентификатора перед выбранным символом участника. Например, в C q, `languageService` учитывая переменную `LanguageService`члена, которая имеет тип, ввод **languageService.** создает список всех членов `LanguageService` класса. Кроме того, в C , набрав **это.** создает список всех членов класса в текущей области.

### <a name="parser-example"></a>Парзер пример

Следующий пример показывает один способ <xref:Microsoft.VisualStudio.Package.Declarations> заполнить список. Этот код предполагает, что парсер строит декларацию и добавляет `AddDeclaration` ее в `TestAuthoringScope` список, вызывая метод в классе.

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
