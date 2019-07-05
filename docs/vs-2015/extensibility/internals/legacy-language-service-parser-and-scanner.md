---
title: Средство синтаксического анализа устаревший языковой службы и сканер | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- parsers, language services [managed package framework]
- language services [managed package framework], Parsers
ms.assetid: 1ac3de27-a23b-438d-9593-389e45839cfa
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 64f9a9f4d0785f033191ab527084f0dddb1ff104
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63434367"
---
# <a name="legacy-language-service-parser-and-scanner"></a>Средство синтаксического анализа и сканер языковой службы прежних версий
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Анализатор является сердцем языковой службы. Классы Managed Package Framework (MPF) языка требуется средство синтаксического анализа языка, чтобы выбрать сведения о коде отображения. Средство синтаксического анализа разделяет текст на лексических маркеров, а затем определяет эти маркеры по типу и функциональные возможности.  
  
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
  
 В этом примере токены являются слов и знаков препинания. Ниже приведены типы маркеров.  
  
|Имя токена|Тип маркера|  
|----------------|----------------|  
|пространство имен, класс, public void, int|ключевое-слово|  
|=|оператор|  
|{ } ( ) ;|разделитель|  
|MyNamespace, MyClass, MyFunction, arg1, var1|идентификатор|  
|MyNamespace|namespace|  
|MyClass|класс|  
|MyFunction|метод|  
|arg1|параметр|  
|var1|Локальная переменная|  
  
 Роль средство синтаксического анализа заключается в том, чтобы идентифицировать токены. Некоторые маркеры могут иметь более одного типа. После синтаксического анализа обнаружила токены, языковой службы можно использовать сведения для предоставления полезных функций, таких как выделение синтаксиса, парные фигурные скобки и операции IntelliSense.  
  
## <a name="types-of-parsers"></a>Типы средств синтаксического анализа  
 Средства синтаксического анализа языка службы не является таким же, как средство синтаксического анализа, используемые в рамках одного компилятора. Тем не менее такого рода средство синтаксического анализа необходимо использовать средство синтаксического анализа и сканер в так же, как средство синтаксического анализа компилятора.  
  
- Сканер используется для определения типов токенов. Эти данные используется для выделения синтаксиса и для быстрого определения типов токенов, способных вызывать другие операции, например, проверку соответствия фигурных скобок. После этого средство проверки представленного <xref:Microsoft.VisualStudio.Package.IScanner> интерфейс.  
  
- Средство синтаксического анализа используется для описания функций и области токенов. Эта информация используется в операции IntelliSense для идентификации элементов языка, таких как методы, переменные, параметры и объявления и приведены списки элементов и подписи методов, на основе контекста. Это средство синтаксического анализа также используется для поиска соответствия пар элементов языка, таких как фигурные скобки и круглые скобки. Это средство синтаксического анализа осуществляется через <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод в <xref:Microsoft.VisualStudio.Package.LanguageService> класса.  
  
  Как реализовать для языковой службы сканера и средство синтаксического анализа принимает разработчик. Доступны несколько ресурсов, описывающих, как работают средства синтаксического анализа и способах создания собственного средства синтаксического анализа. Кроме того, доступны несколько бесплатных и коммерческих продуктов, предназначенных для создания средство синтаксического анализа.  
  
### <a name="the-parsesource-parser"></a>Средство синтаксического анализа ParseSource  
 В отличие от средства синтаксического анализа, который используется как часть компилятора, (где маркеры преобразуются в некоторую форму исполняемого кода) средства синтаксического анализа языка службы может быть вызван по разным причинам и во многих разных контекстах. Как реализовать этот подход в <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод в <xref:Microsoft.VisualStudio.Package.LanguageService> класса принимает разработчик. Важно помнить, что <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод может вызываться в фоновом потоке.  
  
