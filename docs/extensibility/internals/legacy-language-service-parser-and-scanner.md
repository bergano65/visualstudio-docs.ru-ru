---
title: "Средство синтаксического анализа языка прежних версий службы и сканер | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parsers, language services [managed package framework]
- language services [managed package framework], Parsers
ms.assetid: 1ac3de27-a23b-438d-9593-389e45839cfa
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 30453237dcd95607a4f3524f115d16bc1cf4859a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="legacy-language-service-parser-and-scanner"></a>Средство синтаксического анализа языка прежних версий службы и сканера
Средство синтаксического анализа является сердцем языковой службы. Классы Managed Package Framework (MPF) языка требуют средства синтаксического анализа языка, чтобы выбрать сведения о коде отображения. Средство синтаксического анализа разделяет текст на лексические маркеры, а затем находит эти токены по типу и функциональные возможности.  
  
## <a name="discussion"></a>Обсуждение  
 Ниже приведен метод C#.  
  
```csharp  
namespace MyNamespace  
{  
    class MyClass  
    {  
        public void MyFunction(int arg1)  
        {  
            int var1 = arg1;  
        }  
    }  
}  
```  
  
 В этом примере токены, слов и знаков препинания. Ниже приведены типы токенов.  
  
|Имя токена|Тип маркера|  
|----------------|----------------|  
|пространство имен, класс, public void, int|ключевое-слово|  
|=|оператор|  
|{ } ( ) ;|разделитель|  
|MyNamespace, MyClass, MyFunction, arg1, переменная1|идентификатор|  
|MyNamespace|namespace|  
|MyClass|класс|  
|MyFunction|метод|  
|arg1|параметр|  
|переменная1|Локальная переменная|  
  
 Средство синтаксического анализа заключается в идентификации токены. Некоторые маркеры может иметь более одного типа. После идентификации токенов средства синтаксического анализа языковой службы можно использовать сведения для предоставления полезные функции, такие как выделение синтаксиса, парные фигурные скобки и IntelliSense операций.  
  
## <a name="types-of-parsers"></a>Типы синтаксического анализа  
 Средство синтаксического анализа языковой службы не является таким же, как средство синтаксического анализа, используются как часть одного компилятора. Тем не менее средство синтаксического анализа такого рода должен использовать сканер и средство синтаксического анализа в так же, как средство синтаксического анализа компилятор.  
  
-   Сканер используется для определения типов токенов. Эта информация используется для выделения синтаксиса и для быстрого определения типов токенов, способных вызывать другие операции, например, проверку соответствия фигурных скобок. Представленный этого средства проверки <xref:Microsoft.VisualStudio.Package.IScanner> интерфейса.  
  
-   Средство синтаксического анализа используется для описания функций и области токенов. Эта информация используется в операциях IntelliSense для определения элементов языка, таких как методы, переменные, параметры и объявления и приведены списки элементов и подписи методов в зависимости от контекста. Это средство синтаксического анализа также используется для поиска соответствующих пар элемента языка, например фигурные скобки и круглые скобки. Это средство синтаксического анализа осуществляется с помощью <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод <xref:Microsoft.VisualStudio.Package.LanguageService> класса.  
  
 Как реализовать сканера и синтаксического анализа языковой службы зависит от пользователя. Доступны несколько ресурсов, описывающих, как работают средства синтаксического анализа и способы написания собственного средства синтаксического анализа. Кроме того, доступны несколько бесплатных и коммерческих продуктов, помогающие при создании средство синтаксического анализа.  
  
### <a name="the-parsesource-parser"></a>Средство синтаксического анализа ParseSource  
 В отличие от синтаксического анализа, который используется как часть компилятора, (где токены преобразовываются в некоторую форму исполняемого кода) средство синтаксического анализа языковой службы может быть вызван разными причинами и во многих разных контекстах. Как реализовать этот подход в <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод <xref:Microsoft.VisualStudio.Package.LanguageService> класса принимает разработчик. Важно помнить, что <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод может вызываться в фоновом потоке.  
  
