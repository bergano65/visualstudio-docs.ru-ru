---
title: "Сведения о параметрах в языковую службу для прежних версий | Microsoft Docs"
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
  - "Технология IntelliSense, сведения о параметрах всплывающей подсказки"
  - "языковые службы [платформа управляемых пакетов], сведения о параметрах IntelliSense"
  - "Сведения о параметре (технология IntelliSense), поддержка в языковые службы [платформа управляемых пакетов]"
ms.assetid: a117365d-320d-4bb5-b61d-3e6457b8f6bc
caps.latest.revision: 23
caps.handback.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
---
# Сведения о параметрах в языковую службу для прежних версий
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Сведения о параметрах IntelliSense — подсказку, которая отображает подпись метода, при вводе пользователем списка параметров начальный знак \(обычно открывающей круглой скобкой\) для списка параметров метода. Вводится каждый параметр и типом параметра разделителем \(обычно запятой\), подсказка обновляется для отображения следующего параметра полужирным шрифтом.  
  
 Классы framework \(MPF\) управляемых пакетов обеспечивают поддержку для управления подсказка о параметрах. Средство синтаксического анализа должен определить параметр запуска, параметр Далее, и параметр конечных символов и необходимо предоставить список подписи методов и связанными с ними параметрами.  
  
 Устаревший языковые службы реализуются как частью VSPackage, но это использование расширений MEF новый способ реализации возможностей службы языка. Для получения дополнительных см [Расширение редактора и языковые службы](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Мы рекомендуем начать использовать новый редактор API как можно быстрее. Это улучшает производительность службы языка и позволяют воспользоваться преимуществами новых функций редактора.  
  
## Реализация  
 Средство синтаксического анализа следует установить значение триггера <xref:Microsoft.VisualStudio.Package.TokenTriggers> устанавливается при нахождении символа начала списка параметр \(часто открывающая скобка\). Он должен устанавливать <xref:Microsoft.VisualStudio.Package.TokenTriggers> запуска при обнаружении разделителя параметров \(часто запятая\). В результате всплывающей подсказки о параметрах и Показать следующего параметра полужирным шрифтом. Средство синтаксического анализа следует установить значение триггера <xref:Microsoft.VisualStudio.Package.TokenTriggers> При Если находит знак конца списка параметров \(часто закрывающей круглой скобкой\).  
  
 <xref:Microsoft.VisualStudio.Package.TokenTriggers> Значение триггера инициирует вызов <xref:Microsoft.VisualStudio.Package.Source.MethodTip%2A> метод, который в свою очередь вызывает <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> синтаксического анализа метод parse причину <xref:Microsoft.VisualStudio.Package.ParseReason>. Если анализатор определяет, что идентификатор перед списком параметров начальный знак имени метода распознается, он возвращает список сопоставлении сигнатур методов в <xref:Microsoft.VisualStudio.Package.AuthoringScope> объекта. Если найдены все подписи метода, с подписью, первой в списке отображается подсказка о параметрах. Это подсказка обновляется по более подпись набора. При вводе знак конца списка параметров подсказка о параметрах удаляется из представления.  
  
> [!NOTE]
>  Чтобы обеспечить подсказка о параметрах имеет правильный формат, необходимо переопределить свойства на <xref:Microsoft.VisualStudio.Package.Methods> класса для предоставления соответствующих символов. Базовый <xref:Microsoft.VisualStudio.Package.Methods> предполагается, что класс C\#\-стиль сигнатуру метода. В разделе <xref:Microsoft.VisualStudio.Package.Methods> класса сведения о том, как это сделать.  
  
## Включение поддержки для сведения о параметрах  
 Для поддержки подсказки о параметрах, необходимо задать `ShowCompletion` параметр с именем <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> для `true`. Языковая служба считывает значение этой записи реестра из <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> свойство.  
  
 Кроме того <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ParameterInformation%2A> должно быть присвоено свойству `true` для подсказки будет отображаться сведения о параметрах.  
  
### Пример  
 Ниже приведен упрощенный пример того, какие символы список параметров и установив соответствующие триггеры. Данный пример является только для иллюстративных целей. Предполагается, что сканер содержит метод `GetNextToken` определяет и возвращает маркеры из строки текста. Пример кода просто устанавливает триггеры при каждом обнаружении правильный тип символа.  
  
```c#  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestScanner : IScanner  
    {  
        private Lexer lex;  
        private const char parameterListStartChar = '(';  
        private const char parameterListEndChar   = ')';  
        private const char parameterNextChar      = ',';  
  
        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,  
                                                   ref int state)  
        {  
            bool foundToken = false  
            string token = lex.GetNextToken();  
            if (token != null)  
            {  
                foundToken = true;  
                char c = token[0];  
                if (Char.IsPunctuation(c))  
                {  
                    tokenInfo.Type = TokenType.Operator;  
                    tokenInfo.Color = TokenColor.Keyword;  
                    tokenInfo.EndIndex = index;  
  
                    if (c == parameterListStartChar)  
                    {  
                        tokenInfo.Trigger |= TokenTriggers.ParameterStart;  
                    }  
                    else if (c == parameterListNextChar)  
                    {  
                        tokenInfo.Trigger |= TokenTriggers.ParameterNext;  
                    else if (c == parameterListEndChar)  
                    {  
                        tokenInfo.Trigger |= TokenTriggers.ParameterEnd;  
                    }  
                }  
            return foundToken;  
        }  
    }  
}  
```  
  
## Поддержка всплывающей подсказки параметр Info в средстве синтаксического анализа  
 <xref:Microsoft.VisualStudio.Package.Source> Класс делает некоторые предположения о содержимом <xref:Microsoft.VisualStudio.Package.AuthoringScope> и <xref:Microsoft.VisualStudio.Package.AuthoringSink> при отображается подсказка о параметрах и обновить классы.  
  
-   Получает средство синтаксического анализа <xref:Microsoft.VisualStudio.Package.ParseReason> при типизированных знак начала списка параметров.  
  
-   Расположение, заданное в <xref:Microsoft.VisualStudio.Package.ParseRequest> объект находится сразу после списка параметров начальный знак. Средство синтаксического анализа необходимо собирать все подписи всех объявлений методов в положение и хранить их в список в версии <xref:Microsoft.VisualStudio.Package.AuthoringScope> объекта. Этот список включает имя метода, метод типа \(или возвращаемого типа\) и список возможных параметров. Этот список позднее поиск сигнатуры метода или подписи будет отображаться в подсказке сведения о параметрах.  
  
 Средство синтаксического анализа необходимо затем синтаксический анализ строки, указанной в <xref:Microsoft.VisualStudio.Package.ParseRequest> объект для получения имени метода ввода, а также насколько вдоль пользователь находится в ввода параметров. Это достигается путем передачи имени метода <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> метод <xref:Microsoft.VisualStudio.Package.AuthoringSink> объекта и последующего вызова <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A> метод, если список параметров начальный знак анализируется, вызвав <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A> при анализе следующий символ список параметров метода и наконец вызов <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A> метод при анализе знак конца списка параметров. Результаты этих вызовов методов используются <xref:Microsoft.VisualStudio.Package.Source> класс соответствующим образом обновить подсказка о параметрах.  
  
### Пример  
 Вот строка текста, которое может быть введено пользователем. Числа ниже этой линии указывают, какой шаг берется средством синтаксического анализа в этой позиции в строке \(если анализа перемещается слева направо\). Здесь предполагается, что все, что перед строкой уже проверен для подписей метода, включая сигнатуру метода «testfunc».  
  
```  
testfunc("a string",3);  
     ^^          ^ ^  
     12          3 4  
```  
  
 Ниже описаны действия, которые использует средство синтаксического анализа:  
  
1.  Средство синтаксического анализа вызовов <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> с текстом «testfunc».  
  
2.  Вызывает средство синтаксического анализа <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A>.  
  
3.  Вызывает средство синтаксического анализа <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A>.  
  
4.  Вызывает средство синтаксического анализа <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A>.