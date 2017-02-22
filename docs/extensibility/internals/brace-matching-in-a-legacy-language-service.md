---
title: "Проверка парности фигурных скобок в языковую службу для прежних версий | Microsoft Docs"
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
  - "парные фигурные скобки"
  - "языковые службы [платформа управляемых пакетов] парные фигурные скобки"
ms.assetid: 4e3d0a70-f22f-49dd-92d8-edf48ab62b52
caps.latest.revision: 27
caps.handback.revision: 27
ms.author: "gregvanl"
manager: "ghogen"
---
# Проверка парности фигурных скобок в языковую службу для прежних версий
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Парные фигурные скобки позволяет разработчику отслеживать языковые элементы, которые необходимо осуществить вместе, таких как круглые скобки и фигурные скобки. Когда разработчик вводит закрывающую фигурную скобку, открывающая фигурная скобка будет выделен.  
  
 Можно сопоставить два или три встречающиеся элементов, называемых пары и тройки. Тройки представляют собой наборы три встречающиеся элементы. Например, в C\# `foreach` инструкции forms тройку:»`foreach()`«,»`{`», и «`}`». Все три элемента выделяются при вводе закрывающей фигурной скобки.  
  
 Устаревший языковые службы реализуются как частью VSPackage, но это использование расширений MEF новый способ реализации возможностей службы языка. Чтобы узнать больше о новый способ реализовать парные фигурные скобки, в разделе [Пошаговое руководство: Отображение парные фигурные скобки](../../extensibility/walkthrough-displaying-matching-braces.md).  
  
> [!NOTE]
>  Мы рекомендуем начать использовать новый редактор API как можно быстрее. Это улучшает производительность службы языка и позволяют воспользоваться преимуществами новых функций редактора.  
  
 <xref:Microsoft.VisualStudio.Package.AuthoringSink> Класс поддерживает обе пары и позволяющая утроить с <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchPair%2A> и <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchTriple%2A> методы.  
  
## Реализация  
 Служба языка необходимо определить все соответствующие элементы в язык и найдите все совпадающие пары. Обычно это выполняется путем реализации <xref:Microsoft.VisualStudio.Package.IScanner> для определения соответствия языка и затем с помощью <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> способа для сравнения элементов.  
  
 <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Метод вызывает сканер для маркировки строки и возвращают маркер прямо перед курсором. Сканер указывает, что найден пары элементов языка, задав значение маркера триггер <xref:Microsoft.VisualStudio.Package.TokenTriggers> на текущий маркер.<xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Вызовы метода <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> в свою очередь вызывает метод <xref:Microsoft.VisualStudio.Package.LanguageService.BeginParse%2A> метод со значением анализа причин <xref:Microsoft.VisualStudio.Package.ParseReason> для поиска соответствующего элемента языка. Если соответствующий элемент языка найден, выделяются оба элемента.  
  
 Полное описание как ввод фигурную скобку запускает Выделение скобок, см. в разделе «Пример анализа операция» в разделе [Средство синтаксического анализа языка прежних версий службы и сканера](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).  
  
## Включение поддержки парные фигурные скобки  
 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> Можно задать атрибут `MatchBraces`, `MatchBracesAtCaret`, и `ShowMatchingBrace` именованные параметры, которые заданы соответствующие свойства <xref:Microsoft.VisualStudio.Package.LanguagePreferences> класса. Свойства предпочтения языка также могут задаваться пользователем.  
  
|Запись реестра|Свойство|Описание|  
|--------------------|--------------|--------------|  
|`MatchBraces`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBraces%2A>|Включает парные фигурные скобки|  
|`MatchBracesAtCaret`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBracesAtCaret%2A>|Включает парные фигурные скобки как курсор перемещается.|  
|`ShowMatchingBrace`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>|Выделяет парную скобку.|  
  
## Сопоставление условные операторы  
 Можно сопоставить условные операторы, такие как `if`, `else if`, и `else`, или `#if`, `#elif`, `#else`, `#endif`, таким же образом, как соответствующие разделители. Можно создать подкласс <xref:Microsoft.VisualStudio.Package.AuthoringSink> класса и предоставить охватывает метод, который можно добавить текст, а также разделители для внутреннего массива соответствующих элементов.  
  
## Установка триггера  
 Приведенный ниже показано, как определить сопоставления скобок, фигурных скобок и квадратные скобки и задание триггера для него в сканер.<xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Метод <xref:Microsoft.VisualStudio.Package.Source> класса определяет триггер и вызывает средство синтаксического анализа для поиска соответствующей пары \(см. раздел «Поиск совпадения» этого раздела\). Данный пример является только для иллюстративных целей. Предполагается, что сканер содержит метод `GetNextToken` определяет и возвращает маркеры из строки текста.  
  
```c#  
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
  
## Согласование скобок  
 Ниже приведен упрощенный пример для совпадения {} элементы языка, \(\) и \[\] и добавления их диапазоны для <xref:Microsoft.VisualStudio.Package.AuthoringSink> объекта. Этот подход не является рекомендуемым подходом для анализа исходного кода; Это только в иллюстративных целях.  
  
```c#  
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
  
## См. также  
 [Компоненты прежних версий языка службы](../../extensibility/internals/legacy-language-service-features1.md)   
 [Средство синтаксического анализа языка прежних версий службы и сканера](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)