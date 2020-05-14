---
title: Соответствие скобки в устаревшей языковой службе (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- brace matching
- language services [managed package framework], brace matching
ms.assetid: 4e3d0a70-f22f-49dd-92d8-edf48ab62b52
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0081be3e3ab5a53f7d85f77475d4288aa5c87092
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709808"
---
# <a name="brace-matching-in-a-legacy-language-service"></a>Соответствие скобки в устаревшей языковой службе
Соответствие скобки помогает разработчику отслеживать языковые элементы, которые должны происходить вместе, такие как скобки и фигурные скобки. Когда разработчик вводит закрывающий скобку, открывающийся скобка выделяется.

 Вы можете сопоставить два или три сопутствующих элемента, называемые парами и тройками. Тройки представляют собой наборы из трех сопутствующих элементов. Например, в C `foreach` q, заявление `foreach()`формирует `{`тройной: , и `}`. Все три элемента выделены при набранной скобке закрытия.

 Устаревшие языковые службы реализуются как часть VSPackage, но новый способ реализации функций языкового сервиса заключается в использовании расширений MEF. Чтобы узнать больше о новом способе реализации соответствия [скобки, см.](../../extensibility/walkthrough-displaying-matching-braces.md)

> [!NOTE]
> Мы рекомендуем вам начать использовать новый API редактора как можно скорее. Это повысит производительность вашего языкового сервиса и позволит вам воспользоваться новыми функциями редактора.

 Класс <xref:Microsoft.VisualStudio.Package.AuthoringSink> поддерживает как пары, так <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchPair%2A> и <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchTriple%2A> тройки с помощью методов.

## <a name="implementation"></a>Реализация
 Языковой службе необходимо определить все соответствующие элементы в языке, а затем найти все соответствующие пары. Обычно это достигается путем реализации <xref:Microsoft.VisualStudio.Package.IScanner> для обнаружения <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> совмещенных языков, а затем с помощью метода для соответствия элементам.

 Метод <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> вызывает сканер, чтобы тотекенизировать линию и вернуть токен непосредственно перед каретом. Сканер указывает, что пара элемента языка была найдена <xref:Microsoft.VisualStudio.Package.TokenTriggers> путем установки значения триггера маркера на токе. Метод <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> вызывает <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> метод, который, <xref:Microsoft.VisualStudio.Package.LanguageService.BeginParse%2A> в свою очередь, вызывает <xref:Microsoft.VisualStudio.Package.ParseReason> метод с значением причины для определения, чтобы найти соответствующий элемент языка. При обнаружении соответствующего языкового элемента оба элемента выделены.

 Для полного описания того, как ввод скобки вызывает скобки выделения, *см. Пример разбора операции* раздел в статье Наследие [языковой сервис parser и сканера](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).

## <a name="enable-support-for-brace-matching"></a>Включить поддержку для соответствия скобки
 Атрибут <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> может установить **MatchBraces,** **MatchBracesAtCaret**и записи реестра **ShowMatchingBrace,** которые устанавливают соответствующие свойства <xref:Microsoft.VisualStudio.Package.LanguagePreferences> класса. Свойства языковых предпочтений также могут быть установлены пользователем.

|Параметр реестра|Свойство|Описание|
|--------------------|--------------|-----------------|
|MatchBraces|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBraces%2A>|Позволяет соответствие скобки.|
|MatchBracesAtCaret|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBracesAtCaret%2A>|Позволяет скобки соответствия, как карет движется.|
|ShowMatchingBrace|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>|Выделяет соответствующую скобку.|

## <a name="match-conditional-statements"></a>Условные заявления матча
 Вы можете сопоставить условные операторы, `#if` `#elif`такие `#else` `#endif`как, `if` `else if`и , или `else`, , , , , так же, как соответствующие делимитеры. Можно подклассифицировать <xref:Microsoft.VisualStudio.Package.AuthoringSink> класс и предоставить метод, который может добавить текстовые пролеты, а также делимитеры для внутреннего массива соответствующих элементов.

## <a name="set-the-trigger"></a>Установите спусковой крючок
 Ниже приводится следующий пример, как обнаружить соответствующие скобки, фигурные скобки и квадратные скобки, и установка триггера для него в сканере. Метод <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> на <xref:Microsoft.VisualStudio.Package.Source> классе обнаруживает спусковой крючок и вызывает парсер, чтобы найти соответствующую пару (см. раздел *«Поиск соответствия»* в этой статье). Этот пример предназначен только для иллюстративных целей. Предполагается, что ваш сканер `GetNextToken` содержит метод, который идентифицирует и возвращает токены из строки текста.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestScanner : IScanner
    {
        private const string braces = "()[]{}";
        private Lexer lex;

        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,
                                                   ref int state)
        {
            bool foundToken = false;
            string token = lex.GetNextToken();
            if (token != null)
            {
                foundToken = true;
                char firstChar = token[0];
                if (Char.IsPunctuation(firstChar) && token.Length > 0)
                {
                    if (braces.IndexOf(firstChar) != -1)
                    {
                        tokenInfo.Trigger = TokenTriggers.MatchBraces;
                    }
                }
            }
            return foundToken;
        }
```

## <a name="match-the-braces"></a>Матч скобки
 Вот упрощенный пример для сопоставления языковых `{ }`элементов , `( )`и , и, `[ ]`и добавление их диапазонов к объекту. <xref:Microsoft.VisualStudio.Package.AuthoringSink> Этот подход не является рекомендуемым подходом к разбору исходного кода; это только для иллюстративных целей.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class Parser
    {
         private IList<TextSpan[]> m_braces;
         public IList<TextSpan[]> Braces
         {
             get { return m_braces; }
         }
         private void AddMatchingBraces(TextSpan braceSpan1, TextSpan braceSpan2)
         {
             if IsMatch(braceSpan1, braceSpan2)
                 m_braces.Add(new TextSpan[] { braceSpan1, braceSpan2 });
         }

         private bool IsMatch(TextSpan braceSpan1, TextSpan braceSpan2)
         {
             //definition for matching here
          }
    }

    public class TestLanguageService : LanguageService
    {
         Parser parser = new Parser();
         Source source = (Source) this.GetSource(req.FileName);

         private AuthoringScope ParseSource(ParseRequest req)
         {
             if (req.Sink.BraceMatching)
             {
                 if (req.Reason==ParseReason.MatchBraces)
                 {
                     foreach (TextSpan[] brace in parser.Braces)
                     {
                         req.Sink.MatchPair(brace[0], brace[1], 1);
                     }
                 }
             }
             return new TestAuthoringScope();
         }
    }
}
```

## <a name="see-also"></a>См. также
- [Функции устаревшего языкового сервиса](../../extensibility/internals/legacy-language-service-features1.md)
- [Устаревший языковой сервис-парсер и сканер](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)
