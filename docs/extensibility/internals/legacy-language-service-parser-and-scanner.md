---
title: Анализатор и сканер языковой службы прежних версий | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- parsers, language services [managed package framework]
- language services [managed package framework], Parsers
ms.assetid: 1ac3de27-a23b-438d-9593-389e45839cfa
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11b172fee8f6f5cf1c80d306a8a8b154f7316bf8
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726735"
---
# <a name="legacy-language-service-parser-and-scanner"></a>Средство синтаксического анализа и сканер языковой службы прежних версий
Средство синтаксического анализа является основой языковой службы. Для классов языка Managed Package Framework (MPF) требуется средство синтаксического анализа языка, чтобы выбрать сведения о отображаемом коде. Средство синтаксического анализа разделяет текст на лексические токены, а затем определяет эти токены по типу и функциональности.

## <a name="discussion"></a>Обсуждение
 Ниже приведен C# метод.

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

 В этом примере токены являются словами и знаками препинания. Ниже приведены типы токенов.

|Имя токена|Тип маркера|
|----------------|----------------|
|пространство имен, класс, Public, void, int|ключевое-слово|
|=|оператор|
|{ } ( ) ;|Разделитель|
|MyNamespace, MyClass, MyFunction, arg1, var1|идентификатор|
|MyNamespace|namespace|
|MyClass|класс|
|MyFunction|method|
|arg1|параметр|
|var1|Локальная переменная|

 Роль средства синтаксического анализа заключается в определении токенов. Некоторые токены могут иметь более одного типа. После того как анализатор определил маркеры, языковая служба может использовать эти сведения для предоставления полезных функций, таких как выделение синтаксиса, сопоставление фигурных скобок и операции IntelliSense.

## <a name="types-of-parsers"></a>Типы средств синтаксического анализа
 Средство синтаксического анализа языковой службы отличается от синтаксического анализатора, используемого в составе компилятора. Однако этот тип синтаксического анализатора должен использовать как сканер, так и средство синтаксического анализа так же, как средство синтаксического анализа компилятора.

- Для обнаружения типов токенов используется сканер. Эти сведения используются для выделения синтаксиса и для быстрого определения типов токенов, которые могут активировать другие операции, например, сопоставление фигурных скобок. Этот сканер представлен интерфейсом <xref:Microsoft.VisualStudio.Package.IScanner>.

- Средство синтаксического анализа используется для описания функций и области токенов. Эти сведения используются в операциях IntelliSense для определения элементов языка, таких как методы, переменные, параметры и объявления, а также для предоставления списков членов и подписей методов на основе контекста. Этот синтаксический анализатор также используется для поиска соответствующих пар языковых элементов, таких как фигурные скобки и круглые скобки. Доступ к этому анализатору осуществляется с помощью метода <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> в классе <xref:Microsoft.VisualStudio.Package.LanguageService>.

  Способ реализации сканера и средства синтаксического анализа для языковой службы не отличается от вас. Доступно несколько ресурсов, описывающих работу средств синтаксического анализа и написание собственного средства синтаксического анализа. Кроме того, доступны несколько бесплатных и коммерческих продуктов, помогающих в создании средства синтаксического анализа.

### <a name="the-parsesource-parser"></a>Средство синтаксического анализа Парсесаурце
 В отличие от анализатора, используемого в составе компилятора (в котором маркеры преобразуются в некоторый формат исполняемого кода), средство синтаксического анализа языковой службы может вызываться по различным причинам и в различных контекстах. Способ реализации этого подхода в методе <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> класса <xref:Microsoft.VisualStudio.Package.LanguageService>. Важно помнить, что метод <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> может быть вызван в фоновом потоке.

