---
title: Наследие Языковая служба Parser и сканер (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- parsers, language services [managed package framework]
- language services [managed package framework], Parsers
ms.assetid: 1ac3de27-a23b-438d-9593-389e45839cfa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c87f447a4b8bca804d27aae4967f4adaf389c627
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707318"
---
# <a name="legacy-language-service-parser-and-scanner"></a>Средство синтаксического анализа и сканер языковой службы прежних версий
Парсер является сердцем языковой службы. Языковые классы управляемых пакетов (MPF) требуют языкового парсера для выбора информации о отображаемом коде. Парсер разделяет текст на лексические токены, а затем идентифицирует эти маркеры по типу и функциональности.

## <a name="discussion"></a>Обсуждение
 Ниже приводится метод C-центра.

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

 В этом примере маркеры являются словами и знаками препинания. Виды токенов являются следующими.

|Имя токена|Тип маркера|
|----------------|----------------|
|пространство имен, класс, общественный, пустоты, Int|ключевое слово|
|=|оператор|
|{ } ( ) ;|разделитель|
|MyNamespace, MyClass, MyFunction, arg1, var1|идентификатор|
|MyNamespace|namespace|
|MyClass|class|
|MyFunction|method|
|arg1|параметр|
|var1|локальная переменная|

 Роль парсера заключается в идентификации токенов. Некоторые маркеры могут иметь более одного типа. После того, как парсер идентифицировал токены, языковая служба может использовать эту информацию для предоставления полезных функций, таких как выделение синтаксиса, соответствие скобки и операции IntelliSense.

## <a name="types-of-parsers"></a>Типы парзеров
 Языковой парсер службы не такой же, как парсер, используемый в качестве составного компилятора. Тем не менее, этот вид парсера необходимо использовать как сканер и парсер, так же, как пилайзер пилсера.

- Сканер используется для идентификации типов токенов. Эти данные используется для выделения синтаксиса и для быстрого определения типов токенов, способных вызывать другие операции, например, проверку соответствия фигурных скобок. Этот сканер представлен интерфейсом. <xref:Microsoft.VisualStudio.Package.IScanner>

- Для описания функций и сферы действия токенов используется парсер. Эта информация используется в операциях IntelliSense для определения языковых элементов, таких как методы, переменные, параметры и декларации, а также для предоставления списков членов и подписей метода на основе контекста. Этот парсер также используется для определения местом расположения соответствующих пар элементов языка, таких как скобки и скобки. Этот парсер доступен <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> через метод <xref:Microsoft.VisualStudio.Package.LanguageService> в классе.

  Способ реализации сканера и парсера для языкового сервиса за вами. Доступно несколько ресурсов, которые описывают, как работают парсеры и как написать свой собственный парзер. Кроме того, несколько бесплатных и коммерческих продуктов доступны, которые помогают в создании парсера.

### <a name="the-parsesource-parser"></a>The ParseSource Parser
 В отличие от парзера, который используется как часть компилятора (где токены преобразуются в ту или иную форму исполняемого кода), языковой парсер может быть вызван по разным причинам и во многих различных контекстах. Способ реализации этого <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> подхода в <xref:Microsoft.VisualStudio.Package.LanguageService> методе в классе до вас. Важно иметь в виду, <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> что метод может быть вызван на фоновом потоке.

> [!CAUTION]
> Структура <xref:Microsoft.VisualStudio.Package.ParseRequest> содержит ссылку <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> на объект. Этот <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> объект не может быть использован в фоновом потоке. На самом деле, многие базовые классы MPF не могут быть использованы в фоновом потоке. К ним <xref:Microsoft.VisualStudio.Package.Source> <xref:Microsoft.VisualStudio.Package.ViewFilter>относятся, классы, <xref:Microsoft.VisualStudio.Package.CodeWindowManager> и любой другой класс, который прямо или косвенно общается с представлением.

 Этот парсер обычно разбирает весь исходный файл при первом вызове или <xref:Microsoft.VisualStudio.Package.ParseReason> при приведении значения причины. Последующие вызовы к методу <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> обрабатывают небольшую часть разобрана кода и могут быть выполнены гораздо быстрее, используя результаты предыдущей операции полного разбора. Метод <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> передает результаты операции разбора через <xref:Microsoft.VisualStudio.Package.AuthoringSink> объекты и <xref:Microsoft.VisualStudio.Package.AuthoringScope> объекты. Объект <xref:Microsoft.VisualStudio.Package.AuthoringSink> используется для сбора информации для определенной причины разбора, например, информации о диапазонах соответствующих сепаржей или сигнатур метода, которые имеют списки параметров. Предоставляет <xref:Microsoft.VisualStudio.Package.AuthoringScope> коллекции деклараций и метод подписей, а также поддержку Перейти к расширенной вариант edit (**Перейти к определению**, **перейдите к декларации**, **Перейти к ссылке**).

### <a name="the-iscanner-scanner"></a>Сканер IScanner
 Вы также должны реализовать сканер, который <xref:Microsoft.VisualStudio.Package.IScanner>реализует. Однако, поскольку этот сканер работает по очереди <xref:Microsoft.VisualStudio.Package.Colorizer> через класс, его, как правило, легче реализовать. В начале каждой строки MPF придает <xref:Microsoft.VisualStudio.Package.Colorizer> классу значение для использования в качестве переменной состояния, которая передается сканеру. В конце каждой строки сканер возвращает обновленную переменную состояния. MPF кэширует эту информацию о состоянии для каждой строки, так что сканер может начать разбор с любой строки без необходимости запуска в начале исходного файла. Это быстрое сканирование одной строки позволяет редактору обеспечить быструю обратную связь с пользователем.

## <a name="parsing-for-matching-braces"></a>Разбор для соответствия скобки
 Этот пример показывает поток управления для сопоставления закрывающей скобки, которую пользователь набрал. В этом процессе сканер, используемый для окраски, также используется для определения типа токена и того, может ли токен вызвать операцию спирел-брекет. Если триггер найден, <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод вызывается, чтобы найти соответствующую скобку. Наконец, две скобки выделены.

 Несмотря на то, что скобки используются в названиях триггеров и разбор причин, этот процесс не ограничивается фактическими скобки. Поддерживается любая пара символов, которая указана как соответствующая пара. Примеры включают \< в себя ( и ), и >, и .

 Предположим, что языковая служба поддерживает соответствующие скобки.

1. Пользователь вводит закрывающий фигурную скобку (к).

2. Фигурная скобка вставляется в курсор в исходном файле, а курсор продвигается по одному.

3. Метод <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> в <xref:Microsoft.VisualStudio.Package.Source> классе вызывается с набранной закрывающей скобкой.

4. Метод <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> вызывает <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> метод в <xref:Microsoft.VisualStudio.Package.Source> классе, чтобы получить токен в позиции непосредственно перед текущим положением курсора. Этот маркер соответствует набранной закрывающей скобке).

    1. Метод <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> вызывает <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> метод на <xref:Microsoft.VisualStudio.Package.Colorizer> объекте, чтобы получить все токены на текущей строке.

    2. Метод <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> вызывает <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> метод на <xref:Microsoft.VisualStudio.Package.IScanner> объекте с текстом текущей строки.

    3. Метод <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> неоднократно вызывает <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> метод <xref:Microsoft.VisualStudio.Package.IScanner> на объекте, чтобы собрать все маркеры из текущей строки.

    4. Метод <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> вызывает частный метод <xref:Microsoft.VisualStudio.Package.Source> в классе для получения токена, содержащего желаемое положение, <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> и проходит в списке токенов, полученных из метода.

