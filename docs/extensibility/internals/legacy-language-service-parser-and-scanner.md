---
title: "Средство синтаксического анализа языка прежних версий службы и сканера | Microsoft Docs"
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
  - "анализаторы языковые службы [платформа управляемых пакетов]"
  - "языковые службы [платформа управляемых пакетов] средства синтаксического анализа"
ms.assetid: 1ac3de27-a23b-438d-9593-389e45839cfa
caps.latest.revision: 20
caps.handback.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
---
# Средство синтаксического анализа языка прежних версий службы и сканера
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Анализатор является сердцем языковой службы. Классы управляемых пакета Framework Являющиеся языка требуют синтаксического анализа языка, чтобы выбрать сведения о коде, который будет отображаться. Средство синтаксического анализа разделяет текст на лексические маркеры, а затем находит эти маркеры по типу и функциональные возможности.  
  
## Обсуждение  
 Ниже приведен метод C\#.  
  
```c#  
namespace MyNamespace { class MyClass { public void MyFunction(int arg1) { int var1 = arg1; } } }  
```  
  
 В этом примере используются токены, слов и знаков препинания. Ниже приведены типы маркеров.  
  
|Имя маркера|Тип маркера|  
|-----------------|-----------------|  
|пространство имен, класс, public void, int|ключевое\-слово|  
|\=|оператор|  
|{ } \( \) ;|разделитель|  
|MyNamespace, MyClass, MyFunction, arg1, var1|идентификатор|  
|MyNamespace|namespace|  
|MyClass|класс|  
|MyFunction|метод|  
|arg1|параметр|  
|var1|Локальная переменная|  
  
 Средство синтаксического анализа заключается в идентификации маркеры. Некоторые маркеры могут иметь более одного типа. После синтаксического анализа обнаружила токены, языковой службы можно использовать сведения для предоставления полезных функций, например, выделение синтаксиса, парные фигурные скобки и операции IntelliSense.  
  
## Типы средства синтаксического анализа  
 Средство синтаксического анализа языковой службы не является таким же, как средство синтаксического анализа, используется как часть компилятора. Тем не менее средство синтаксического анализа такого рода намерен использовать так же, как средство синтаксического анализа компилятор сканера и средство синтаксического анализа.  
  
-   Сканер используется для определения типов токенов. Эта информация используется для выделения синтаксиса и для быстрого определения типов маркеров, вызывающие другие операции, например, проверка парности фигурных скобок. Представленный этого средства проверки <xref:Microsoft.VisualStudio.Package.IScanner> интерфейса.  
  
-   Средство синтаксического анализа используется для описания функций и области токенов. Эта информация используется в операциях IntelliSense для определения элементов языка, таких как методы, переменные, параметры и объявления и предоставления списков членов и подписях метода, на основе контекста. Это средство синтаксического анализа также используется для поиска совпадающие пары элемент языка, таких как фигурные скобки и скобки. Это средство синтаксического анализа осуществляется с помощью <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод <xref:Microsoft.VisualStudio.Package.LanguageService> класса.  
  
 Как реализовать сканера и синтаксического анализатора языка службы зависит от вас. Доступны несколько ресурсов, описывающих, как работают средства синтаксического анализа и способы написания собственного средства синтаксического анализа. Кроме того, доступны несколько бесплатных и коммерческих продуктов, предназначенных для создания средство синтаксического анализа.  
  
### Средство синтаксического анализа ParseSource  
 В отличие от средства синтаксического анализа, используемый как часть компилятора \(где маркеры преобразуются в некоторой формы исполняемого кода\) средство синтаксического анализа языковой службы может быть вызван по разным причинам и во многих разных контекстах. Как реализовать этот подход в <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод <xref:Microsoft.VisualStudio.Package.LanguageService> класса зависит от вас. Важно помнить, что <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод может вызываться в фоновом потоке.  
  