> [!CAUTION]
> Структура <xref:Microsoft.VisualStudio.Package.ParseRequest> содержит ссылку на объект <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>. Этот объект <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> нельзя использовать в фоновом потоке. На самом деле многие базовые классы MPF не могут использоваться в фоновом потоке. К ним относятся <xref:Microsoft.VisualStudio.Package.Source>, <xref:Microsoft.VisualStudio.Package.ViewFilter>, <xref:Microsoft.VisualStudio.Package.CodeWindowManager> классы и любой другой класс, который напрямую или косвенно взаимодействует с представлением.

 Этот синтаксический анализатор обычно выполняет синтаксический анализ всего исходного файла при первом его вызове или при задании значения причины синтаксического анализа <xref:Microsoft.VisualStudio.Package.ParseReason>. Последующие вызовы метода <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> обрабатывают небольшую часть проанализированного кода и могут выполняться гораздо быстрее, используя результаты предыдущей операции полного синтаксического анализа. Метод <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> передает результаты операции синтаксического анализа через объекты <xref:Microsoft.VisualStudio.Package.AuthoringSink> и <xref:Microsoft.VisualStudio.Package.AuthoringScope>. Объект <xref:Microsoft.VisualStudio.Package.AuthoringSink> используется для получения сведений о конкретной причине синтаксического анализа, например сведения о диапазонах соответствующих скобок или сигнатурах методов, имеющих списки параметров. @No__t_0 предоставляет коллекции объявлений и сигнатур методов, а также поддержку параметра переход к расширенному редактированию (**Переход к определению**, **Переход к объявлению**, **Переход по ссылке**).

### <a name="the-iscanner-scanner"></a>Сканер средства проверки
 Необходимо также реализовать сканер, реализующий <xref:Microsoft.VisualStudio.Package.IScanner>. Однако, поскольку этот сканер работает построчно с помощью класса <xref:Microsoft.VisualStudio.Package.Colorizer>, обычно проще реализовать. В начале каждой строки MPF предоставляет <xref:Microsoft.VisualStudio.Package.Colorizer> классу значение, используемое в качестве переменной состояния, которая передается сканеру. В конце каждой строки сканер возвращает обновленную переменную состояния. MPF кэширует эти сведения о состоянии для каждой строки, чтобы средство проверки может начать анализ из любой строки без необходимости запуска в начале исходного файла. Это быстрое сканирование одной строки позволяет редактору обеспечить быструю обратную связь с пользователем.

## <a name="parsing-for-matching-braces"></a>Синтаксический анализ парных скобок
 В этом примере показан поток управления для сопоставления закрывающей фигурной скобки, которую пользователь ввел. В этом процессе средство проверки, используемое для выделения цветом, также используется для определения типа маркера и того, может ли маркер активировать операцию сопоставления с фигурными скобками. Если триггер найден, вызывается метод <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> для поиска парной скобки. Наконец, две фигурные скобки выделены.

 Несмотря на то, что скобки используются в именах триггеров и из соображений синтаксического анализа, этот процесс не ограничивается фактическими фигурными скобками. Поддерживается любая пара символов, которая указана как соответствующая пара. Примеры: (и), \< и >, а [и].

 Предположим, что языковая служба поддерживает Парные фигурные скобки.

1. Пользователь вводит закрывающую фигурную скобку (}).

2. Фигурная скобка вставляется в курсор в исходном файле, а курсор — на один.

3. Метод <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> в классе <xref:Microsoft.VisualStudio.Package.Source> вызывается с типизированной закрывающей фигурной скобкой.

4. Метод <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> вызывает метод <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> в классе <xref:Microsoft.VisualStudio.Package.Source>, чтобы получить маркер в позиции непосредственно перед текущим положением курсора. Этот маркер соответствует типизированной закрывающей фигурной скобке.

    1. Метод <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> вызывает метод <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> для объекта <xref:Microsoft.VisualStudio.Package.Colorizer>, чтобы получить все токены в текущей строке.

    2. Метод <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> вызывает метод <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> для объекта <xref:Microsoft.VisualStudio.Package.IScanner> с текстом текущей строки.

    3. Метод <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> многократно вызывает метод <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> для объекта <xref:Microsoft.VisualStudio.Package.IScanner>, чтобы собрать все токены из текущей строки.

    4. Метод <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> вызывает закрытый метод в классе <xref:Microsoft.VisualStudio.Package.Source> для получения токена, содержащего нужную точку, и передает в список токенов, полученных из метода <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A>.