5. Метод <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> ищет маркертриггерный <xref:Microsoft.VisualStudio.Package.TokenTriggers> флаг на маркере, который возвращается из метода; <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> то есть токен, представляющий закрывающий сяк).

6. При обнаружении <xref:Microsoft.VisualStudio.Package.TokenTriggers> триггерного <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> флага <xref:Microsoft.VisualStudio.Package.Source> вызывается метод в классе.

7. Метод <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> начинает операцию разбора с значением причины разбора. <xref:Microsoft.VisualStudio.Package.ParseReason> Эта операция в <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> конечном <xref:Microsoft.VisualStudio.Package.LanguageService> счете вызывает метод на класс. Если включен асинхронный разбор, этот <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> вызов методу происходит на фоновом потоке.

8. Когда операция разбора закончена, в `HandleMatchBracesResponse` <xref:Microsoft.VisualStudio.Package.Source> классе вызывается внутренний обработчик завершения (также известный как метод обратного вызова). Этот вызов производится <xref:Microsoft.VisualStudio.Package.LanguageService> автоматически базовым классом, а не парсером.

9. Метод `HandleMatchBracesResponse` получает список пролетов <xref:Microsoft.VisualStudio.Package.AuthoringSink> от объекта, который <xref:Microsoft.VisualStudio.Package.ParseRequest> хранится в объекте. (Пролет — <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> это структура, которая определяет диапазон строк и символов в исходном файле.) Этот список диапазонов обычно содержит два диапазона, по одному для открытия и закрытия скобки.