> [!CAUTION]
> <xref:Microsoft.VisualStudio.Package.ParseRequest> Структура содержит ссылку на <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> объекта. Это <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> объект не может использоваться в фоновом потоке. На самом деле многие базовые классы MPF не может использоваться в фоновом потоке. К ним относятся <xref:Microsoft.VisualStudio.Package.Source>, <xref:Microsoft.VisualStudio.Package.ViewFilter>, <xref:Microsoft.VisualStudio.Package.CodeWindowManager> классов и любой другой класс, который прямо или косвенно взаимодействует с представлением.  
  
 Это средство синтаксического анализа обычно анализирует источник в момент первой он вызывается или когда синтаксический анализ причин значение <xref:Microsoft.VisualStudio.Package.ParseReason> прав. Последующие вызовы <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод обработки небольшая часть анализируемого кода и могут выполняться гораздо быстрее, используя результаты предыдущей операции полного синтаксического анализа. <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Метод передает результаты операции анализа через <xref:Microsoft.VisualStudio.Package.AuthoringSink> и <xref:Microsoft.VisualStudio.Package.AuthoringScope> объектов. <xref:Microsoft.VisualStudio.Package.AuthoringSink> Объект используется для сбора сведений по определенной причине синтаксического анализа, например, сведения о диапазоны фигурные или сигнатур метода, которые имеют списки параметров. <xref:Microsoft.VisualStudio.Package.AuthoringScope> Предоставляет коллекции, объявления и подписи методов, а также поддержку для перехода к дополнительной изменить параметр (**перейти к определению**, **перейти к объявлению**, **перейти к Ссылаться на**).  
  
### <a name="the-iscanner-scanner"></a>Средство проверки IScanner  
 Необходимо также реализовать сканер, который реализует <xref:Microsoft.VisualStudio.Package.IScanner>. Тем не менее это средство проверки работает по принципу по одной строке через <xref:Microsoft.VisualStudio.Package.Colorizer> класса, это обычно проще в реализации. В начале каждой строки, дает MPF <xref:Microsoft.VisualStudio.Package.Colorizer> класса значение для использования в качестве переменной состояния, передается к сканеру. В конце каждой строки сканер возвращает переменную обновленное состояние. MPF кэширует сведения о состоянии для каждой строки таким образом, чтобы средство проверки можно запустить анализ из любой строки без необходимости запуска в начале исходного файла. Это быстрое сканирование одну строку позволяет редактор быстрый отзыв для пользователя.  
  
## <a name="parsing-for-matching-braces"></a>Синтаксический анализ для соответствующих фигурных скобок  
 В этом примере показан поток управления для сопоставления закрывающую фигурную скобку, введенный пользователем. В этом процессе сканер, используемый для окрашивания также используется для определения типа маркера и ли маркер может активировать операцию соответствие скобок. Если определенный триггером <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> был вызван для поиска парной скобке. Наконец будут выделены две фигурные скобки.  
  
 Несмотря на то, что в фигурные скобки используются в имен триггеров и синтаксический анализ причин, этот процесс не ограничивается фактическое фигурные скобки. Поддерживается любой пары символов, указанный как совпадающую пару. Примеры (и), \< и >, и [и].  
  
 Предположим, что служба языка поддерживает парные фигурные скобки.  
  
1. Пользователь вводит закрывающую фигурную скобку (}).  
  
2. Фигурная скобка вставляется в позиции курсора в исходном файле, и курсор увеличивается на единицу.  
  
3. <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Метод в <xref:Microsoft.VisualStudio.Package.Source> класса вызывается с типизированным закрывающей фигурной скобки.  
  
4. <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Вызовы методов <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> метод в <xref:Microsoft.VisualStudio.Package.Source> класса для получения маркера в позицию непосредственно перед текущей позицией курсора. Этот токен соответствует типизированный закрывающая фигурная скобка).  
  
    1. <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> Вызовы методов <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> метод <xref:Microsoft.VisualStudio.Package.Colorizer> объекта, чтобы получить все токены в текущей строке.  
  
    2. <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> Вызовы методов <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> метод <xref:Microsoft.VisualStudio.Package.IScanner> с текстом в текущей строке.  
  
    3. <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> Многократно вызывает метод <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> метод <xref:Microsoft.VisualStudio.Package.IScanner> объекта для сбора всех маркеров из текущей строки.  
  
    4. <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> Метод вызывает закрытый метод <xref:Microsoft.VisualStudio.Package.Source> класса для получения маркера, который содержит нужное место, и передает в списке маркеров получен из <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> метод.  
  