> [!CAUTION]
>  <xref:Microsoft.VisualStudio.Package.ParseRequest> Структура содержит ссылку на <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> объекта. Это <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> объект не может использоваться в фоновом потоке. На самом деле многие базовые классы MPF не может использоваться в фоновом потоке. К ним относятся <xref:Microsoft.VisualStudio.Package.Source>, <xref:Microsoft.VisualStudio.Package.ViewFilter>, <xref:Microsoft.VisualStudio.Package.CodeWindowManager> классы и любой другой класс, который прямо или косвенно обменивается данными с представлением.  
  
 Это средство синтаксического анализа обычно выполняет синтаксический анализ исходного в момент первой вызове или если синтаксический анализ причины значение <xref:Microsoft.VisualStudio.Package.ParseReason> присваивается. Последующие вызовы <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод обработки небольшую часть анализируемого кода и могут выполняться гораздо быстрее, используя результаты предыдущей операции полного синтаксического анализа. <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Метод взаимодействует результаты операции анализа через <xref:Microsoft.VisualStudio.Package.AuthoringSink> и <xref:Microsoft.VisualStudio.Package.AuthoringScope> объектов. <xref:Microsoft.VisualStudio.Package.AuthoringSink> Объект используется для сбора сведений по определенной причине синтаксического анализа, например, сведения о диапазоны фигурные или сигнатуры метода, которые имеют списки параметров. <xref:Microsoft.VisualStudio.Package.AuthoringScope> Предоставляет коллекции, объявления и сигнатуры методов, а также поддержку для перехода к дополнительной изменить параметр (**перейти к определению**, **перейти к объявлению**, **перейдите к Ссылаться на**).  
  
### <a name="the-iscanner-scanner"></a>IScanner сканера  
 Необходимо также реализовать сканер, который реализует <xref:Microsoft.VisualStudio.Package.IScanner>. Тем не менее так как этот сканер работает на основе строка за строкой, используя <xref:Microsoft.VisualStudio.Package.Colorizer> класса, это обычно проще реализовать. В начале каждой строки, дает MPF <xref:Microsoft.VisualStudio.Package.Colorizer> значение для использования в качестве переменной состояния, передаваемый сканер класса. В конце каждой строки сканер возвращает обновленное состояние переменной. MPF кэширует сведения о состоянии для каждой строки, чтобы сканер начала синтаксического анализа из любой строки без необходимости запуска в начале файла исходного кода. Это быстрое сканирование линию позволяет редактор быстрый отзыв для пользователя.  
  
## <a name="parsing-for-matching-braces"></a>Синтаксический анализ для парные фигурные скобки  
 В этом примере показан поток управления для сопоставления закрывающую фигурную скобку, данные, введенные пользователем. В этом процессе сканер, который используется для окраски также используется для определения типа маркера и ли токен может инициировать операцию фигурная скобка совпадения. При обнаружении триггер <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод вызывается, чтобы найти парную скобку. Наконец будут выделены две фигурные скобки.  
  
 Даже если фигурные скобки используются имена триггеров и причин синтаксический анализ, этот процесс не ограничивается фактическое фигурные скобки. Каждая пара символов, которые указано соответствие пары поддерживается. Примеры (и), \< и >, и [и].  
  
 Предположим, что службе языка поддерживает парные фигурные скобки.  
  
1.  Пользователь вводит закрывающей фигурной скобки (}).  
  
2.  Фигурная скобка вставляется в позицию курсора в исходном файле, и курсор перемещается вперед на один.  
  
3.  <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Метод <xref:Microsoft.VisualStudio.Package.Source> класса вызывается с типизированным закрывающую фигурную скобку.  
  
4.  <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Вызовы метода <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> метод <xref:Microsoft.VisualStudio.Package.Source> класса, чтобы получить маркер позиции непосредственно перед текущей позицией курсора. Этот токен соответствует типизированный закрывающая фигурная скобка).  
  
    1.  <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> Вызовы метода <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> метод <xref:Microsoft.VisualStudio.Package.Colorizer> объекта, чтобы получить все токены в текущей строке.  
  
    2.  <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> Вызовы метода <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> метод <xref:Microsoft.VisualStudio.Package.IScanner> вместе с текстом текущей строки.  
  
    3.  <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> Многократно вызывает метод <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> метод <xref:Microsoft.VisualStudio.Package.IScanner> объекта для сбора всех токенов из текущей строки.  
  
    4.  <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> Метод вызывает закрытый метод в <xref:Microsoft.VisualStudio.Package.Source> класса для получения маркера, который содержит нужное место и передает в список лексем, полученный от <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> метод.  
  
