---
title: Состояние порта правила FxCop
ms.date: 05/21/2019
description: Сведения о правилах статического анализа кода, перенесенных в анализаторы .NET в Visual Studio. Просматривайте правила и ресурсы по переносу обновлений.
ms.custom: SEO-VS-2020
ms.topic: reference
helpviewer_keywords:
- fxcop rules
- .NET analyzers, ported rules
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: de23f3529cfcd321b0a7c3f9844ac69d96fed9c3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860325"
---
# <a name="fxcop-rule-port-status"></a>Состояние порта правила FxCop

Если в Visual Studio ранее использовался статический анализ кода, возможно, вас интересует, какие из этих правил доступны в текущей реализации в виде [анализаторов .NET](install-net-analyzers.md). На этой странице перечислены правила, которые были перенесены. См. раздел [неперенесенные правила](fxcop-unported-rules.md) для тех, которые не были перенесены и есть ли планы на их перенос.

## <a name="ported-rules"></a>Перенесенные правила

На [странице автоматически сформированной документации](https://github.com/dotnet/roslyn-analyzers/blob/master/src/NetAnalyzers/Microsoft.CodeAnalysis.NetAnalyzers.md) в репозитории Roslyn-Analyzers содержится самый актуальный список правил, которые были перенесены в анализаторы Roslyn. Эта страница также содержит дополнительные сведения, например, включено ли правило по умолчанию и имеет ли оно соответствующее *исправление кода*. ([Исправления кода](../ide/quick-actions.md) — это исправления одного щелчка, доступные в меню значка лампочки в Visual Studio.)

В соответствии с датой на этой странице список правил FxCop, которые были перенесены в [анализаторы .NET](install-net-analyzers.md) , включают:

Идентификатор правила | Название
--------|---------
[CA1000](/dotnet/fundamentals/code-analysis/quality-rules/ca1000) | Не объявляйте статические члены в универсальных типах
[CA1001](/dotnet/fundamentals/code-analysis/quality-rules/ca1001) | Типы, которым принадлежат освобождаемые поля, должны быть освобождаемыми
[CA1002](/dotnet/fundamentals/code-analysis/quality-rules/ca1002) | Не предоставляйте универсальные списки
[CA1003](/dotnet/fundamentals/code-analysis/quality-rules/ca1003) | Используйте экземпляры обработчика универсальных событий
[CA1005](/dotnet/fundamentals/code-analysis/quality-rules/ca1005) | Не используйте слишком много параметров в универсальных типах
[CA1008](/dotnet/fundamentals/code-analysis/quality-rules/ca1008) | Перечисляемые типы должны иметь нулевое значение
[CA1010](/dotnet/fundamentals/code-analysis/quality-rules/ca1010) | Коллекции должны реализовать универсальный интерфейс
[CA1012](/dotnet/fundamentals/code-analysis/quality-rules/ca1012) | Абстрактные типы не должны иметь конструкторы
[CA1014](/dotnet/fundamentals/code-analysis/quality-rules/ca1014) | Пометьте сборки с помощью CLSCompliant
[CA1016](/dotnet/fundamentals/code-analysis/quality-rules/ca1016) | Пометить сборки версией сборки
[CA1017](/dotnet/fundamentals/code-analysis/quality-rules/ca1017) | Пометить сборки атрибутом ComVisible
[CA1018](/dotnet/fundamentals/code-analysis/quality-rules/ca1018) | Пометьте атрибуты с помощью AttributeUsageAttribute
[CA1019](/dotnet/fundamentals/code-analysis/quality-rules/ca1019) | Определите методы доступа для аргументов атрибута
[CA1021](/dotnet/fundamentals/code-analysis/quality-rules/ca1021) | Не используйте параметры out
[CA1024](/dotnet/fundamentals/code-analysis/quality-rules/ca1024) | По возможности используйте свойства
[CA1027](/dotnet/fundamentals/code-analysis/quality-rules/ca1027) | Пометьте перечисляемые типы с помощью FlagsAttribute
[CA1028](/dotnet/fundamentals/code-analysis/quality-rules/ca1028) | Хранилище перечислений должно иметь тип Int32
[CA1030](/dotnet/fundamentals/code-analysis/quality-rules/ca1030) | По возможности используйте события
[CA1031](/dotnet/fundamentals/code-analysis/quality-rules/ca1031) | Не перехватывайте типы общих исключений
[CA1032](/dotnet/fundamentals/code-analysis/quality-rules/ca1032) | Реализуйте стандартные конструкторы исключений
[CA1033](/dotnet/fundamentals/code-analysis/quality-rules/ca1033) | Методы интерфейса должны быть доступны для вызова дочерними типами
[CA1034](/dotnet/fundamentals/code-analysis/quality-rules/ca1034) | Вложенные типы не должны быть видимыми
[CA1036](/dotnet/fundamentals/code-analysis/quality-rules/ca1036) | Переопределите методы в сопоставимых типах
[CA1040](/dotnet/fundamentals/code-analysis/quality-rules/ca1040) | Не используйте пустые интерфейсы
[CA1041](/dotnet/fundamentals/code-analysis/quality-rules/ca1041) | Укажите сообщение ObsoleteAttribute
[CA1043](/dotnet/fundamentals/code-analysis/quality-rules/ca1043) | Использование целочисленного или строкового аргумента для индексаторов
[CA1044](/dotnet/fundamentals/code-analysis/quality-rules/ca1044) | Свойства не должны быть доступными только для записи
[CA1045](/dotnet/fundamentals/code-analysis/quality-rules/ca1045) | Не передавайте типы по ссылке
[CA1046](/dotnet/fundamentals/code-analysis/quality-rules/ca1046) | Не перегружайте оператор равенства для ссылочных типов
[CA1047](/dotnet/fundamentals/code-analysis/quality-rules/ca1047) | Не объявляйте защищенные члены в запечатанных типах
[CA1050](/dotnet/fundamentals/code-analysis/quality-rules/ca1050) | Объявите типы в пространствах имен
[CA1051](/dotnet/fundamentals/code-analysis/quality-rules/ca1051) | Не объявляйте видимые поля экземпляров
[CA1052](/dotnet/fundamentals/code-analysis/quality-rules/ca1052) | Типы со статическими заполнителями должны быть статическими или NotInheritable
[CA1053](/dotnet/fundamentals/code-analysis/quality-rules/ca1053) | Типы статических владельцев не должны иметь конструкторы (CA1053 является частью [CA1052](/dotnet/fundamentals/code-analysis/quality-rules/ca1052) для анализаторов .NET)
[CA1054](/dotnet/fundamentals/code-analysis/quality-rules/ca1054) | Параметры URI не должны быть строками
[CA1055](/dotnet/fundamentals/code-analysis/quality-rules/ca1055) | Возвращаемые значения URI не должны быть строками
[CA1056](/dotnet/fundamentals/code-analysis/quality-rules/ca1056) | Свойства URI не должны быть строками
[CA1058](/dotnet/fundamentals/code-analysis/quality-rules/ca1058) | Типы не должны расширять определенные базовые типы
[CA1060](/dotnet/fundamentals/code-analysis/quality-rules/ca1060) | Перемещение пинвокес в класс методов машинного кода
[CA1061](/dotnet/fundamentals/code-analysis/quality-rules/ca1061) | Не скрывайте методы базовых классов
[CA1062](/dotnet/fundamentals/code-analysis/quality-rules/ca1062) | Проверьте аргументы или открытые методы
[CA1063](/dotnet/fundamentals/code-analysis/quality-rules/ca1063) | Правильно реализуйте IDisposable
[CA1064](/dotnet/fundamentals/code-analysis/quality-rules/ca1064) | Исключения должны быть общими
[CA1065](/dotnet/fundamentals/code-analysis/quality-rules/ca1065) | Не вызывайте исключения в непредвиденных местах
[CA1066](/dotnet/fundamentals/code-analysis/quality-rules/ca1066) | Тип {0} должен реализовывать IEquatable, \<T> так как он переопределяет Equals
[CA1067](/dotnet/fundamentals/code-analysis/quality-rules/ca1067) | Переопределить Object. Equals (Object) при реализации IEquatable\<T>
[CA1303](/dotnet/fundamentals/code-analysis/quality-rules/ca1303) | Не передавайте литералы в качестве локализованных параметров
[CA1304](/dotnet/fundamentals/code-analysis/quality-rules/ca1304) | Указывайте CultureInfo
[CA1305](/dotnet/fundamentals/code-analysis/quality-rules/ca1305) | Указывайте IFormatProvider
[CA1307](/dotnet/fundamentals/code-analysis/quality-rules/ca1307) | Укажите StringComparison для ясности
[CA1308](/dotnet/fundamentals/code-analysis/quality-rules/ca1308) | Нормализуйте строки в верхний регистр
[CA1309](/dotnet/fundamentals/code-analysis/quality-rules/ca1309) | Использовать порядковое сравнение строк
[CA1401](/dotnet/fundamentals/code-analysis/quality-rules/ca1401) | Методы P/Invoke не должны быть видимыми
[CA1501](/dotnet/fundamentals/code-analysis/quality-rules/ca1501) | Избегайте излишнего наследования
[CA1502](/dotnet/fundamentals/code-analysis/quality-rules/ca1502) | Избегайте чрезмерной сложности
[CA1505](/dotnet/fundamentals/code-analysis/quality-rules/ca1505) | Избегайте кода, неудобного для поддержки
[CA1506](/dotnet/fundamentals/code-analysis/quality-rules/ca1506) | Избегайте чрезмерной взаимозависимости классов
[CA1700](/dotnet/fundamentals/code-analysis/quality-rules/ca1700) | Не присваивайте перечисляемым значениям имя Reserved
[CA1707](/dotnet/fundamentals/code-analysis/quality-rules/ca1707) | Идентификаторы не должны содержать символы подчеркивания
[CA1708](/dotnet/fundamentals/code-analysis/quality-rules/ca1708) | Идентификаторы должны отличаться не только прописными и строчными буквами
[CA1710](/dotnet/fundamentals/code-analysis/quality-rules/ca1710) | Идентификаторы должны иметь правильные суффиксы
[CA1711](/dotnet/fundamentals/code-analysis/quality-rules/ca1711) | Идентификаторы не должны иметь неправильные суффиксы
[CA1712](/dotnet/fundamentals/code-analysis/quality-rules/ca1712) | Не добавляйте имя типа перед перечисляемыми значениями
[CA1713](/dotnet/fundamentals/code-analysis/quality-rules/ca1713) | События не должны иметь префикс before или after
[CA1714](/dotnet/fundamentals/code-analysis/quality-rules/ca1714) | У перечислений флагов должны быть имена во множественном числе
[CA1715](/dotnet/fundamentals/code-analysis/quality-rules/ca1715) | Идентификаторы должны иметь правильные префиксы
[CA1716](/dotnet/fundamentals/code-analysis/quality-rules/ca1716) | Идентификаторы не должны совпадать с ключевыми словами
[CA1717](/dotnet/fundamentals/code-analysis/quality-rules/ca1717) | Только перечисления FlagsAttribute должны иметь имена во множественном числе
[CA1720](/dotnet/fundamentals/code-analysis/quality-rules/ca1720) | Идентификатор содержит имя типа
[CA1721](/dotnet/fundamentals/code-analysis/quality-rules/ca1721) | Имена свойств не должны совпадать с именами методов get
[CA1724](/dotnet/fundamentals/code-analysis/quality-rules/ca1724) | Имена типов не должны совпадать с именами пространств имен
[CA1725](/dotnet/fundamentals/code-analysis/quality-rules/ca1725) | Имена параметров должны соответствовать базовому объявлению
[CA1801](/dotnet/fundamentals/code-analysis/quality-rules/ca1801) | Проверьте неиспользуемые параметры
[CA1802](/dotnet/fundamentals/code-analysis/quality-rules/ca1802) | Используйте литералы там, где это уместно
[CA1805](/dotnet/fundamentals/code-analysis/quality-rules/ca1805) | Не выполнять инициализацию без необходимости
[CA1806](/dotnet/fundamentals/code-analysis/quality-rules/ca1806) | Не игнорируйте результаты метода
[CA1810](/dotnet/fundamentals/code-analysis/quality-rules/ca1810) | Инициализируйте статические поля ссылочных типов при объявлении
[CA1812](/dotnet/fundamentals/code-analysis/quality-rules/ca1812) | Избегайте неиспользуемых внутренних классов
[CA1813](/dotnet/fundamentals/code-analysis/quality-rules/ca1813) | Избегайте незапечатанных атрибутов
[CA1814](/dotnet/fundamentals/code-analysis/quality-rules/ca1814) | Используйте массивы массивов вместо многомерных массивов
[CA1815](/dotnet/fundamentals/code-analysis/quality-rules/ca1815) | Переопределяйте операторы Equals и равенства для типов значений
[CA1816](/dotnet/fundamentals/code-analysis/quality-rules/ca1816) | Методы Dispose должны вызывать SuppressFinalize
[CA1819](/dotnet/fundamentals/code-analysis/quality-rules/ca1819) | Свойства не должны возвращать массивы
[CA1820](/dotnet/fundamentals/code-analysis/quality-rules/ca1820) | Проверяйте наличие пустых строк, используя длину строки
[CA1821](/dotnet/fundamentals/code-analysis/quality-rules/ca1821) | Удалить пустые методы завершения
[CA1822](/dotnet/fundamentals/code-analysis/quality-rules/ca1822) | Пометьте члены как статические
[CA1823](/dotnet/fundamentals/code-analysis/quality-rules/ca1823) | Избегайте неиспользуемых частных полей
[CA1824](/dotnet/fundamentals/code-analysis/quality-rules/ca1824) | Помечайте сборки с помощью NeutralResourcesLanguageAttribute
[CA1825](/dotnet/fundamentals/code-analysis/quality-rules/ca1825) | Избегайте выделения массивов нулевой длины.
[CA2000](/dotnet/fundamentals/code-analysis/quality-rules/ca2000) | Ликвидируйте объекты перед потерей области
[CA2002](/dotnet/fundamentals/code-analysis/quality-rules/ca2002) | Не блокируйте объекты с ненадежными удостоверениями
[CA2100](/dotnet/fundamentals/code-analysis/quality-rules/ca2100) | Проверьте запросы SQL на наличие уязвимостей системы безопасности
[CA2101](/dotnet/fundamentals/code-analysis/quality-rules/ca2101) | Укажите тип маршалинга для строковых аргументов P/Invoke
[CA2109](/dotnet/fundamentals/code-analysis/quality-rules/ca2109) | Проверьте видимые обработчики событий
[CA2119](/dotnet/fundamentals/code-analysis/quality-rules/ca2119) | Запечатайте методы, соответствующие частным интерфейсам
[CA2153](/dotnet/fundamentals/code-analysis/quality-rules/ca2153) | Не перехватывайте исключения поврежденного состояния
[CA2200](/dotnet/fundamentals/code-analysis/quality-rules/ca2200) | Вызывайте, чтобы сохранить сведения о стеке.
[CA2201](/dotnet/fundamentals/code-analysis/quality-rules/ca2201) | Не порождайте исключения зарезервированных типов
[CA2207](/dotnet/fundamentals/code-analysis/quality-rules/ca2207) | Используйте встроенную инициализацию статических полей типов значений
[CA2208](/dotnet/fundamentals/code-analysis/quality-rules/ca2208) | Правильно создавайте экземпляры исключений аргументов
[CA2211](/dotnet/fundamentals/code-analysis/quality-rules/ca2211) | Поля, не являющиеся константами, не должны быть видимыми
[CA2213](/dotnet/fundamentals/code-analysis/quality-rules/ca2213) | Следует высвобождать высвобождаемые поля
[CA2214](/dotnet/fundamentals/code-analysis/quality-rules/ca2214) | Не вызывайте переопределяемые методы в конструкторах
[CA2215](/dotnet/fundamentals/code-analysis/quality-rules/ca2215) | Метод Dispose должен вызывать базовый класс Dispose
[CA2216](/dotnet/fundamentals/code-analysis/quality-rules/ca2216) | Высвобождаемые типы должны объявлять методы завершения
[CA2217](/dotnet/fundamentals/code-analysis/quality-rules/ca2217) | Не помечайте перечисляемые типы с помощью FlagsAttribute
[CA2219](/dotnet/fundamentals/code-analysis/quality-rules/ca2219) | Не вызывайте исключения в предложениях finally
[CA2225](/dotnet/fundamentals/code-analysis/quality-rules/ca2225) | Для перегрузок операторов существуют варианты с именами
[CA2226](/dotnet/fundamentals/code-analysis/quality-rules/ca2226) | Перегрузки операторов должны быть симметричными
[CA2227](/dotnet/fundamentals/code-analysis/quality-rules/ca2227) | Свойства, возвращающие коллекции, должны быть доступными только для чтения
[CA2229](/dotnet/fundamentals/code-analysis/quality-rules/ca2229) | Реализуйте конструкторы сериализации
[CA2231](/dotnet/fundamentals/code-analysis/quality-rules/ca2231) | Перегруженный оператор равенства при переопределении значения типа Equals
[CA2234](/dotnet/fundamentals/code-analysis/quality-rules/ca2234) | Передавать системные объекты URI вместо строк
[CA2235](/dotnet/fundamentals/code-analysis/quality-rules/ca2235) | Пометьте все несериализуемые поля
[CA2237](/dotnet/fundamentals/code-analysis/quality-rules/ca2237) | Пометьте типы ISerializable атрибутом serializable
[CA2241](/dotnet/fundamentals/code-analysis/quality-rules/ca2241) | Задайте правильные аргументы для методов форматирования
[CA2242](/dotnet/fundamentals/code-analysis/quality-rules/ca2242) | Правильно выполняйте проверку NaN
[CA2243](/dotnet/fundamentals/code-analysis/quality-rules/ca2243) | Синтаксический разбор строковых литералов должен осуществляться правильно
[CA2300](/dotnet/fundamentals/code-analysis/quality-rules/ca2300) | Не используйте небезопасный десериализатор BinaryFormatter
[CA2301](/dotnet/fundamentals/code-analysis/quality-rules/ca2301) | Не вызывайте BinaryFormatter.Deserialize, не задав предварительно BinaryFormatter.Binder
[CA2302](/dotnet/fundamentals/code-analysis/quality-rules/ca2302) | Убедитесь, что BinaryFormatter.Binder задан перед вызовом BinaryFormatter.Deserialize
[CA2305](/dotnet/fundamentals/code-analysis/quality-rules/ca2305) | Не используйте небезопасный десериализатор LosFormatter
[CA2310](/dotnet/fundamentals/code-analysis/quality-rules/ca2310) | Не используйте небезопасный десериализатор NetDataContractSerializer
[CA2311](/dotnet/fundamentals/code-analysis/quality-rules/ca2311) | Не десериализируйте, не задав предварительно NetDataContractSerializer.Binder
[CA2312](/dotnet/fundamentals/code-analysis/quality-rules/ca2312) | Убедитесь, что NetDataContractSerializer.Binder задан перед десериализацией
[CA2315](/dotnet/fundamentals/code-analysis/quality-rules/ca2315) | Не используйте небезопасный десериализатор ObjectStateFormatter
[CA2321](/dotnet/fundamentals/code-analysis/quality-rules/ca2321) | Не десериализируйте с помощью JavaScriptSerializer, используя SimpleTypeResolver
[CA2322](/dotnet/fundamentals/code-analysis/quality-rules/ca2322) | Убедитесь, что JavaScriptSerializer не был инициализирован с помощью SimpleTypeResolver до десериализации
[CA3001](/dotnet/fundamentals/code-analysis/quality-rules/ca3001) | Проверьте код на наличие уязвимостей к внедрению кода SQL
[CA3002](/dotnet/fundamentals/code-analysis/quality-rules/ca3002) | Проверьте код на наличие уязвимостей к межсайтовым сценариям (XSS)
[CA3003](/dotnet/fundamentals/code-analysis/quality-rules/ca3003) | Проверьте код на наличие уязвимостей к внедрению пути к файлу
[CA3004](/dotnet/fundamentals/code-analysis/quality-rules/ca3004) | Проверьте код на наличие уязвимостей к раскрытию информации
[CA3005](/dotnet/fundamentals/code-analysis/quality-rules/ca3005) | Проверьте код на наличие уязвимостей к внедрению LDAP
[CA3006](/dotnet/fundamentals/code-analysis/quality-rules/ca3006) | Проверьте код на наличие уязвимостей к внедрению команд процесса
[CA3007](/dotnet/fundamentals/code-analysis/quality-rules/ca3007) | Проверьте код на наличие уязвимостей к открытому перенаправлению
[CA3008](/dotnet/fundamentals/code-analysis/quality-rules/ca3008) | Проверьте код на наличие уязвимостей к внедрению кода XPath
[CA3009](/dotnet/fundamentals/code-analysis/quality-rules/ca3009) | Проверьте код на наличие уязвимостей к внедрению кода XML
[CA3010](/dotnet/fundamentals/code-analysis/quality-rules/ca3010) | Проверьте код на наличие уязвимостей к внедрению кода XAML
[CA3011](/dotnet/fundamentals/code-analysis/quality-rules/ca3011) | Проверьте код на наличие уязвимостей к внедрению DLL
[CA3012](/dotnet/fundamentals/code-analysis/quality-rules/ca3012) | Проверьте код на наличие уязвимостей к внедрению регулярных выражений
[CA3061](/dotnet/fundamentals/code-analysis/quality-rules/ca3061) | Не добавлять схему по URL-адресу
[CA3075](/dotnet/fundamentals/code-analysis/quality-rules/ca3075) | Небезопасная обработка DTD в формате XML
[CA3076](/dotnet/fundamentals/code-analysis/quality-rules/ca3076) | Незащищенная обработка скриптов XSLT.
[CA3077](/dotnet/fundamentals/code-analysis/quality-rules/ca3077) | Небезопасная обработка в конструкторе API, XmlDocument и XmlTextReader
[CA3147](/dotnet/fundamentals/code-analysis/quality-rules/ca3147) | Помечайте обработчики команд с помощью токена проверки подделки
[CA5350](/dotnet/fundamentals/code-analysis/quality-rules/ca5350) | Не используйте ненадежные алгоритмы шифрования
[CA5351](/dotnet/fundamentals/code-analysis/quality-rules/ca5351) | Не используйте неработающие алгоритмы шифрования
[CA5358](/dotnet/fundamentals/code-analysis/quality-rules/ca5358) | Не используйте небезопасные режимы шифрования
CA5359 | Не отключайте проверку сертификата
CA5360 | Не вызывайте опасные методы при десериализации
[CA5361](/dotnet/fundamentals/code-analysis/quality-rules/ca5361) | Не отключайте использование стойкого шифрования SChannel
CA5362 | Не обращаться к Self в сериализуемых классах
[CA5363](/dotnet/fundamentals/code-analysis/quality-rules/ca5363) | Не отключайте проверку запроса
[CA5364](/dotnet/fundamentals/code-analysis/quality-rules/ca5364) | Не используйте устаревшие протоколы безопасности
CA5365 | Не отключайте проверку заголовка HTTP
CA5366 | Использование XmlReader для чтения XML-данных
CA5367 | Не сериализовывать типы с полями указателя
CA5368 | Задать ViewStateUserKey для классов, производных от страницы
[CA5369](/dotnet/fundamentals/code-analysis/quality-rules/ca5369) | Использование XmlReader для десериализации
[CA5370](/dotnet/fundamentals/code-analysis/quality-rules/ca5370) | Использование XmlReader для проверки модуля чтения
[CA5371](/dotnet/fundamentals/code-analysis/quality-rules/ca5371) | Использование XmlReader для чтения схемы
[CA5372](/dotnet/fundamentals/code-analysis/quality-rules/ca5372) | Использование XmlReader для XPathDocument
[CA5373](/dotnet/fundamentals/code-analysis/quality-rules/ca5373) | Не использовать устаревшую функцию формирования ключа
CA5374 | Не использовать XslTransform
CA5375 | Не использовать подписанный URL общего доступа
CA5376 | Использование Шаредакцесспротокол Хттпсонли
CA5377 | Использовать политику доступа на уровне контейнера
[CA5378](/dotnet/fundamentals/code-analysis/quality-rules/ca5378) | Не отключайте ServicePointManagerSecurityProtocols
CA5379 | Не используйте алгоритм функции наследования слабых ключей
CA9999 | Несоответствие версии анализатора

## <a name="see-also"></a>См. также раздел

- [Правила анализатора .NET](https://github.com/dotnet/roslyn-analyzers/blob/master/src/NetAnalyzers/Microsoft.CodeAnalysis.NetAnalyzers.md)