5. <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Метод ищет флаг маркера триггера <xref:Microsoft.VisualStudio.Package.TokenTriggers> в маркере, который возвращается из <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> метод, то есть токен, представляющий закрывающая фигурная скобка).  
  
6. Если флаг триггер <xref:Microsoft.VisualStudio.Package.TokenTriggers> найден, <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> метод в <xref:Microsoft.VisualStudio.Package.Source> класс называется.  
  
7. <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> Метод начинает операцию анализа со значением причина синтаксического анализа <xref:Microsoft.VisualStudio.Package.ParseReason>. Эта операция в конечном итоге вызывает <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод <xref:Microsoft.VisualStudio.Package.LanguageService> класса. Если асинхронный анализ включена, это вызов <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метода происходит в фоновом потоке.  
  
8. После завершения операции синтаксического анализа внутренний обработчик завершения (также известный как метод обратного вызова) с именем `HandleMatchBracesResponse` вызывается в <xref:Microsoft.VisualStudio.Package.Source> класса. Этот вызов выполняется автоматически по <xref:Microsoft.VisualStudio.Package.LanguageService> базового класса, не средством синтаксического анализа.  
  
9. `HandleMatchBracesResponse` Метод получает список диапазонов из <xref:Microsoft.VisualStudio.Package.AuthoringSink> объект, хранящийся в <xref:Microsoft.VisualStudio.Package.ParseRequest> объекта. (Диапазон – это <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> структуры, которое указывает диапазон строк и символов в исходном файле.) Этот список диапазонов обычно содержит два диапазона, по одной для открывающей и закрывающей фигурными скобками.  
  
10. `HandleBracesResponse` Вызовы методов <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> объект, хранящийся в <xref:Microsoft.VisualStudio.Package.ParseRequest> объекта. Это подчеркивает заданных диапазонов.  
  
11. Если <xref:Microsoft.VisualStudio.Package.LanguagePreferences> свойство <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> включен, `HandleBracesResponse` метод получает текст, который охватывается соответствующий диапазон и отображает первые 80 знаков, охватывающих в строке состояния. Это работает лучше, если <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод включает элементом языка, который прилагается к соответствующей пары. Дополнительные сведения см. в описании свойства <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>.  
  
12. Договорились.  
  