> [!CAUTION]
>  <xref:Microsoft.VisualStudio.Package.ParseRequest> Структура содержит ссылку на <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> объект. Это <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> объект не может использоваться в фоновом потоке. На самом деле многие из базовых классов MPF не может использоваться в фоновом потоке. К ним относятся <xref:Microsoft.VisualStudio.Package.Source>, <xref:Microsoft.VisualStudio.Package.ViewFilter>, <xref:Microsoft.VisualStudio.Package.CodeWindowManager> классов и любой другой класс, который прямо или косвенно взаимодействует с представлением.  
  
 Это средство синтаксического анализа обычно анализирует весь исходный в момент первой называется или когда синтаксический анализ причин значение <xref:Microsoft.VisualStudio.Package.ParseReason> присваивается. Последующие вызовы <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод обработки небольшую часть анализируемого кода и могут выполняться гораздо быстрее, используя результаты предыдущей операции полного анализа.<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Метод передает результаты операции анализа через <xref:Microsoft.VisualStudio.Package.AuthoringSink> и <xref:Microsoft.VisualStudio.Package.AuthoringScope> объектов.<xref:Microsoft.VisualStudio.Package.AuthoringSink> Объект используется для сбора сведений по определенной причине синтаксического анализа, например, сведения о диапазоны фигурные или сигнатуры метода, которые имеют списки параметров.<xref:Microsoft.VisualStudio.Package.AuthoringScope> Предоставляет коллекции, объявления и подписи методов, а также поддержка перейти к сложные изменить параметр \(**Перейти к определению**, **Перейти к объявлению**, **Перейти по ссылке**\).  
  
### IScanner сканера  
 Необходимо также реализовать сканер, который реализует <xref:Microsoft.VisualStudio.Package.IScanner>. Тем не менее поскольку этот сканер работает на основе строка за строкой, используя <xref:Microsoft.VisualStudio.Package.Colorizer> класс, он обычно проще реализовать. В начале каждой строки, предоставляет MPF <xref:Microsoft.VisualStudio.Package.Colorizer> класса значение для использования в качестве переменной состояния, передаваемый программе поиска вирусов. В конце каждой строки сканер возвращает обновленное состояние переменной. MPF кэширует сведения о состоянии для каждой строки, чтобы сканер начала разбора из любой строки без необходимости в начале файла исходного кода. Это быстрое сканирование одну строку позволяет редактор быстрый отзыв для пользователя.  
  
## Синтаксический анализ парных скобок  
 В этом примере показан поток управления для соответствия закрывающую фигурную скобку, данные, введенные пользователем. В этом процессе сканер, который используется для окраски также используется для определения типа маркера и ли токен может инициировать операцию соответствие скобок. При обнаружении триггера, <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод вызывается, чтобы найти парную скобку. Наконец будут выделены две фигурные скобки.  
  
 Даже если скобки используются имена триггеров и синтаксический анализ причин, этот процесс не только фактические фигурные скобки. Поддерживается любая пара символов, заданные для соответствующей пары. Примеры \(и\), \< и \>, и \[и\].  
  
 Предположим, что языковая служба поддерживает парные фигурные скобки.  
  
1.  Пользователь вводит закрывающей фигурной скобки \(}\).  
  
2.  Фигурная скобка вставляется в позиции курсора в исходном файле, и курсор увеличивается на единицу.  
  
3.  <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Метод <xref:Microsoft.VisualStudio.Package.Source> класса вызывается с типизированным закрывающую фигурную скобку.  
  
4.  <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Вызовы метода <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> метод <xref:Microsoft.VisualStudio.Package.Source> для получения маркера на позицию непосредственно перед текущей позицией курсора. Этот токен соответствует типизированный закрывающая фигурная скобка\).  
  
    1.  <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> Вызовы метода <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> метод <xref:Microsoft.VisualStudio.Package.Colorizer> объекта, чтобы получить все маркеры в текущей строке.  
  
    2.  <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> Вызовы метода <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> метод <xref:Microsoft.VisualStudio.Package.IScanner> вместе с текстом текущей строки.  
  
    3.  <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> Многократно вызывает метод <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> метод <xref:Microsoft.VisualStudio.Package.IScanner> объекта, чтобы собрать все маркеры из текущей строки.  
  
    4.  <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> Метод вызывает закрытый метод в <xref:Microsoft.VisualStudio.Package.Source> класса для получения маркера, который содержит нужное место и передает в список лексем, полученные из <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> метод.  
  
