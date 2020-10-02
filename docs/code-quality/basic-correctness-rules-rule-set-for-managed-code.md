---
title: Набор правил "Базовые правила определения правильности" для управляемого кода
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 631f0daf-1d42-4c90-a7dc-1a6a9de64c93
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: eef90c024c03c0a8346fda6b90225dd0ebf3ee51
ms.sourcegitcommit: c025a5e2013c4955ca685092b13e887ce64aaf64
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2020
ms.locfileid: "91659144"
---
# <a name="basic-correctness-rules-rule-set-for-managed-code"></a>Набор правил "Базовые правила определения правильности" для управляемого кода

Набор правил "основные правила корректности" предназначен для логических ошибок и распространенных ошибок при использовании API-интерфейсов платформы. Основные правила корректности включают правила из набора правил " [управляемые Рекомендуемые правила](managed-recommended-rules-rule-set-for-managed-code.md) ".

В следующей таблице описаны все правила в наборе правил правил исправления Microsoft Basic.

|Правило|Описание|
|----------|-----------------|
|[CA1001](/dotnet/fundamentals/code-analysis/quality-rules/ca1001)|Типы, которым принадлежат освобождаемые поля, должны быть освобождаемыми|
|[CA1009](../code-quality/ca1009.md)|Правильно объявляйте обработчики событий|
|[CA1016](/dotnet/fundamentals/code-analysis/quality-rules/ca1016)|Пометьте сборки с помощью AssemblyVersionAttribute|
|[CA1033](/dotnet/fundamentals/code-analysis/quality-rules/ca1033)|Методы интерфейса должны быть доступны для вызова дочерними типами|
|[CA1049](../code-quality/ca1049.md)|Типы, которым принадлежат собственные ресурсы, должны быть освобождаемыми|
|[CA1060](/dotnet/fundamentals/code-analysis/quality-rules/ca1060)|Переместите методы P/Invoke в класс NativeMethods|
|[CA1061](/dotnet/fundamentals/code-analysis/quality-rules/ca1061)|Не скрывайте методы базовых классов|
|[CA1063](/dotnet/fundamentals/code-analysis/quality-rules/ca1063)|Правильно реализуйте IDisposable|
|[CA1065](/dotnet/fundamentals/code-analysis/quality-rules/ca1065)|Не вызывайте исключения в непредвиденных местах|
|[CA1301](../code-quality/ca1301.md)|Избегайте повторяющихся акселераторов|
|[CA1400](../code-quality/ca1400.md)|Для методов P/Invoke должны существовать точки входа|
|[CA1401](/dotnet/fundamentals/code-analysis/quality-rules/ca1401)|Методы P/Invoke не должны быть видимыми|
|[CA1403](../code-quality/ca1403.md)|Типы с автомакетом не должны быть видимыми для COM|
|[CA1404](../code-quality/ca1404.md)|Вызывайте GetLastError сразу после P/Invoke|
|[CA1405](../code-quality/ca1405.md)|Базовые типы, относящиеся к типу, видимому для COM, должны быть видимыми для COM|
|[CA1410](../code-quality/ca1410.md)|Методы регистрации COM должны быть согласованными|
|[CA1415](../code-quality/ca1415.md)|Правильно объявляйте методы P/Invoke|
|[CA1821](/dotnet/fundamentals/code-analysis/quality-rules/ca1821)|Удалите пустые методы завершения|
|[CA1900](../code-quality/ca1900.md)|Поля типов значений должны быть переносимыми|
|[CA1901](../code-quality/ca1901.md)|Объявления P/Invoke должны быть переносимыми|
|[CA2002](/dotnet/fundamentals/code-analysis/quality-rules/ca2002)|Не блокируйте объекты с ненадежными удостоверениями|
|[CA2100](/dotnet/fundamentals/code-analysis/quality-rules/ca2100)|Проверьте запросы SQL на наличие уязвимостей системы безопасности|
|[CA2101](/dotnet/fundamentals/code-analysis/quality-rules/ca2101)|Укажите тип маршалинга для строковых аргументов P/Invoke|
|[CA2108](../code-quality/ca2108.md)|Проверьте объявляемые параметры безопасности типов значений|
|[CA2111](../code-quality/ca2111.md)|Указатели не должны быть видимыми|
|[CA2112](../code-quality/ca2112.md)|Защищенные типы не должны предоставлять поля|
|[CA2114](../code-quality/ca2114.md)|Безопасность метода должна быть надмножеством типа|
|[CA2116](../code-quality/ca2116.md)|APTCA-методы должны вызывать только APTCA-методы|
|[CA2117](../code-quality/ca2117.md)|APTCA-типы должны расширять только базовые APTCA-типы|
|[CA2122](../code-quality/ca2122.md)|Не используйте косвенное представление методов с требованиями ссылки|
|[CA2123](../code-quality/ca2123.md)|Переопределяющие требования ссылки должны быть идентичны базовым|
|[CA2124](../code-quality/ca2124.md)|Ограничьте уязвимые предложения finally во внешних блоках try|
|[CA2126](../code-quality/ca2126.md)|Для требований ссылок на тип необходимы требования наследования|
|[CA2131](../code-quality/ca2131.md)|Критические для безопасности типы не могут участвовать в эквивалентности типов|
|[CA2132](../code-quality/ca2132.md)|Конструкторы по умолчанию должны быть по меньшей мере такими же критическими, как конструкторы по умолчанию базового типа|
|[CA2133](../code-quality/ca2133.md)|Делегаты должны быть привязаны к методам с соответствующей прозрачностью|
|[CA2134](../code-quality/ca2134.md)|Методы должны сохранять одинаковую прозрачность при переопределении базовых методов|
|[CA2137](../code-quality/ca2137.md)|Прозрачные методы должны содержать только поддающийся проверке промежуточный язык|
|[CA2138](../code-quality/ca2138.md)|Прозрачные методы не должны вызывать методы с атрибутом SuppressUnmanagedCodeSecurity|
|[CA2140](../code-quality/ca2140.md)|Прозрачный код не должен ссылаться на критические для безопасности элементы|
|[CA2141](../code-quality/ca2141.md)|Прозрачные методы не должны соответствовать требованиям LinkDemand|
|[CA2146](../code-quality/ca2146.md)|Типы должны быть по крайней мере настолько же критическими, как их базовые типы и интерфейсы|
|[CA2147](../code-quality/ca2147.md)|Прозрачные методы могут не использовать утверждения безопасности|
|[CA2149](../code-quality/ca2149.md)|Прозрачные методы не должны вызывать машинный код|
|[CA2200](/dotnet/fundamentals/code-analysis/quality-rules/ca2200)|Повторно порождайте исключения для сохранения сведений стека|
|[CA2202](../code-quality/ca2202.md)|Не ликвидируйте объекты несколько раз|
|[CA2207](/dotnet/fundamentals/code-analysis/quality-rules/ca2207)|Используйте встроенную инициализацию статических полей типов значений|
|[CA2212](../code-quality/ca2212.md)|Не помечайте обслуживаемые компоненты с помощью WebMethod|
|[CA2213](/dotnet/fundamentals/code-analysis/quality-rules/ca2213)|Следует высвобождать высвобождаемые поля|
|[CA2214](/dotnet/fundamentals/code-analysis/quality-rules/ca2214)|Не вызывайте переопределяемые методы в конструкторах|
|[CA2216](/dotnet/fundamentals/code-analysis/quality-rules/ca2216)|Высвобождаемые типы должны объявлять методы завершения|
|[CA2220](../code-quality/ca2220.md)|Методы завершения должны вызывать метод завершения базового класса|
|[CA2229](/dotnet/fundamentals/code-analysis/quality-rules/ca2229)|Реализуйте конструкторы сериализации|
|[CA2231](/dotnet/fundamentals/code-analysis/quality-rules/ca2231)|Перегрузите оператор равенства на переопределяющем типе ValueType.Equals|
|[CA2232](../code-quality/ca2232.md)|Отметьте точки входа Windows Forms меткой STAThread|
|[CA2235](/dotnet/fundamentals/code-analysis/quality-rules/ca2235)|Пометьте все несериализуемые поля|
|[CA2236](../code-quality/ca2236.md)|Вызывайте методы базового класса для типов ISerializable|
|[CA2237](/dotnet/fundamentals/code-analysis/quality-rules/ca2237)|Пометьте типы ISerializable атрибутом SerializableAttribute|
|[CA2238](../code-quality/ca2238.md)|Правильно реализуйте методы сериализации|
|[CA2240](../code-quality/ca2240.md)|Правильно реализуйте ISerializable|
|[CA2241](/dotnet/fundamentals/code-analysis/quality-rules/ca2241)|Задайте правильные аргументы для методов форматирования|
|[CA2242](/dotnet/fundamentals/code-analysis/quality-rules/ca2242)|Правильно выполняйте проверку NaN|
|[CA1008](/dotnet/fundamentals/code-analysis/quality-rules/ca1008)|Перечисляемые типы должны иметь нулевое значение|
|[CA1013](../code-quality/ca1013.md)|Перегружайте оператор равенства при перегрузке операторов сложения и вычитания|
|[CA1303](/dotnet/fundamentals/code-analysis/quality-rules/ca1303)|Не передавайте литералы в качестве локализованных параметров|
|[CA1308](/dotnet/fundamentals/code-analysis/quality-rules/ca1308)|Нормализуйте строки в верхний регистр|
|[CA1806](/dotnet/fundamentals/code-analysis/quality-rules/ca1806)|Не игнорируйте результаты метода|
|[CA1816](/dotnet/fundamentals/code-analysis/quality-rules/ca1816)|Вызов GC.SuppressFinalize должен осуществляться правильно|
|[CA1819](/dotnet/fundamentals/code-analysis/quality-rules/ca1819)|Свойства не должны возвращать массивы|
|[CA1820](/dotnet/fundamentals/code-analysis/quality-rules/ca1820)|Проверяйте наличие пустых строк, используя длину строки|
|[CA1903](../code-quality/ca1903.md)|Используйте API только из целевой рабочей среды|
|[CA2004](../code-quality/ca2004.md)|Удалите вызовы GC.KeepAlive|
|[CA2006](../code-quality/ca2006.md)|Используйте SafeHandle для инкапсуляции собственных ресурсов|
|[CA2102](../code-quality/ca2102.md)|Перехватывайте исключения, не являющиеся CLSCompliant, с помощью общих обработчиков|
|[CA2104](../code-quality/ca2104.md)|Не объявляйте изменяющиеся ссылочные типы только для чтения|
|[CA2105](../code-quality/ca2105.md)|Поля массивов не должны быть доступны только для чтения|
|[CA2106](../code-quality/ca2106.md)|Обеспечьте безопасность утверждений|
|[CA2115](../code-quality/ca2115.md)|Вызывайте GC.KeepAlive при использовании собственных ресурсов|
|[CA2119](/dotnet/fundamentals/code-analysis/quality-rules/ca2119)|Запечатайте методы, соответствующие частным интерфейсам|
|[CA2120](../code-quality/ca2120.md)|Обеспечьте безопасность конструкторов сериализации|
|[CA2121](../code-quality/ca2121.md)|Статические конструкторы должны быть частными|
|[CA2130](../code-quality/ca2130.md)|Важные константы безопасности должны быть прозрачными|
|[CA2205](../code-quality/ca2205.md)|Используйте управляемые эквиваленты Win32 API|
|[CA2215](/dotnet/fundamentals/code-analysis/quality-rules/ca2215)|Метод Dispose должен вызывать базовый класс Dispose|
|[CA2221](../code-quality/ca2221.md)|Методы завершения должны быть защищенными|
|[CA2222](../code-quality/ca2222.md)|Не уменьшайте видимость наследуемого члена|
|[CA2223](../code-quality/ca2223.md)|Члены должны различаться не только возвращаемым типом|
|[CA2224](../code-quality/ca2224.md)|Переопределяйте Equals при перегрузке оператора равенства|
|[CA2226](/dotnet/fundamentals/code-analysis/quality-rules/ca2226)|Перегрузки операторов должны быть симметричными|
|[CA2227](/dotnet/fundamentals/code-analysis/quality-rules/ca2227)|Свойства, возвращающие коллекции, должны быть доступными только для чтения|
|[CA2239](../code-quality/ca2239.md)|Обеспечьте наличие методов десериализации в необязательных полях|