5. Метод <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> ищет флаг триггера маркера <xref:Microsoft.VisualStudio.Package.TokenTriggers> в токене, возвращаемом методом <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A>; то есть маркер, представляющий закрывающую фигурную скобку.

6. Если обнаружен флаг триггера <xref:Microsoft.VisualStudio.Package.TokenTriggers>, вызывается метод <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> в классе <xref:Microsoft.VisualStudio.Package.Source>.

7. Метод <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> запускает операцию синтаксического анализа со значением причины синтаксического анализа <xref:Microsoft.VisualStudio.Package.ParseReason>. Эта операция в конечном итоге вызывает метод <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> для класса <xref:Microsoft.VisualStudio.Package.LanguageService>. Если асинхронный анализ включен, этот вызов метода <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> происходит в фоновом потоке.

8. По завершении операции синтаксического анализа внутренний обработчик завершения (также известный как метод обратного вызова) с именем `HandleMatchBracesResponse` вызывается в классе <xref:Microsoft.VisualStudio.Package.Source>. Этот вызов выполняется автоматически <xref:Microsoft.VisualStudio.Package.LanguageService> базовым классом, а не синтаксическим анализатором.

9. Метод `HandleMatchBracesResponse` получает список диапазонов от объекта <xref:Microsoft.VisualStudio.Package.AuthoringSink>, хранящегося в объекте <xref:Microsoft.VisualStudio.Package.ParseRequest>. (Диапазон — это <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> структура, указывающая диапазон строк и символов в исходном файле.) Этот список диапазонов обычно содержит два диапазона: по одному для открывающих и закрывающих фигурных скобок.

10. Метод `HandleBracesResponse` вызывает метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> для объекта <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>, который хранится в объекте <xref:Microsoft.VisualStudio.Package.ParseRequest>. Это выделяет заданные диапазоны.

11. Если <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> свойство <xref:Microsoft.VisualStudio.Package.LanguagePreferences> включено, метод `HandleBracesResponse` получает текст, который включается в соответствующий диапазон, и отображает первые 80 символов этого интервала в строке состояния. Это лучше, если метод <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> включает элемент Language, сопровождающий соответствующую пару. Дополнительные сведения см. в описании свойства <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>.

12. Договорились.

### <a name="summary"></a>Сводка
 Парная операция скобок обычно ограничена простыми парами языковых элементов. Более сложные элементы, такие как парные триадные ("`if(...)`", "`{`" и "`}`", или "`else`", "`{`" и "`}`"), могут быть выделены в рамках операции завершения слова. Например, при завершении слова «else» соответствующая инструкция «`if`» может быть выделена. Если существовал ряд `if` / `else if`, все они могут быть выделены с помощью того же механизма, что и парные скобки. Базовый класс <xref:Microsoft.VisualStudio.Package.Source> уже поддерживает это, как показано ниже. сканер должен возвращать значение триггера маркера <xref:Microsoft.VisualStudio.Package.TokenTriggers> в сочетании со значением триггера <xref:Microsoft.VisualStudio.Package.TokenTriggers> для токена, который предшествует позиции курсора.

 Дополнительные сведения см. [в разделе Сопоставление фигурных скобок в языковой службе прежних версий](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).

