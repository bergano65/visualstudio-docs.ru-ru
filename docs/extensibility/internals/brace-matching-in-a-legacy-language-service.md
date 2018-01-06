---
title: "Парные фигурные скобки в языковую службу прежних версий | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- brace matching
- language services [managed package framework], brace matching
ms.assetid: 4e3d0a70-f22f-49dd-92d8-edf48ab62b52
caps.latest.revision: "27"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c496c65244f0ede0c3a6385f6cf1329479a17c22
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="brace-matching-in-a-legacy-language-service"></a>Парные фигурные скобки в языковую службу прежних версий
Парные фигурные скобки позволяет разработчику отслеживать языковые элементы, которые нужно выполнить друг с другом, таких как круглые и фигурные скобки. Когда разработчик вводит закрывающую фигурную скобку, выделяется открывающей фигурной скобки.  
  
 Можно сопоставить два или три встречающиеся элементов, называемых пары и тройки. Тройки представляют собой наборы три встречающиеся элементы. Например, в C# `foreach` инструкции forms тройном: "`foreach()`«,»`{`», и «`}`». Все три элемента, выделяются при вводе закрывающей фигурной скобки.  
  
 Прежних версий языка службы реализованы как часть пакета VSPackage, но новой реализации возможностей службы языка можно выполнить с помощью расширений MEF. Дополнительные сведения о новых способ реализации парные фигурные скобки, в разделе [Пошаговое руководство: отображение парные фигурные скобки](../../extensibility/walkthrough-displaying-matching-braces.md).  
  
> [!NOTE]
>  Мы рекомендуем начать использовать новый редактор API, как можно быстрее. Это повысит быстродействие языковой службы и позволяют воспользоваться преимуществами новых функций редактора.  
  
 <xref:Microsoft.VisualStudio.Package.AuthoringSink> Класс поддерживает обе пары и позволяющая утроить с <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchPair%2A> и <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchTriple%2A> методы.  
  
## <a name="implementation"></a>Реализация  
 Служба языка необходимо определить все соответствующие элементы в язык и найдите все совпадающие пары. Обычно это выполняется путем реализации <xref:Microsoft.VisualStudio.Package.IScanner> обнаружение соответствующих языков и затем с помощью <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> способа для сравнения элементов.  
  
 <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Метод вызывает сканер для маркировки строки и возвратить маркер прямо перед курсором. Средство проверки указывает, что языковой пары элемент найден, задав значение токена триггер <xref:Microsoft.VisualStudio.Package.TokenTriggers> на текущий маркер. <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Вызовы метода <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> метод, который в свою очередь вызывает <xref:Microsoft.VisualStudio.Package.LanguageService.BeginParse%2A> метода со значением причина синтаксического анализа <xref:Microsoft.VisualStudio.Package.ParseReason> найти соответствующий элемент языка. Если найден соответствующий элемент языка выделяются обоих элементов.  
  
 Полное описание как вводить фигурную скобку запускает выделение фигурную скобку в разделе «Операция синтаксического анализа примере» в разделе [средство синтаксического анализа службы языка для прежних версий и сканера](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).  
  
## <a name="enabling-support-for-brace-matching"></a>Включение поддержки парные фигурные скобки  
 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> Атрибут можно установить `MatchBraces`, `MatchBracesAtCaret`, и `ShowMatchingBrace` именованные параметры, задать соответствующие свойства <xref:Microsoft.VisualStudio.Package.LanguagePreferences> класса. Свойства языка и предпочтений можно также задать пользователем.  
  
|Запись реестра|Свойство.|Описание:|  
|--------------------|--------------|-----------------|  
|`MatchBraces`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBraces%2A>|Включает парные фигурные скобки|  
|`MatchBracesAtCaret`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBracesAtCaret%2A>|Включает проверку соответствия фигурных скобок как курсор перемещается.|  
|`ShowMatchingBrace`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>|Выделяет парную скобку.|  
  
## <a name="matching-conditional-statements"></a>Сопоставление условные операторы  
 Можно сопоставить условные операторы, такие как `if`, `else if`, и `else`, или `#if`, `#elif`, `#else`, `#endif`, таким же образом, как соответствующие разделители. Можно создать подкласс <xref:Microsoft.VisualStudio.Package.AuthoringSink> класса и предоставить охватывает метод, который можно добавить текст, а также разделители внутреннего массива соответствующих элементов.  
  
## <a name="setting-the-trigger"></a>Установка триггера  
 В следующем примере показано, как для обнаружения сопоставления скобок, фигурных скобок и квадратных скобок и задание триггера для него в сканер. <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Метод <xref:Microsoft.VisualStudio.Package.Source> класса триггер обнаруживает и вызывает средство синтаксического анализа для поиска соответствующей пары (см. в разделе «Поиск соответствия» в этом разделе). Данный пример является исключительно для демонстрационных целей. Предполагается, что сканер содержит метод `GetNextToken` , определяет и возвращает токенов из текстовой строки.  
  
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
  
## <a name="matching-the-braces"></a>Парные фигурные скобки  
 Ниже приведен упрощенный пример для сопоставления {} элементы языка, () и [] и добавление их диапазоны для <xref:Microsoft.VisualStudio.Package.AuthoringSink> объекта. Такой подход не рекомендуется для разбора исходного кода; Это исключительно для демонстрационных целей.  
  
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
 [Возможности службы прежних версий языка](../../extensibility/internals/legacy-language-service-features1.md)   
 [Средство синтаксического анализа и сканер языковой службы прежних версий](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)