5.  <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Метод ищет маркера триггер флагом <xref:Microsoft.VisualStudio.Package.TokenTriggers> на маркер, возвращенный <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> метода, то есть маркер, представляющий закрывающая фигурная скобка\).  
  
6.  Если триггер флаг <xref:Microsoft.VisualStudio.Package.TokenTriggers> найден, <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> метод <xref:Microsoft.VisualStudio.Package.Source> класса вызывается.  
  
7.  <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> Метод начинается операция синтаксического анализа со значением причина синтаксического анализа <xref:Microsoft.VisualStudio.Package.ParseReason>. Эта операция в конечном итоге вызывает <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод <xref:Microsoft.VisualStudio.Package.LanguageService> класса. При включении асинхронного анализа это вызов <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метода происходит в фоновом потоке.  
  
8.  После завершения операции анализа обработчик внутреннего завершения \(также известный как метод обратного вызова\) с именем `HandleMatchBracesResponse` вызывается в <xref:Microsoft.VisualStudio.Package.Source> класса. Этот вызов выполняется автоматически <xref:Microsoft.VisualStudio.Package.LanguageService> базового класса, не средством синтаксического анализа.  
  
9. `HandleMatchBracesResponse` Метод получает список диапазонов из <xref:Microsoft.VisualStudio.Package.AuthoringSink> объект, хранящийся в <xref:Microsoft.VisualStudio.Package.ParseRequest> объекта. \(Диапазон – это <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> Структура, которая указывает диапазон строк и символов в исходном файле.\) Этот список диапазонов обычно содержит два диапазона, открывающей и закрывающей фигурными скобками.  
  
10. `HandleBracesResponse` Вызовы метода <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> объекта, хранящегося в <xref:Microsoft.VisualStudio.Package.ParseRequest> объекта. Это подчеркивает заданного диапазона.  
  
11. Если <xref:Microsoft.VisualStudio.Package.LanguagePreferences> свойство <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> включено, `HandleBracesResponse` метод получает текст, который охватывается соответствующий диапазон и отображает первые 80 знаков, диапазона в строке состояния. Это работает лучше, если <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод включает элемент языка, сопровождающий совпадающую пару. Дополнительные сведения см. в описании свойства <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>.  
  
12. Сделать.  
  
### Сводка  
 Операции сопоставления фигурные скобки обычно ограничена простые пары элементов языка. Более сложные элементы, такие как сопоставления тройки \(»`if(…)`«,»`{`«и»`}`», или «`else`«,»`{`«и»`}`»\), может быть выделен как часть операции завершение слов. Например, после завершения слово «else» соответствующий «`if`» инструкции могут быть выделены. При отсутствии ряд `if`и`else if` инструкций, все из них можно выделить с помощью того же механизма как фигурные.<xref:Microsoft.VisualStudio.Package.Source> Базовый класс уже поддерживает это, следующим образом: сканер должен возвращать значение маркера триггера <xref:Microsoft.VisualStudio.Package.TokenTriggers> в сочетании с значение триггера <xref:Microsoft.VisualStudio.Package.TokenTriggers> для маркера, до позиции курсора.  
  
 Дополнительные сведения см. в разделе [Проверка парности фигурных скобок в языковую службу для прежних версий](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).  
  