### <a name="summary"></a>Сводка  
 Операции сопоставления фигурные скобки обычно ограничена простых пар элементов языка. Более сложные элементы, такие как сопоставления триад («`if(…)`«,»`{`«и»`}`«, или "`else`«,»`{`«и»`}`«), может быть выделен как часть операции завершения слова. Например, после завершения слово «else» сопоставления "`if`" инструкции могут быть выделены. При наличии ряд `if` / `else if` инструкций, то они могут выделяться с помощью того же механизма как парные фигурные скобки. <xref:Microsoft.VisualStudio.Package.Source> Базовый класс уже поддерживает это, как показано ниже: Сканер должен возвращать значение маркера триггера <xref:Microsoft.VisualStudio.Package.TokenTriggers> вместе со значением триггера <xref:Microsoft.VisualStudio.Package.TokenTriggers> для токен, который предшествует позиции курсора.  
  
 Дополнительные сведения см. в разделе [парные фигурные скобки в языковой службе прежних версий](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).  
  
## <a name="parsing-for-colorization"></a>Синтаксический анализ для окрашивания  
 Выделения цветом исходный код прост, просто определите тип данных, цвет маркера и возвращают сведения об этом типе. <xref:Microsoft.VisualStudio.Package.Colorizer> Класс действует как посредник между редактором и сканер цвет информацию о каждом токене. <xref:Microsoft.VisualStudio.Package.Colorizer> Класс использует <xref:Microsoft.VisualStudio.Package.IScanner> объекта для упрощения выделения цветом строки, так и для сбора сведений о состоянии для всех строк в исходном файле. В классах службы языка MPF <xref:Microsoft.VisualStudio.Package.Colorizer> обязательно должен быть переопределен, поскольку он взаимодействует с помощью сканера только с помощью <xref:Microsoft.VisualStudio.Package.IScanner> интерфейс. Объект, который реализует <xref:Microsoft.VisualStudio.Package.IScanner> интерфейса путем переопределения <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> метод <xref:Microsoft.VisualStudio.Package.LanguageService> класса.  
  
 <xref:Microsoft.VisualStudio.Package.IScanner> Сканера является заданной строки исходного кода через <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> метод. Вызовы <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> метод повторяются для получения следующий токен в строке, пока не будет исчерпано строке маркеров. Для цветового выделения MPF обрабатывает весь исходный код, как последовательность строк. Таким образом сканер должен иметь возможность справиться с источником, поступающие на него как строки. Кроме того любую строку, которая может передаваться к сканеру в любое время и гарантируется только то, что сканер получает переменную состояния из строку перед строкой будет проверяться.  
  
 <xref:Microsoft.VisualStudio.Package.Colorizer> Класс также используется для определения маркера триггеров. Эти триггеры сообщить MPF, что данная лексема может инициировать более сложные операции, такие как завершение слов или парные фигурные скобки. Так как определение таких триггеров должен быть быстрым и должны происходить в любом расположении, сканер, лучше всего подходит для выполнения этой задачи.  
  
 Дополнительные сведения см. в разделе [цветовая маркировка синтаксиса в языковой службе прежних версий](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).  
  
## <a name="parsing-for-functionality-and-scope"></a>Синтаксический анализ для функций и области  
 Синтаксический анализ для функциональные возможности и область требует больших усилий, чем просто определение типов маркеров, которые стали известны. Средство синтаксического анализа должен определить не только тип маркера, но функциональные возможности, для которого используется маркер. Например идентификатор-это просто имя, но на языке, идентификатор может быть имя класса, пространства имен, метода или переменной, в зависимости от контекста. Общий тип маркера может быть идентификатором, но идентификатор может также иметь другие значения, в зависимости от того, что это такое и где он определен. Этот код требуется средство синтаксического анализа, чтобы более обширные знания языка, который анализируется. Именно здесь <xref:Microsoft.VisualStudio.Package.AuthoringSink> пригодиться класс. <xref:Microsoft.VisualStudio.Package.AuthoringSink> Класс собирает сведения о идентификаторы, методы, соответствующие языковые пары (например, фигурные скобки и круглые скобки) и язык триад (аналогичен языковых пар, за исключением того, что состоит из трех частей, например, "`foreach()`" "`{`«и»`}`«). Кроме того, можно переопределить <xref:Microsoft.VisualStudio.Package.AuthoringSink> класс для поддержки идентификационный код, используемый в начале проверки точек останова, отладчик не имеет для загрузки, и **"Видимые"** отладки окно, в котором показаны локальные переменные и параметры автоматически Если программа отлаживается; требуется средство синтаксического анализа для определения соответствующих локальных переменных и параметров, помимо тех, которые отладчик предоставляет.  
  
 <xref:Microsoft.VisualStudio.Package.AuthoringSink> Объект передается в средство синтаксического анализа как часть <xref:Microsoft.VisualStudio.Package.ParseRequest> объекта, а новые <xref:Microsoft.VisualStudio.Package.AuthoringSink> объект создается при каждом запуске, новый <xref:Microsoft.VisualStudio.Package.ParseRequest> создается объект. Кроме того <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод должен возвращать <xref:Microsoft.VisualStudio.Package.AuthoringScope> объект, который используется для обработки различных операций IntelliSense. <xref:Microsoft.VisualStudio.Package.AuthoringScope> Поддерживает список для объявлений и список для методов, либо из которых заполняется, в зависимости от причины для синтаксического анализа. <xref:Microsoft.VisualStudio.Package.AuthoringScope> Класс должен быть реализован.  
  
## <a name="see-also"></a>См. также  
 [Реализация языковой службы прежних версий](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [Общие сведения о службе устаревшего языка](../../extensibility/internals/legacy-language-service-overview.md)   
 [Цветовая маркировка синтаксиса в языковой службе прежних версий](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)   
 [Парные фигурные скобки в языковой службе прежних версий](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)