10. Метод `HandleBracesResponse` вызывает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> метод на <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> объект, который <xref:Microsoft.VisualStudio.Package.ParseRequest> хранится в объекте. Это подчеркивает данные диапазоны.

11. Если <xref:Microsoft.VisualStudio.Package.LanguagePreferences> свойство <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> включено, `HandleBracesResponse` метод получает текст, который охватывается соответствующим диапазоном, и отображает первые 80 символов этого диапазона в панели статуса. Это работает лучше <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> всего, если метод включает в себя элемент языка, который сопровождает соответствующую пару. Дополнительные сведения см. в описании свойства <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>.

12. Готово.

### <a name="summary"></a>Сводка
 Операция соответствующих фигурных скобок обычно ограничивается простыми парами языковых элементов. Более сложные элементы, такие как`if(...)`сопоставление тройных`else`(",`{`"`}`"`{`и "`}`" или ", " и ", " и ""), могут быть выделены как часть слова завершения операции. Например, когда слово "else" закончено,`if`соответствующее "заявление может быть выделено. Если существует ряд `if` / `else if` утверждений, все они могут быть выделены с помощью того же механизма, что и соответствующие скобки. Базовый <xref:Microsoft.VisualStudio.Package.Source> класс уже поддерживает это следующим образом: сканер должен <xref:Microsoft.VisualStudio.Package.TokenTriggers> вернуть значение <xref:Microsoft.VisualStudio.Package.TokenTriggers> триггера в сочетании с значением триггера для маркера, которое находится перед положением курсора.

 Для получения дополнительной информации [см.](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)

## <a name="parsing-for-colorization"></a>Разбор для окраски
 Цветение исходного кода является простым, просто определить тип маркера и вернуть информацию о цвете этого типа. Класс <xref:Microsoft.VisualStudio.Package.Colorizer> выступает в качестве посредника между редактором и сканером, чтобы предоставить цветную информацию о каждом маркере. Класс <xref:Microsoft.VisualStudio.Package.Colorizer> использует <xref:Microsoft.VisualStudio.Package.IScanner> объект для окраски строки, а также для сбора информации о состоянии для всех строк в исходном файле. В классах языкового обслуживания <xref:Microsoft.VisualStudio.Package.Colorizer> MPF класс не должен быть переопределен, поскольку <xref:Microsoft.VisualStudio.Package.IScanner> он общается со сканером только через интерфейс. Вы поставляете объект, <xref:Microsoft.VisualStudio.Package.IScanner> который реализует интерфейс, переопределяя <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> метод в <xref:Microsoft.VisualStudio.Package.LanguageService> классе.

 Сканеру <xref:Microsoft.VisualStudio.Package.IScanner> предоставляется строка исходного <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> кода с помощью метода. Вызовы <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> к методу повторяются, чтобы получить следующий маркер в строке до тех пор, пока линия не будет исчерпана токенов. Для окрашивания MPF рассматривает весь исходный код как последовательность строк. Таким образом, сканер должен быть в состоянии справиться с источником, идущим на него в виде линий. Кроме того, любая линия может быть передана сканеру в любое время, и единственной гарантией является то, что сканер получает переменную состояния от линии до того, как линия будет отсканирована.

 Класс <xref:Microsoft.VisualStudio.Package.Colorizer> также используется для определения триггеров токенов. Эти триггеры говорят MPF, что определенный маркер может инициировать более сложную операцию, такую как завершение слов или соответствующие скобки. Поскольку идентификация таких триггеров должна быть быстрой и должна происходить в любом месте, сканер лучше всего подходит для этой задачи.

 Для получения дополнительной информации смотрите [Syntax Colorizing в службе языка Legacy.](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)

## <a name="parsing-for-functionality-and-scope"></a>Разбор функциональности и сферы действия
 Разбор функциональности и сферы охвата требует больших усилий, чем просто определение типов токенов, которые встречаются. Парсер должен определить не только тип токена, но и функциональность, для которой используется токен. Например, идентификатор — это просто имя, но в вашем языке идентификатором может быть имя класса, пространство имен, метод или переменная, в зависимости от контекста. Общий тип токена может быть идентификатором, но идентификатор может иметь и другие значения, в зависимости от того, что это такое и где он определен. Эта идентификация требует, чтобы парсер получил более обширные знания о языке, который разбирается. Вот где <xref:Microsoft.VisualStudio.Package.AuthoringSink> класс приходит дюйма Класс <xref:Microsoft.VisualStudio.Package.AuthoringSink> собирает информацию об идентификаторах, методах, соответствующих языковых парах (например, скобках и скобках) и языковых`foreach()`тройных (по аналогии с языковыми парами, за исключением трех частей, например, ««`{`«» и ««««»).`}` Кроме того, можно переопределить <xref:Microsoft.VisualStudio.Package.AuthoringSink> класс для поддержки идентификации кода, которая используется в ранней проверке точек разрыва, так что отладчик не должен быть загружен, и окно отладки **Autos,** которое показывает локальные переменные и параметры автоматически, когда программа отлажена и требует parser для соответствующего определения локальных переменных и параметров в дополнение к тем, которые представляет отладчик.

 Объект <xref:Microsoft.VisualStudio.Package.AuthoringSink> передается в парсер как <xref:Microsoft.VisualStudio.Package.ParseRequest> часть объекта, <xref:Microsoft.VisualStudio.Package.AuthoringSink> и новый объект создается каждый раз, когда создается новый <xref:Microsoft.VisualStudio.Package.ParseRequest> объект. Кроме того, <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод должен <xref:Microsoft.VisualStudio.Package.AuthoringScope> вернуть объект, который используется для обработки различных операций IntelliSense. Объект <xref:Microsoft.VisualStudio.Package.AuthoringScope> поддерживает список деклараций и список методов, любой из которых заселен, в зависимости от причины разбора. Класс <xref:Microsoft.VisualStudio.Package.AuthoringScope> должен быть реализован.

## <a name="see-also"></a>См. также
- [Реализация языковой службы прежних версий](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [Обзор языковой службы прежних версий](../../extensibility/internals/legacy-language-service-overview.md)
- [Цветовая маркировка синтаксиса в языковой службе прежних версий](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)
- [Парные фигурные скобки в языковой службе прежних версий](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)