## Синтаксический анализ окраски  
 Выделение цветом исходный код прост, просто идентификации типа данных цвет маркера и возвращают сведения об этом типе.<xref:Microsoft.VisualStudio.Package.Colorizer> Класс действует как посредник между редактор и сканер цвет информацию о каждого маркера.<xref:Microsoft.VisualStudio.Package.Colorizer> Класс использует <xref:Microsoft.VisualStudio.Package.IScanner> объекта для выделения цветом строки и собрать сведения о состоянии для всех строк в исходном файле. В классах службы языка MPF <xref:Microsoft.VisualStudio.Package.Colorizer> обязательно должен быть переопределен, поскольку он взаимодействует с сканер только через <xref:Microsoft.VisualStudio.Package.IScanner> интерфейса. Необходимо указать объект, реализующий <xref:Microsoft.VisualStudio.Package.IScanner> интерфейс путем переопределения <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> метод <xref:Microsoft.VisualStudio.Package.LanguageService> класса.  
  
 <xref:Microsoft.VisualStudio.Package.IScanner> Сканера является заданной строки исходного кода через <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> метод. Вызовы <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> метод повторяются для получения следующий токен в строке, пока не будет исчерпан строке маркеров. Окраски MPF обрабатывает весь исходный код, как последовательность строк. Таким образом сканер должен уметь справляться с источником, поступающие на него как строки. Кроме того можно передать любой строки в сканер в любое время, и гарантируется только то, что сканер получает переменной состояния из строку перед строкой будет проверяться.  
  
 <xref:Microsoft.VisualStudio.Package.Colorizer> Класс также используется для определения маркера триггеров. Эти триггеры сообщить MPF, что данная лексема может инициировать более сложные операции, такие как завершение слов или парных скобок. Поскольку определение таких триггеров должен быть быстрым и должно происходить в любом расположении, сканер лучше всего подходит для этой задачи.  
  
 Для получения дополнительной информации см. [Синтаксис выделения цветом в языковую службу для прежних версий](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).  
  
## Синтаксический анализ для функций и области  
 Синтаксический анализ для функций и области требует больше усилий, чем просто определение типов маркеров, которые встречаются. Средство синтаксического анализа должен определить не только тип маркера, но функциональные возможности, для которого используется токен. Например идентификатор\-это просто имя, но на вашем языке идентификатор может быть имя класса, пространства имен, метода или переменной, в зависимости от контекста. Общий тип маркера может быть идентификатором, но идентификатор может также имеют другие значения, в зависимости от того, что это такое и где он определен. Эта Идентификация требуется средство синтаксического анализа для более глубокого знания языка, при анализе. Вот где <xref:Microsoft.VisualStudio.Package.AuthoringSink> класса могут пригодиться.<xref:Microsoft.VisualStudio.Package.AuthoringSink> Класс собирает сведения об идентификаторах, методы, соответствующие пары языков \(например, фигурные скобки и скобки\) и тройки языка \(аналогично языковых пар, за исключением того, что состоит из трех частей, например, «`foreach()`» «`{`«и»`}`»\). Кроме того, можно переопределить <xref:Microsoft.VisualStudio.Package.AuthoringSink> класс для поддержки идентификационный код, который используется в начале проверки точек останова, чтобы отладчик не нужно загружать, и **Видимые** окна отладки, показывающий локальные переменные и параметры автоматически при отлаживаемой программы и требуется средство синтаксического анализа для определения соответствующих локальных переменных и параметров, помимо тех, которые предоставляет отладчик.  
  
 <xref:Microsoft.VisualStudio.Package.AuthoringSink> Объект передается в средство синтаксического анализа в рамках <xref:Microsoft.VisualStudio.Package.ParseRequest> объекта, а новые <xref:Microsoft.VisualStudio.Package.AuthoringSink> объект создается каждый раз, новый <xref:Microsoft.VisualStudio.Package.ParseRequest> создается объект. Кроме того <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод должен возвращать <xref:Microsoft.VisualStudio.Package.AuthoringScope> объект, который используется для обработки различных операций IntelliSense.<xref:Microsoft.VisualStudio.Package.AuthoringScope> Сохраняет список для объявлений и список методов, либо из которых заполнен, в зависимости от причины для синтаксического анализа.<xref:Microsoft.VisualStudio.Package.AuthoringScope> Класс должен быть реализован.  
  
## См. также  
 [Реализация службы языка прежних версий](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [Общие сведения о службе устаревших языка](../../extensibility/internals/legacy-language-service-overview.md)   
 [Синтаксис выделения цветом в языковую службу для прежних версий](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)   
 [Проверка парности фигурных скобок в языковую службу для прежних версий](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)