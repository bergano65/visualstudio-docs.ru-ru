---
title: Парные фигурные скобки в языковой службе прежних версий | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- brace matching
- language services [managed package framework], brace matching
ms.assetid: 4e3d0a70-f22f-49dd-92d8-edf48ab62b52
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cceac8f2eb6842166f9c73f6374f4f1923cf3831
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54920036"
---
# <a name="brace-matching-in-a-legacy-language-service"></a>Парные фигурные скобки в языковой службы прежних версий
Парные фигурные скобки позволяет разработчику отслеживать языковые элементы, которые должны применяться вместе, таких как круглые и фигурные скобки. Когда разработчик вводит закрывающую фигурную скобку, выделяется открывающей фигурной скобки.  
  
 Можно сопоставить два или три встречающиеся элементы (пары ") и триад. Триад — это набор из трех элементов, встречающиеся. Например, в C# `foreach` инструкции forms тройку: `foreach()`, `{`, и `}`. Все три элемента выделяются при вводе закрывающей фигурной скобки.  
  
 Устаревший языковой службы реализуются как часть пакета VSPackage, но новый способ реализовать функции языковой службы является использование расширений MEF. Чтобы узнать больше о новый способ реализовать парные фигурные скобки, см. в разделе [Пошаговое руководство: Отображение парных скобок](../../extensibility/walkthrough-displaying-matching-braces.md).  
  
> [!NOTE]
>  Мы рекомендуем начать использовать новый редактор API как можно скорее. Это улучшит производительность службы языка и позволяют воспользоваться преимуществами новых функций редактора.  
  
 <xref:Microsoft.VisualStudio.Package.AuthoringSink> Класс поддерживает оба пары и позволяющая утроить с <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchPair%2A> и <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchTriple%2A> методы.  
  
## <a name="implementation"></a>Реализация  
 Служба языка необходимо определить все соответствующие элементы на языке, а затем найдите все совпадающие пары. Обычно это выполняется путем реализации <xref:Microsoft.VisualStudio.Package.IScanner> обнаружить соответствующий язык, а затем использовав <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод для сопоставления элементов.  
  
 <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Метод вызывает сканер для маркировки строке и возвращает токен, прямо перед курсором. Средство проверки указывает, что языковой пары элемент найден, задав значение маркера триггера <xref:Microsoft.VisualStudio.Package.TokenTriggers> на текущий маркер. <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Вызовы методов <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> метод, который в свою очередь вызывает <xref:Microsoft.VisualStudio.Package.LanguageService.BeginParse%2A> метод со значением причина синтаксического анализа <xref:Microsoft.VisualStudio.Package.ParseReason> найти соответствующий элемент языка. Если найден соответствующий элемент языка, выделяются оба элемента.  
  
 Полное описание как вводить фигурную скобку активирует Выделение скобок, см. в разделе *операция синтаксического анализа примера* приведенной выше статьи [средства синтаксического анализа службы языка для прежних версий и сканер](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).  
  
## <a name="enable-support-for-brace-matching"></a>Включить поддержку парные фигурные скобки  
 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> Можно задать атрибут **MatchBraces**, **MatchBracesAtCaret**, и **ShowMatchingBrace** записи реестра, устанавливает соответствующие свойства из <xref:Microsoft.VisualStudio.Package.LanguagePreferences> класса. Свойства предпочтения языка также могут задаваться пользователем.  
  
|Запись реестра|Свойство.|Описание:|  
|--------------------|--------------|-----------------|  
|MatchBraces|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBraces%2A>|Включает парные фигурные скобки.|  
|MatchBracesAtCaret|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBracesAtCaret%2A>|Перемещает включает парные фигурные скобки, где находится курсор.|  
|ShowMatchingBrace|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>|Выделяет соответствующую скобку.|  
  
## <a name="match-conditional-statements"></a>Соответствует условные операторы  
 Можно сопоставить условные операторы, такие как `if`, `else if`, и `else`, или `#if`, `#elif`, `#else`, `#endif`, в так же, как парные разделители. Вы можете подкласс <xref:Microsoft.VisualStudio.Package.AuthoringSink> класса и предоставить распространяется на метод, который можно добавить текст, а также разделителей внутренний массив соответствующих элементов.  
  
## <a name="set-the-trigger"></a>Установите триггер  
 Приведенный ниже показано, как обнаружить соответствующий круглые скобки, фигурные скобки и квадратные скобки и задание триггера для него в сканер. <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Метод <xref:Microsoft.VisualStudio.Package.Source> класс определяет триггер и вызывает средство синтаксического анализа для поиска соответствующей пары (см. в разделе *поиск совпадения* этой статьи). Данный пример является только для иллюстративных целей. Предполагается, что сканер содержит метод `GetNextToken` идентификации и возвращает токены из строки текста.  
  
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
  
## <a name="match-the-braces"></a>Соответствует фигурные скобки  
 Ниже приведен упрощенный пример для соответствующих элементов языка `{ }`, `( )`, и `[ ]`и добавления их диапазоны для <xref:Microsoft.VisualStudio.Package.AuthoringSink> объекта. Этот подход не является рекомендуемым для анализа исходного кода; Это только для иллюстративных целей.  
  
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
 [Функции службы устаревшего языка](../../extensibility/internals/legacy-language-service-features1.md)   
 [Средство синтаксического анализа устаревший языковой службы и средства проверки](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)