## <a name="parsing-for-colorization"></a>Синтаксический анализ для выделения цветом
 Выкрасить исходный код несложно, просто укажите тип маркера и возвращаемые сведения о цвете для этого типа. Класс <xref:Microsoft.VisualStudio.Package.Colorizer> выступает в качестве посредника между редактором и средством проверки, чтобы предоставить сведения о цвете для каждого маркера. Класс <xref:Microsoft.VisualStudio.Package.Colorizer> использует объект <xref:Microsoft.VisualStudio.Package.IScanner> для выделения цветом линии, а также для сбора сведений о состоянии для всех строк в исходном файле. В классах языковой службы MPF класс <xref:Microsoft.VisualStudio.Package.Colorizer> не требуется переопределять, так как он взаимодействует с сканером только через интерфейс <xref:Microsoft.VisualStudio.Package.IScanner>. Вы предоставляете объект, реализующий интерфейс <xref:Microsoft.VisualStudio.Package.IScanner>, переопределяя метод <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> в классе <xref:Microsoft.VisualStudio.Package.LanguageService>.

 Сканер <xref:Microsoft.VisualStudio.Package.IScanner> получает строку исходного кода с помощью метода <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A>. Вызовы метода <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> повторяются для получения следующего токена в строке, пока строка не будет исчерпана токенов. Для выделения цветом MPF обрабатывает весь исходный код как последовательность строк. Таким образом, сканер должен иметь возможность работать с источником, находящимся в виде линий. Кроме того, любая строка может быть передана сканеру в любое время, и единственной гарантией является то, что сканер получает переменную состояния из строки до того, как строка будет просканирована.

 Класс <xref:Microsoft.VisualStudio.Package.Colorizer> также используется для обнаружения триггеров маркеров. Эти триггеры сообщают MPF, что конкретный маркер может инициировать более сложную операцию, например завершение слов или Парные фигурные скобки. Так как определение таких триггеров должно выполняться быстро и должно происходить в любом месте, сканер лучше всего подходит для этой задачи.

 Дополнительные сведения см. [в разделе тонирование синтаксиса в языковой службе прежних версий](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).

## <a name="parsing-for-functionality-and-scope"></a>Синтаксический анализ функциональности и области
 Синтаксический анализ функциональности и области требует больше усилий, чем просто определение типов обнаруженных маркеров. Синтаксический анализатор должен вычислить не только тип токена, но и функциональные возможности, для которых используется маркер. Например, идентификатор — это просто имя, но на вашем языке идентификатор может быть именем класса, пространства имен, метода или переменной в зависимости от контекста. Общий тип токена может быть идентификатором, но идентификатор также может иметь другие значения, в зависимости от того, что это такое и где оно определено. Эта идентификация требует, чтобы средство синтаксического анализа имело более широкие знания о языке, который анализируется. Именно здесь поступает класс <xref:Microsoft.VisualStudio.Package.AuthoringSink>. Класс <xref:Microsoft.VisualStudio.Package.AuthoringSink> собирает сведения об идентификаторах, методах, соответствующих парах языков (например, фигурных скобках и круглых скобках) и тройных языках (аналогично парам языков, за исключением того, что есть три части, например "`foreach()`" "`{`" и "`}`"). . Кроме того, можно переопределить <xref:Microsoft.VisualStudio.Package.AuthoringSink> класс для поддержки идентификации кода, который используется в ранних проверках точек останова, чтобы отладчик не загружался, и окно " **видимая** Отладка", которое показывает локальные переменные и параметры. автоматически при отладке программы и требует, чтобы средство синтаксического анализа определяло соответствующие локальные переменные и параметры в дополнение к тем, которые представляет отладчик.

 Объект <xref:Microsoft.VisualStudio.Package.AuthoringSink> передается средству синтаксического анализа как часть объекта <xref:Microsoft.VisualStudio.Package.ParseRequest>, а новый объект <xref:Microsoft.VisualStudio.Package.AuthoringSink> создается каждый раз при создании нового объекта <xref:Microsoft.VisualStudio.Package.ParseRequest>. Кроме того, метод <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> должен возвращать объект <xref:Microsoft.VisualStudio.Package.AuthoringScope>, который используется для работы с различными операциями IntelliSense. Объект <xref:Microsoft.VisualStudio.Package.AuthoringScope> поддерживает список для объявлений и список методов, каждый из которых заполняется в зависимости от причины синтаксического анализа. Класс <xref:Microsoft.VisualStudio.Package.AuthoringScope> должен быть реализован.

## <a name="see-also"></a>См. также
- [Реализация языковой службы прежних версий](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [Обзор языковой службы прежних версий](../../extensibility/internals/legacy-language-service-overview.md)
- [Цветовая маркировка синтаксиса в языковой службе прежних версий](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)
- [Парные фигурные скобки в языковой службе прежних версий](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)