5.  <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Метод ищет флагом маркера триггер <xref:Microsoft.VisualStudio.Package.TokenTriggers> на маркер, возвращенный <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> метода, то есть токен, представляющий закрывающая фигурная скобка).  
  
6.  Если триггер флаг <xref:Microsoft.VisualStudio.Package.TokenTriggers> найден, <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> метод в <xref:Microsoft.VisualStudio.Package.Source> класс называется.  
  
7.  <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> Метод начинается операция синтаксического анализа со значением причина синтаксического анализа <xref:Microsoft.VisualStudio.Package.ParseReason>. Эта операция в конечном итоге вызывает <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод <xref:Microsoft.VisualStudio.Package.LanguageService> класса. Если включен асинхронной синтаксического анализа, это вызов <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метода происходит в фоновом потоке.  
  
8.  После завершения операции анализа внутренний обработчик завершения (также известный как метод обратного вызова) с именем `HandleMatchBracesResponse` вызывается в <xref:Microsoft.VisualStudio.Package.Source> класса. Этот вызов выполняется автоматически <xref:Microsoft.VisualStudio.Package.LanguageService> базового класса, не средством синтаксического анализа.  
  
9. `HandleMatchBracesResponse` Метод получает список диапазонов из <xref:Microsoft.VisualStudio.Package.AuthoringSink> объект, хранящийся в <xref:Microsoft.VisualStudio.Package.ParseRequest> объекта. (Область является <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> структуру, которая указывает диапазон строк и символов в исходном файле.) Этот список диапазонов обычно содержит два диапазона, по одной для открывающей и закрывающей фигурными скобками.  
  
10. `HandleBracesResponse` Вызовы метода <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> объект, хранящийся в <xref:Microsoft.VisualStudio.Package.ParseRequest> объекта. Это подчеркивает заданного диапазона.  
  
11. Если <xref:Microsoft.VisualStudio.Package.LanguagePreferences> свойство <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> включен, `HandleBracesResponse` метод получает текст, который охватывается соответствующий диапазон и отображает первые 80 знаков, охватывающих в строке состояния. Это работает лучше, если <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод включает элемент языка, прилагаемый к соответствующей пары. Дополнительные сведения см. в описании свойства <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>.  
  
12. Договорились.  
  
