---
title: Набор правил "Базовые нормы и правила разработки" для управляемого кода
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 7eb384f5-f961-400b-b151-115d92addc6a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 2bf7542d94b16042df27ec8b780cc93c9061d6e8
ms.sourcegitcommit: c025a5e2013c4955ca685092b13e887ce64aaf64
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2020
ms.locfileid: "91659131"
---
# <a name="basic-design-guideline-rules-rule-set-for-managed-code"></a>Набор правил "Базовые нормы и правила разработки" для управляемого кода

Вы можете использовать набор правил по рекомендациям по проектированию Microsoft Basic, чтобы сосредоточиться на том, как упростить понимание и использование кода. Этот набор правил следует включать, если проект включает в себя код библиотеки или если вы хотите применить рекомендации для кода, который легко поддерживать.

Базовые правила разработки включают в себя все правила в наборе правил " [управляемые Рекомендуемые правила](managed-recommended-rules-rule-set-for-managed-code.md) ".

В следующей таблице описаны все правила набора правил "базовые правила для разработки Microsoft".

|Правило|Описание|
|----------|-----------------|
|[CA1000](/dotnet/fundamentals/code-analysis/quality-rules/ca1000)|Не объявляйте статические члены в универсальных типах|
|[CA1001](/dotnet/fundamentals/code-analysis/quality-rules/ca1001)|Типы, которым принадлежат освобождаемые поля, должны быть освобождаемыми|
|[CA1002](/dotnet/fundamentals/code-analysis/quality-rules/ca1002)|Не предоставляйте универсальные списки|
|[CA1003](/dotnet/fundamentals/code-analysis/quality-rules/ca1003)|Используйте экземпляры обработчика универсальных событий|
|[CA1004](../code-quality/ca1004.md)|Универсальные методы должны предоставлять параметр типа|
|[CA1005](/dotnet/fundamentals/code-analysis/quality-rules/ca1005)|Не используйте слишком много параметров в универсальных типах|
|[CA1006](../code-quality/ca1006.md)|Не создавайте вложенные универсальные типы в сигнатурах членов|
|[CA1007](../code-quality/ca1007.md)|По возможности используйте универсальные объекты|
|[CA1008](/dotnet/fundamentals/code-analysis/quality-rules/ca1008)|Перечисляемые типы должны иметь нулевое значение|
|[CA1009](../code-quality/ca1009.md)|Правильно объявляйте обработчики событий|
|[CA1010](/dotnet/fundamentals/code-analysis/quality-rules/ca1010)|Коллекции должны реализовать универсальный интерфейс|
|[CA1011](../code-quality/ca1011.md)|Попробуйте передать базовые типы в качестве параметров|
|[CA1012](/dotnet/fundamentals/code-analysis/quality-rules/ca1012)|Абстрактные типы не должны иметь конструкторы|
|[CA1013](../code-quality/ca1013.md)|Перегружайте оператор равенства при перегрузке операторов сложения и вычитания|
|[CA1014](/dotnet/fundamentals/code-analysis/quality-rules/ca1014)|Пометьте сборки с помощью CLSCompliantAttribute|
|[CA1016](/dotnet/fundamentals/code-analysis/quality-rules/ca1016)|Пометьте сборки с помощью AssemblyVersionAttribute|
|[CA1017](/dotnet/fundamentals/code-analysis/quality-rules/ca1017)|Пометьте сборки с помощью ComVisibleAttribute|
|[CA1018](/dotnet/fundamentals/code-analysis/quality-rules/ca1018)|Пометьте атрибуты с помощью AttributeUsageAttribute|
|[CA1019](/dotnet/fundamentals/code-analysis/quality-rules/ca1019)|Определите методы доступа для аргументов атрибута|
|[CA1023](../code-quality/ca1023.md)|Индексы не должны быть многомерными|
|[CA1024](/dotnet/fundamentals/code-analysis/quality-rules/ca1024)|По возможности используйте свойства|
|[CA1025](../code-quality/ca1025.md)|Замените повторяющиеся аргументы массивом параметров|
|[CA1026](../code-quality/ca1026.md)|Не следует использовать параметры по умолчанию|
|[CA1027](/dotnet/fundamentals/code-analysis/quality-rules/ca1027)|Пометьте перечисляемые типы с помощью FlagsAttribute|
|[CA1028](/dotnet/fundamentals/code-analysis/quality-rules/ca1028)|Хранилище перечисляемых типов должно относиться к типу Int32|
|[CA1030](/dotnet/fundamentals/code-analysis/quality-rules/ca1030)|По возможности используйте события|
|[CA1031](/dotnet/fundamentals/code-analysis/quality-rules/ca1031)|Не перехватывайте типы общих исключений|
|[CA1032](/dotnet/fundamentals/code-analysis/quality-rules/ca1032)|Реализуйте стандартные конструкторы исключений|
|[CA1033](/dotnet/fundamentals/code-analysis/quality-rules/ca1033)|Методы интерфейса должны быть доступны для вызова дочерними типами|
|[CA1034](/dotnet/fundamentals/code-analysis/quality-rules/ca1034)|Вложенные типы не должны быть видимыми|
|[CA1035](../code-quality/ca1035.md)|В составе реализаций ICollection есть члены со строгим типом|
|[CA1036](/dotnet/fundamentals/code-analysis/quality-rules/ca1036)|Переопределите методы в сопоставимых типах|
|[CA1038](../code-quality/ca1038.md)|Перечислители должны иметь строгие типы|
|[CA1039](../code-quality/ca1039.md)|Списки имеют строгие типы|
|[CA1041](/dotnet/fundamentals/code-analysis/quality-rules/ca1041)|Укажите сообщение ObsoleteAttribute|
|[CA1043](/dotnet/fundamentals/code-analysis/quality-rules/ca1043)|Используйте целый или строковый аргумент для индексаторов|
|[CA1044](/dotnet/fundamentals/code-analysis/quality-rules/ca1044)|Свойства не должны быть доступными только для записи|
|[CA1046](/dotnet/fundamentals/code-analysis/quality-rules/ca1046)|Не перегружайте оператор равенства для ссылочных типов|
|[CA1047](/dotnet/fundamentals/code-analysis/quality-rules/ca1047)|Не объявляйте защищенные члены в запечатанных типах|
|[CA1048](../code-quality/ca1048.md)|Не объявляйте виртуальные члены в запечатанных типах|
|[CA1049](../code-quality/ca1049.md)|Типы, которым принадлежат собственные ресурсы, должны быть освобождаемыми|
|[CA1050](/dotnet/fundamentals/code-analysis/quality-rules/ca1050)|Объявите типы в пространствах имен|
|[CA1051](/dotnet/fundamentals/code-analysis/quality-rules/ca1051)|Не объявляйте видимые поля экземпляров|
|[CA1052](/dotnet/fundamentals/code-analysis/quality-rules/ca1052)|Типы со статическими заполнителями должны быть запечатаны|
|[CA1053](/dotnet/fundamentals/code-analysis/quality-rules/ca1053)|Типы со статическими заполнителями не должны иметь конструкторы|
|[CA1054](/dotnet/fundamentals/code-analysis/quality-rules/ca1054)|Параметры URI не должны быть строками|
|[CA1055](/dotnet/fundamentals/code-analysis/quality-rules/ca1055)|Возвращаемые значения URI не должны быть строками|
|[CA1056](/dotnet/fundamentals/code-analysis/quality-rules/ca1056)|Свойства URI не должны быть строками|
|[CA1057](../code-quality/ca1057.md)|Перегрузки строковых параметров URI вызывают перегрузки System.Uri|
|[CA1058](/dotnet/fundamentals/code-analysis/quality-rules/ca1058)|Типы не должны расширять определенные базовые типы|
|[CA1059](../code-quality/ca1059.md)|Члены не должны предоставлять определенные конкретные типы|
|[CA1060](/dotnet/fundamentals/code-analysis/quality-rules/ca1060)|Переместите методы P/Invoke в класс NativeMethods|
|[CA1061](/dotnet/fundamentals/code-analysis/quality-rules/ca1061)|Не скрывайте методы базовых классов|
|[CA1063](/dotnet/fundamentals/code-analysis/quality-rules/ca1063)|Правильно реализуйте IDisposable|
|[CA1064](/dotnet/fundamentals/code-analysis/quality-rules/ca1064)|Исключения должны быть общими|
|[CA1065](/dotnet/fundamentals/code-analysis/quality-rules/ca1065)|Не вызывайте исключения в непредвиденных местах|
|[CA1301](../code-quality/ca1301.md)|Избегайте повторяющихся акселераторов|
|[CA1400](../code-quality/ca1400.md)|Для методов P/Invoke должны существовать точки входа|
|[CA1401](/dotnet/fundamentals/code-analysis/quality-rules/ca1401)|Методы P/Invoke не должны быть видимыми|
|[CA1403](../code-quality/ca1403.md)|Типы с автомакетом не должны быть видимыми для COM|
|[CA1404](../code-quality/ca1404.md)|Вызывайте GetLastError сразу после P/Invoke|
|[CA1405](../code-quality/ca1405.md)|Базовые типы, относящиеся к типу, видимому для COM, должны быть видимыми для COM|
|[CA1410](../code-quality/ca1410.md)|Методы регистрации COM должны быть согласованными|
|[CA1415](../code-quality/ca1415.md)|Правильно объявляйте методы P/Invoke|
|[CA1500](../code-quality/ca1500.md)|Имена переменных не должны совпадать с именами полей|
|[CA1502](/dotnet/fundamentals/code-analysis/quality-rules/ca1502)|Избегайте чрезмерной сложности|
|[CA1708](/dotnet/fundamentals/code-analysis/quality-rules/ca1708)|Идентификаторы должны отличаться не только прописными и строчными буквами|
|[CA1716](/dotnet/fundamentals/code-analysis/quality-rules/ca1716)|Идентификаторы не должны совпадать с ключевыми словами|
|[CA1801](/dotnet/fundamentals/code-analysis/quality-rules/ca1801)|Проверьте неиспользуемые параметры|
|[CA1804](../code-quality/ca1804.md)|Удалите неиспользуемые локальные переменные|
|[CA1809](../code-quality/ca1809.md)|Избегайте лишних локальных переменных|
|[CA1810](/dotnet/fundamentals/code-analysis/quality-rules/ca1810)|Инициализируйте статические поля ссылочных типов при объявлении|
|[CA1811](../code-quality/ca1811.md)|Избегайте невызываемого частного кода|
|[CA1812](/dotnet/fundamentals/code-analysis/quality-rules/ca1812)|Избегайте неиспользуемых внутренних классов|
|[CA1813](/dotnet/fundamentals/code-analysis/quality-rules/ca1813)|Избегайте незапечатанных атрибутов|
|[CA1814](/dotnet/fundamentals/code-analysis/quality-rules/ca1814)|Используйте массивы массивов вместо многомерных массивов|
|[CA1815](/dotnet/fundamentals/code-analysis/quality-rules/ca1815)|Переопределяйте операторы Equals и равенства для типов значений|
|[CA1819](/dotnet/fundamentals/code-analysis/quality-rules/ca1819)|Свойства не должны возвращать массивы|
|[CA1820](/dotnet/fundamentals/code-analysis/quality-rules/ca1820)|Проверяйте наличие пустых строк, используя длину строки|
|[CA1821](/dotnet/fundamentals/code-analysis/quality-rules/ca1821)|Удалите пустые методы завершения|
|[CA1822](/dotnet/fundamentals/code-analysis/quality-rules/ca1822)|Пометьте члены как статические|
|[CA1823](/dotnet/fundamentals/code-analysis/quality-rules/ca1823)|Избегайте неиспользуемых частных полей|
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
|[CA2201](/dotnet/fundamentals/code-analysis/quality-rules/ca2201)|Не порождайте исключения зарезервированных типов|
|[CA2202](../code-quality/ca2202.md)|Не ликвидируйте объекты несколько раз|
|[CA2205](../code-quality/ca2205.md)|Используйте управляемые эквиваленты Win32 API|
|[CA2207](/dotnet/fundamentals/code-analysis/quality-rules/ca2207)|Используйте встроенную инициализацию статических полей типов значений|
|[CA2208](/dotnet/fundamentals/code-analysis/quality-rules/ca2208)|Правильно создавайте экземпляры исключений аргументов|
|[CA2211](/dotnet/fundamentals/code-analysis/quality-rules/ca2211)|Поля, не являющиеся константами, не должны быть видимыми|
|[CA2212](../code-quality/ca2212.md)|Не помечайте обслуживаемые компоненты с помощью WebMethod|
|[CA2213](/dotnet/fundamentals/code-analysis/quality-rules/ca2213)|Следует высвобождать высвобождаемые поля|
|[CA2214](/dotnet/fundamentals/code-analysis/quality-rules/ca2214)|Не вызывайте переопределяемые методы в конструкторах|
|[CA2216](/dotnet/fundamentals/code-analysis/quality-rules/ca2216)|Высвобождаемые типы должны объявлять методы завершения|
|[CA2217](/dotnet/fundamentals/code-analysis/quality-rules/ca2217)|Не помечайте перечисляемые типы с помощью FlagsAttribute|
|[CA2219](/dotnet/fundamentals/code-analysis/quality-rules/ca2219)|В предложениях с исключениями не должны порождаться исключения|
|[CA2220](../code-quality/ca2220.md)|Методы завершения должны вызывать метод завершения базового класса|
|[CA2221](../code-quality/ca2221.md)|Методы завершения должны быть защищенными|
|[CA2222](../code-quality/ca2222.md)|Не уменьшайте видимость наследуемого члена|
|[CA2223](../code-quality/ca2223.md)|Члены должны различаться не только возвращаемым типом|
|[CA2224](../code-quality/ca2224.md)|Переопределяйте Equals при перегрузке оператора равенства|
|[CA2225](/dotnet/fundamentals/code-analysis/quality-rules/ca2225)|Для перегрузок операторов существуют варианты с именами|
|[CA2226](/dotnet/fundamentals/code-analysis/quality-rules/ca2226)|Перегрузки операторов должны быть симметричными|
|[CA2227](/dotnet/fundamentals/code-analysis/quality-rules/ca2227)|Свойства, возвращающие коллекции, должны быть доступными только для чтения|
|[CA2229](/dotnet/fundamentals/code-analysis/quality-rules/ca2229)|Реализуйте конструкторы сериализации|
|[CA2230](../code-quality/ca2230.md)|Используйте параметры для аргументов переменной|
|[CA2231](/dotnet/fundamentals/code-analysis/quality-rules/ca2231)|Перегрузите оператор равенства на переопределяющем типе ValueType.Equals|
|[CA2232](../code-quality/ca2232.md)|Отметьте точки входа Windows Forms меткой STAThread|
|[CA2234](/dotnet/fundamentals/code-analysis/quality-rules/ca2234)|Передавайте объекты System.Uri вместо строк|
|[CA2235](/dotnet/fundamentals/code-analysis/quality-rules/ca2235)|Пометьте все несериализуемые поля|
|[CA2236](../code-quality/ca2236.md)|Вызывайте методы базового класса для типов ISerializable|
|[CA2237](/dotnet/fundamentals/code-analysis/quality-rules/ca2237)|Пометьте типы ISerializable атрибутом SerializableAttribute|
|[CA2238](../code-quality/ca2238.md)|Правильно реализуйте методы сериализации|
|[CA2239](../code-quality/ca2239.md)|Обеспечьте наличие методов десериализации в необязательных полях|
|[CA2240](../code-quality/ca2240.md)|Правильно реализуйте ISerializable|
|[CA2241](/dotnet/fundamentals/code-analysis/quality-rules/ca2241)|Задайте правильные аргументы для методов форматирования|
|[CA2242](/dotnet/fundamentals/code-analysis/quality-rules/ca2242)|Правильно выполняйте проверку NaN|