### <a name="summary"></a>Сводка  
 Операции сопоставления фигурные скобки обычно ограничивается простой пары элементов языка. Более сложные элементы, такие как сопоставления тройки («`if(...)`«,»`{`«и»`}`», или "`else`«,»`{`«и»`}`»), могут быть выделены как часть операции завершение слов. Например, после завершения слово «else» сопоставления "`if`» инструкции могут быть выделены. Если бы ряд `if` / `else if` инструкции, все из них может выделяются с помощью того же механизма как парные фигурные скобки. <xref:Microsoft.VisualStudio.Package.Source> Базовый класс уже поддерживает, а именно: сканер должен возвращать значение токена триггера <xref:Microsoft.VisualStudio.Package.TokenTriggers> в сочетании с значение триггера <xref:Microsoft.VisualStudio.Package.TokenTriggers> для маркера, перед позицией курсора.  
  
 Дополнительные сведения см. в разделе [парные фигурные скобки в языковую службу прежних версий](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).  
  
## <a name="parsing-for-colorization"></a>Синтаксический анализ окраски  
 Выделение цветом исходный код структурирован, просто определите тип данных, цвет маркера и возвращают сведения об этом типе. <xref:Microsoft.VisualStudio.Package.Colorizer> Класс действует как посредник между редактор и сканер цвет информацию о каждый маркер. <xref:Microsoft.VisualStudio.Package.Colorizer> Класс использует <xref:Microsoft.VisualStudio.Package.IScanner> объекта для упрощения выделения цветом строки, так и для сбора сведений о состоянии для всех строк в исходном файле. В классах службы языка MPF <xref:Microsoft.VisualStudio.Package.Colorizer> класса не должен быть переопределен, поскольку он взаимодействует с помощью сканера только с использованием <xref:Microsoft.VisualStudio.Package.IScanner> интерфейса. Объект, который реализует <xref:Microsoft.VisualStudio.Package.IScanner> интерфейса путем переопределения <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> метод <xref:Microsoft.VisualStudio.Package.LanguageService> класса.  
  
 <xref:Microsoft.VisualStudio.Package.IScanner> Получает строки исходного кода с помощью сканера <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> метод. Вызовы <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> метод повторяются, чтобы получить следующий токен в строке, пока не будет исчерпан токенов в строке. Окраски MPF обрабатывает все исходного кода, как последовательность строк. Таким образом сканер должен иметь возможность справиться с источником, поступающих на него как строки. Кроме того можно передать любой строки в сканер в любое время и гарантируется только то, что сканер получает переменной состояния из строку перед строкой будет проверяться.  
  
 <xref:Microsoft.VisualStudio.Package.Colorizer> Класс также используется для определения маркера триггеров. Эти триггеры сообщить MPF, что данная лексема может инициировать более сложная операции, такие как завершение слов или парные фигурные скобки. Поскольку определения таких триггеров должен быть быстрым и должно находиться в любом месте, сканер наилучшим образом подходит для этой задачи.  
  
 Дополнительные сведения см. в разделе [синтаксис Раскраска в языковую службу прежних версий](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).  
  
## <a name="parsing-for-functionality-and-scope"></a>Синтаксический анализ для функций и области  
 Синтаксический анализ для функции и область требует больше усилий, чем просто определение типов маркеров, которые встречаются. Средство синтаксического анализа должен определить не только тип маркера, но функциональные возможности, для которого используется токен. Например идентификатор-это просто имя, но на вашем языке идентификатор может быть имя класса, пространства имен, метода или переменной, в зависимости от контекста. Общий тип маркера может быть идентификатором, но идентификатор также могут иметься другие значения, в зависимости от того, что это такое и где оно определено. Эта Идентификация требуется средство синтаксического анализа более сложных знания о языке, который анализировался. Это место, куда <xref:Microsoft.VisualStudio.Package.AuthoringSink> входящий класса. <xref:Microsoft.VisualStudio.Package.AuthoringSink> Класс собирает сведения об идентификаторах, методы, соответствующие пары языков (например, фигурные скобки и круглые скобки) и языка тройки (аналогично пары языков, за исключением того, состоит из трех частей, например, «`foreach()`» «`{`«и»`}`»). Кроме того, можно переопределить <xref:Microsoft.VisualStudio.Package.AuthoringSink> класс для поддержки идентификационный код, который используется в начале проверки точки останова, чтобы отладчик не нужно загружать, и **видимые** окна отладки, показывающий локального переменные и параметры автоматически при программа отлаживается; требуется средство синтаксического анализа для определения соответствующих локальных переменных и параметров, помимо тех, которые предоставляет отладчик.  
  
 <xref:Microsoft.VisualStudio.Package.AuthoringSink> Объект передается в средство синтаксического анализа в рамках <xref:Microsoft.VisualStudio.Package.ParseRequest> объекта, а новые <xref:Microsoft.VisualStudio.Package.AuthoringSink> объект создаются при каждой, новый <xref:Microsoft.VisualStudio.Package.ParseRequest> создан объект. Кроме того <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод должен возвращать <xref:Microsoft.VisualStudio.Package.AuthoringScope> объект, который используется для обработки различных операций IntelliSense. <xref:Microsoft.VisualStudio.Package.AuthoringScope> Сохраняет список для объявлений и список для методов, либо из которых заполнен, в зависимости от причины для синтаксического анализа. <xref:Microsoft.VisualStudio.Package.AuthoringScope> Класс должен быть реализован.  
  
## <a name="see-also"></a>См. также  
 [Реализация службы языка для прежних версий](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [Общие сведения о службе языка прежних версий](../../extensibility/internals/legacy-language-service-overview.md)   
 [Синтаксис Раскраска в языковую службу прежних версий](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)   
 [Парные фигурные скобки в языковой службе прежних версий](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)