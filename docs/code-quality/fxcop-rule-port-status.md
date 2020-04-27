---
title: Состояние порта правила FxCop
ms.date: 05/21/2019
ms.topic: reference
helpviewer_keywords:
- fxcop rules
- fxcop analyzers, ported rules
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 8fa572c3db3726bd1a8518990e1adfdba3c09269
ms.sourcegitcommit: 93859158465eab3423a0c0435f06490f0a456a57
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167414"
---
# <a name="fxcop-rule-port-status"></a>Состояние порта правила FxCop

Если в Visual Studio ранее использовался статический анализ кода, возможно, вас интересует, какие из этих правил доступны в текущей реализации в качестве [анализаторов FxCop](install-fxcop-analyzers.md). На этой странице перечислены правила, которые переносятся, а также те, которые не были перенесены и планируется ли их перенести.

## <a name="ported-rules"></a>Перенесенные правила

На [странице автоматически сформированной документации](https://github.com/dotnet/roslyn-analyzers/blob/master/src/Microsoft.CodeAnalysis.FxCopAnalyzers/Microsoft.CodeAnalysis.FxCopAnalyzers.md) в репозитории Roslyn-Analyzers содержится самый актуальный список правил, которые были перенесены в средства FxCop Analyzer. Эта страница также содержит дополнительные сведения, например, включено ли правило по умолчанию и имеет ли оно соответствующее *исправление кода*. ([Исправления кода](../ide/quick-actions.md) — это исправления одного щелчка, доступные в меню значка лампочки в Visual Studio.)

В соответствии с датой на этой странице в списке правил FxCop, которые были перенесены в средства [FxCop Analyzer](install-fxcop-analyzers.md) , входят:

Идентификатор правила | Заголовок
--------|---------
[CA1000](ca1000-do-not-declare-static-members-on-generic-types.md) | Не объявляйте статические члены в универсальных типах
[CA1001](ca1001-types-that-own-disposable-fields-should-be-disposable.md) | Типы, которым принадлежат освобождаемые поля, должны быть освобождаемыми
[CA1003](ca1003-use-generic-event-handler-instances.md) | Используйте экземпляры обработчика универсальных событий
[CA1008](ca1008-enums-should-have-zero-value.md) | Перечисляемые типы должны иметь нулевое значение
[CA1010](ca1010-collections-should-implement-generic-interface.md) | Коллекции должны реализовать универсальный интерфейс
[CA1012](ca1012-abstract-types-should-not-have-constructors.md) | Абстрактные типы не должны иметь конструкторы
[CA1014](ca1014-mark-assemblies-with-clscompliantattribute.md) | Пометьте сборки с помощью CLSCompliant
[CA1016](ca1016-mark-assemblies-with-assemblyversionattribute.md) | Пометить сборки версией сборки
[CA1017](ca1017-mark-assemblies-with-comvisibleattribute.md) | Пометить сборки атрибутом ComVisible
[CA1018](ca1018-mark-attributes-with-attributeusageattribute.md) | Пометьте атрибуты с помощью AttributeUsageAttribute
[CA1019](ca1019-define-accessors-for-attribute-arguments.md) | Определите методы доступа для аргументов атрибута
[CA1021](ca1021.md) | Не используйте параметры out
[CA1024](ca1024-use-properties-where-appropriate.md) | По возможности используйте свойства
[CA1027](ca1027-mark-enums-with-flagsattribute.md) | Пометьте перечисляемые типы с помощью FlagsAttribute
[CA1028](ca1028-enum-storage-should-be-int32.md) | Хранилище перечислений должно иметь тип Int32
[CA1030](ca1030-use-events-where-appropriate.md) | По возможности используйте события
[CA1031](ca1031-do-not-catch-general-exception-types.md) | Не перехватывайте типы общих исключений
[CA1032](ca1032-implement-standard-exception-constructors.md) | Реализуйте стандартные конструкторы исключений
[CA1033](ca1033-interface-methods-should-be-callable-by-child-types.md) | Методы интерфейса должны быть доступны для вызова дочерними типами
[CA1034](ca1034-nested-types-should-not-be-visible.md) | Вложенные типы не должны быть видимыми
[CA1036](ca1036-override-methods-on-comparable-types.md) | Переопределите методы в сопоставимых типах
[CA1040](ca1040-avoid-empty-interfaces.md) | Не используйте пустые интерфейсы
[CA1041](ca1041-provide-obsoleteattribute-message.md) | Укажите сообщение ObsoleteAttribute
[CA1043](ca1043-use-integral-or-string-argument-for-indexers.md) | Использование целочисленного или строкового аргумента для индексаторов
[CA1044](ca1044-properties-should-not-be-write-only.md) | Свойства не должны быть доступными только для записи
[CA1050](ca1050-declare-types-in-namespaces.md) | Объявите типы в пространствах имен
[CA1051](ca1051-do-not-declare-visible-instance-fields.md) | Не объявляйте видимые поля экземпляров
[CA1052](ca1052-static-holder-types-should-be-sealed.md) | Типы со статическими заполнителями должны быть статическими или NotInheritable
[CA1053](ca1053-static-holder-types-should-not-have-constructors.md) | Типы статических владельцев не должны иметь конструкторы (CA1053 является частью [CA1052](ca1052-static-holder-types-should-be-sealed.md) для анализаторов FxCop)
[CA1054](ca1054-uri-parameters-should-not-be-strings.md) | Параметры URI не должны быть строками
[CA1055](ca1055-uri-return-values-should-not-be-strings.md) | Возвращаемые значения URI не должны быть строками
[CA1056](ca1056-uri-properties-should-not-be-strings.md) | Свойства URI не должны быть строками
[CA1058](ca1058-types-should-not-extend-certain-base-types.md) | Типы не должны расширять определенные базовые типы
[CA1060](ca1060-move-p-invokes-to-nativemethods-class.md) | Перемещение пинвокес в класс методов машинного кода
[CA1061](ca1061-do-not-hide-base-class-methods.md) | Не скрывайте методы базовых классов
[CA1062](ca1062-validate-arguments-of-public-methods.md) | Проверьте аргументы или открытые методы
[CA1063](ca1063-implement-idisposable-correctly.md) | Правильно реализуйте IDisposable
[CA1064](ca1064-exceptions-should-be-public.md) | Исключения должны быть общими
[CA1065](ca1065-do-not-raise-exceptions-in-unexpected-locations.md) | Не вызывайте исключения в непредвиденных местах
CA1066 | Тип {0} должен реализовывать IEquatable\<T> так как он переопределяет Equals
CA1067 | Переопределить Object. Equals (Object) при реализации\<IEquatable T>
[CA1068](ca1068.md) | Параметры CancellationToken должны быть последними
CA1200 | Избегайте использования тегов cref с префиксом
[CA1303](ca1303-do-not-pass-literals-as-localized-parameters.md) | Не передавайте литералы в качестве локализованных параметров
[CA1304](ca1304-specify-cultureinfo.md) | Указывайте CultureInfo
[CA1305](ca1305-specify-iformatprovider.md) | Указывайте IFormatProvider
[CA1307](ca1307-specify-stringcomparison.md) | Указывайте StringComparison
[CA1308](ca1308-normalize-strings-to-uppercase.md) | Нормализуйте строки в верхний регистр
[CA1309](ca1309-use-ordinal-stringcomparison.md) | Использовать порядковое сравнение строк
[CA1401](ca1401-p-invokes-should-not-be-visible.md) | Методы P/Invoke не должны быть видимыми
[CA1501](ca1501-avoid-excessive-inheritance.md) | Избегайте излишнего наследования
[CA1502](ca1502-avoid-excessive-complexity.md) | Избегайте чрезмерной сложности
[CA1505](ca1505-avoid-unmaintainable-code.md) | Избегайте кода, неудобного для поддержки
[CA1506](ca1506-avoid-excessive-class-coupling.md) | Избегайте чрезмерной взаимозависимости классов
[CA1507](ca1507.md) | Использование NameOf для выражения имен символов
CA1508 | Избегайте неработающего условного кода
CA1509 | Недопустимая запись в файле спецификации правил метрик кода
[CA1707](ca1707-identifiers-should-not-contain-underscores.md) | Идентификаторы не должны содержать символы подчеркивания
[CA1708](ca1708-identifiers-should-differ-by-more-than-case.md) | Идентификаторы должны отличаться не только прописными и строчными буквами
[CA1710](ca1710-identifiers-should-have-correct-suffix.md) | Идентификаторы должны иметь правильные суффиксы
[CA1711](ca1711-identifiers-should-not-have-incorrect-suffix.md) | Идентификаторы не должны иметь неправильные суффиксы
[CA1712](ca1712-do-not-prefix-enum-values-with-type-name.md) | Не добавляйте имя типа перед перечисляемыми значениями
[CA1714](ca1714-flags-enums-should-have-plural-names.md) | У перечислений флагов должны быть имена во множественном числе
[CA1715](ca1715-identifiers-should-have-correct-prefix.md) | Идентификаторы должны иметь правильные префиксы
[CA1716](ca1716-identifiers-should-not-match-keywords.md) | Идентификаторы не должны совпадать с ключевыми словами
[CA1717](ca1717-only-flagsattribute-enums-should-have-plural-names.md) | Только перечисления FlagsAttribute должны иметь имена во множественном числе
[CA1720](ca1720-identifiers-should-not-contain-type-names.md) | Идентификатор содержит имя типа
[CA1721](ca1721-property-names-should-not-match-get-methods.md) | Имена свойств не должны совпадать с именами методов get
[CA1724](ca1724-type-names-should-not-match-namespaces.md) | Имена типов не должны совпадать с именами пространств имен
[CA1725](ca1725-parameter-names-should-match-base-declaration.md) | Имена параметров должны соответствовать базовому объявлению
[CA1801](ca1801.md) | Проверьте неиспользуемые параметры
[CA1802](ca1802.md) | Используйте литералы там, где это уместно
[CA1806](ca1806.md) | Не игнорируйте результаты метода
[CA1810](ca1810.md) | Инициализируйте статические поля ссылочных типов при объявлении
[CA1812](ca1812.md) | Избегайте неиспользуемых внутренних классов
[CA1813](ca1813.md) | Избегайте незапечатанных атрибутов
[CA1814](ca1814.md) | Используйте массивы массивов вместо многомерных массивов
[CA1815](ca1815.md) | Переопределяйте операторы Equals и равенства для типов значений
[CA1816](ca1816.md) | Методы Dispose должны вызывать SuppressFinalize
[CA1819](ca1819.md) | Свойства не должны возвращать массивы
[CA1820](ca1820.md) | Проверяйте наличие пустых строк, используя длину строки
[CA1821](ca1821.md) | Удалить пустые методы завершения
[CA1822](ca1822.md) | Пометьте члены как статические
[CA1823](ca1823.md) | Избегайте неиспользуемых частных полей
[CA1824](ca1824.md) | Помечайте сборки с помощью NeutralResourcesLanguageAttribute
[CA2000](ca2000.md) | Ликвидируйте объекты перед потерей области
[CA2002](ca2002.md) | Не блокируйте объекты с ненадежными удостоверениями
[CA2007](ca2007.md) | Попробуйте вызвать ConfigureAwait для ожидаемой задачи
CA2008 | Не создавать задачи без передачи TaskScheduler
CA2009 | Не вызывайте Тоиммутаблеколлектион для значения Иммутаблеколлектион
CA2010 | Всегда потреблять значение, возвращаемое методами, помеченными Пресервесигаттрибуте
[CA2100](ca2100.md) | Проверьте запросы SQL на наличие уязвимостей системы безопасности
[CA2101](ca2101.md) | Укажите тип маршалинга для строковых аргументов P/Invoke
[CA2119](ca2119.md) | Запечатайте методы, соответствующие частным интерфейсам
[CA2153](ca2153.md) | Не перехватывайте исключения поврежденного состояния
[CA2200](ca2200.md) | Вызывайте, чтобы сохранить сведения о стеке.
[CA2201](ca2201.md) | Не порождайте исключения зарезервированных типов
[CA2207](ca2207.md) | Используйте встроенную инициализацию статических полей типов значений
[CA2208](ca2208.md) | Правильно создавайте экземпляры исключений аргументов
[CA2211](ca2211.md) | Поля, не являющиеся константами, не должны быть видимыми
[CA2213](ca2213.md) | Следует высвобождать высвобождаемые поля
[CA2214](ca2214.md) | Не вызывайте переопределяемые методы в конструкторах
[CA2216](ca2216.md) | Высвобождаемые типы должны объявлять методы завершения
[CA2217](ca2217.md) | Не помечайте перечисляемые типы с помощью FlagsAttribute
[CA2218](ca2218.md) | Переопределяйте GetHashCode при переопределении Equals
[CA2219](ca2219.md) | Не вызывайте исключения в предложениях finally
[CA2224](ca2224.md) | Переопределять Equals при перегрузке оператора равенства
[CA2225](ca2225.md) | Для перегрузок операторов существуют варианты с именами
[CA2226](ca2226.md) | Перегрузки операторов должны быть симметричными
[CA2227](ca2227.md) | Свойства, возвращающие коллекции, должны быть доступными только для чтения
[CA2229](ca2229.md) | Реализуйте конструкторы сериализации
[CA2231](ca2231.md) | Перегруженный оператор равенства при переопределении значения типа Equals
[CA2234](ca2234.md) | Передавать системные объекты URI вместо строк
[CA2235](ca2235.md) | Пометьте все несериализуемые поля
[CA2237](ca2237.md) | Пометьте типы ISerializable атрибутом serializable
[CA2241](ca2241.md) | Задайте правильные аргументы для методов форматирования
[CA2242](ca2242.md) | Правильно выполняйте проверку NaN
[CA2243](ca2243.md) | Синтаксический разбор строковых литералов должен осуществляться правильно
CA2244 | Не дублировать инициализации индексированных элементов
[CA2300](ca2300.md) | Не используйте небезопасный десериализатор BinaryFormatter
[CA2301](ca2301.md) | Не вызывайте BinaryFormatter.Deserialize, не задав предварительно BinaryFormatter.Binder
[CA2302](ca2302.md) | Убедитесь, что BinaryFormatter.Binder задан перед вызовом BinaryFormatter.Deserialize
[CA2305](ca2305.md) | Не используйте небезопасный десериализатор LosFormatter
[CA2310](ca2310.md) | Не используйте небезопасный десериализатор NetDataContractSerializer
[CA2311](ca2311.md) | Не десериализируйте, не задав предварительно NetDataContractSerializer.Binder
[CA2312](ca2312.md) | Убедитесь, что NetDataContractSerializer.Binder задан перед десериализацией
[CA2315](ca2315.md) | Не используйте небезопасный десериализатор ObjectStateFormatter
[CA2321](ca2321.md) | Не десериализируйте с помощью JavaScriptSerializer, используя SimpleTypeResolver
[CA2322](ca2322.md) | Убедитесь, что JavaScriptSerializer не был инициализирован с помощью SimpleTypeResolver до десериализации
[CA3001](ca3001.md) | Проверьте код на наличие уязвимостей к внедрению кода SQL
[CA3002](ca3002.md) | Проверьте код на наличие уязвимостей к межсайтовым сценариям (XSS)
[CA3003](ca3003.md) | Проверьте код на наличие уязвимостей к внедрению пути к файлу
[CA3004](ca3004.md) | Проверьте код на наличие уязвимостей к раскрытию информации
[CA3005](ca3005.md) | Проверьте код на наличие уязвимостей к внедрению LDAP
[CA3006](ca3006.md) | Проверьте код на наличие уязвимостей к внедрению команд процесса
[CA3007](ca3007.md) | Проверьте код на наличие уязвимостей к открытому перенаправлению
[CA3008](ca3008.md) | Проверьте код на наличие уязвимостей к внедрению кода XPath
[CA3009](ca3009.md) | Проверьте код на наличие уязвимостей к внедрению кода XML
[CA3010](ca3010.md) | Проверьте код на наличие уязвимостей к внедрению кода XAML
[CA3011](ca3011.md) | Проверьте код на наличие уязвимостей к внедрению DLL
[CA3012](ca3012.md) | Проверьте код на наличие уязвимостей к внедрению регулярных выражений
CA3061 | Не добавлять схему по URL-адресу
[CA3075](ca3075.md) | Небезопасная обработка DTD в формате XML
[CA3076](ca3076.md) | Незащищенная обработка скриптов XSLT.
[CA3077](ca3077.md) | Небезопасная обработка в конструкторе API, XmlDocument и XmlTextReader
[CA3147](ca3147.md) | Помечайте обработчики команд с помощью токена проверки подделки
[CA5350](ca5350.md) | Не используйте ненадежные алгоритмы шифрования
[CA5351](ca5351.md) | Не используйте неработающие алгоритмы шифрования
CA5358 | Не используйте небезопасные режимы шифрования
CA5359 | Не отключайте проверку сертификата
CA5360 | Не вызывайте опасные методы при десериализации
CA5361 | Не отключайте использование стойкого шифрования SChannel
CA5362 | Не обращаться к Self в сериализуемых классах
CA5363 | Не отключайте проверку запроса
CA5364 | Не используйте устаревшие протоколы безопасности
CA5365 | Не отключайте проверку заголовка HTTP
CA5366 | Использование XmlReader для чтения XML-данных
CA5367 | Не сериализовывать типы с полями указателя
CA5368 | Задать ViewStateUserKey для классов, производных от страницы
CA5369 | Использование XmlReader для десериализации
CA5370 | Использование XmlReader для проверки модуля чтения
CA5371 | Использование XmlReader для чтения схемы
CA5372 | Использование XmlReader для XPathDocument
CA5373 | Не использовать устаревшую функцию формирования ключа
CA5374 | Не использовать XslTransform
CA5375 | Не использовать подписанный URL общего доступа
CA5376 | Использование Шаредакцесспротокол Хттпсонли
CA5377 | Использовать политику доступа на уровне контейнера
CA5378 | Не отключайте ServicePointManagerSecurityProtocols
CA5379 | Не используйте алгоритм функции наследования слабых ключей
CA9999 | Несоответствие версии анализатора

## <a name="unported-rules"></a>Неперенесенные правила

Набор правил, которые не были перенесены в [анализаторы FxCop](install-fxcop-analyzers.md) , состоит из правил, которые еще не были включены, но по-прежнему [могут быть перенесены](#rules-that-may-be-ported)и [не будут перенесены](#deprecated-rules).

### <a name="rules-that-may-be-ported"></a>Правила, которые могут быть перенесены

Следующие правила анализа прежних версий FxCop еще не были реализованы в качестве анализаторов, но все равно могут быть. Это может быть вызвано блокирующей технической причиной или просто тем, что правило имеет более низкий приоритет. Для получения дополнительных сведений о состоянии переноса каждого правила щелкните ссылку в столбце **проблемы отслеживания** .

Идентификатор правила | Отслеживание проблемы
--- | ---
[CA1002](ca1002-do-not-expose-generic-lists.md) | [https://github.com/dotnet/roslyn-analyzers/issues/369](https://github.com/dotnet/roslyn-analyzers/issues/369)
[CA1004](ca1004-generic-methods-should-provide-type-parameter.md) | [https://github.com/dotnet/roslyn-analyzers/issues/370](https://github.com/dotnet/roslyn-analyzers/issues/370)
[CA1005](ca1005-avoid-excessive-parameters-on-generic-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/371](https://github.com/dotnet/roslyn-analyzers/issues/371)
[CA1006](ca1006-do-not-nest-generic-types-in-member-signatures.md) | [https://github.com/dotnet/roslyn-analyzers/issues/372](https://github.com/dotnet/roslyn-analyzers/issues/372)
[CA1007](ca1007-use-generics-where-appropriate.md) | [https://github.com/dotnet/roslyn-analyzers/issues/373](https://github.com/dotnet/roslyn-analyzers/issues/373)
[CA1011](ca1011-consider-passing-base-types-as-parameters.md) | [https://github.com/dotnet/roslyn-analyzers/issues/375](https://github.com/dotnet/roslyn-analyzers/issues/375)
[CA1021](ca1021-avoid-out-parameters.md) | [https://github.com/dotnet/roslyn-analyzers/issues/377](https://github.com/dotnet/roslyn-analyzers/issues/377)
[CA1023](ca1023-indexers-should-not-be-multidimensional.md) | [https://github.com/dotnet/roslyn-analyzers/issues/378](https://github.com/dotnet/roslyn-analyzers/issues/378)
[CA1045](ca1045-do-not-pass-types-by-reference.md) | [https://github.com/dotnet/roslyn-analyzers/issues/391](https://github.com/dotnet/roslyn-analyzers/issues/391)
[CA1046](ca1046-do-not-overload-operator-equals-on-reference-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/392](https://github.com/dotnet/roslyn-analyzers/issues/392)
[CA1047](ca1047-do-not-declare-protected-members-in-sealed-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/393](https://github.com/dotnet/roslyn-analyzers/issues/393)
[CA1048](ca1048-do-not-declare-virtual-members-in-sealed-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/394](https://github.com/dotnet/roslyn-analyzers/issues/394)
[CA1049](ca1049-types-that-own-native-resources-should-be-disposable.md) | [https://github.com/dotnet/roslyn-analyzers/issues/395](https://github.com/dotnet/roslyn-analyzers/issues/395)
[CA1057](ca1057-string-uri-overloads-call-system-uri-overloads.md) | [https://github.com/dotnet/roslyn-analyzers/issues/401](https://github.com/dotnet/roslyn-analyzers/issues/401)
[CA1300](ca1300-specify-messageboxoptions.md) | [https://github.com/dotnet/roslyn-analyzers/issues/408](https://github.com/dotnet/roslyn-analyzers/issues/408)
[CA1301](ca1301-avoid-duplicate-accelerators.md) | [https://github.com/dotnet/roslyn-analyzers/issues/409](https://github.com/dotnet/roslyn-analyzers/issues/409)
[CA1306](ca1306-set-locale-for-data-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/414](https://github.com/dotnet/roslyn-analyzers/issues/414)
[CA1402](ca1402-avoid-overloads-in-com-visible-interfaces.md) | [https://github.com/dotnet/roslyn-analyzers/issues/418](https://github.com/dotnet/roslyn-analyzers/issues/418)
[CA1403](ca1403-auto-layout-types-should-not-be-com-visible.md) | [https://github.com/dotnet/roslyn-analyzers/issues/419](https://github.com/dotnet/roslyn-analyzers/issues/419)
[CA1404](ca1404-call-getlasterror-immediately-after-p-invoke.md) | [https://github.com/dotnet/roslyn-analyzers/issues/420](https://github.com/dotnet/roslyn-analyzers/issues/420)
[CA1405](ca1405-com-visible-type-base-types-should-be-com-visible.md) | [https://github.com/dotnet/roslyn-analyzers/issues/421](https://github.com/dotnet/roslyn-analyzers/issues/421)
[CA1407](ca1407-avoid-static-members-in-com-visible-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/423](https://github.com/dotnet/roslyn-analyzers/issues/423)
[CA1408](ca1408-do-not-use-autodual-classinterfacetype.md) | [https://github.com/dotnet/roslyn-analyzers/issues/424](https://github.com/dotnet/roslyn-analyzers/issues/424)
[CA1409](ca1409-com-visible-types-should-be-creatable.md) | [https://github.com/dotnet/roslyn-analyzers/issues/425](https://github.com/dotnet/roslyn-analyzers/issues/425)
[CA1410](ca1410-com-registration-methods-should-be-matched.md) | [https://github.com/dotnet/roslyn-analyzers/issues/426](https://github.com/dotnet/roslyn-analyzers/issues/426)
[CA1411](ca1411-com-registration-methods-should-not-be-visible.md) | [https://github.com/dotnet/roslyn-analyzers/issues/427](https://github.com/dotnet/roslyn-analyzers/issues/427)
[CA1412](ca1412-mark-comsource-interfaces-as-idispatch.md) | [https://github.com/dotnet/roslyn-analyzers/issues/428](https://github.com/dotnet/roslyn-analyzers/issues/428)
[CA1413](ca1413-avoid-non-public-fields-in-com-visible-value-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/429](https://github.com/dotnet/roslyn-analyzers/issues/429)
[CA1414](ca1414-mark-boolean-p-invoke-arguments-with-marshalas.md) | [https://github.com/dotnet/roslyn-analyzers/issues/430](https://github.com/dotnet/roslyn-analyzers/issues/430)
[CA1415](ca1415-declare-p-invokes-correctly.md) | [https://github.com/dotnet/roslyn-analyzers/issues/431](https://github.com/dotnet/roslyn-analyzers/issues/431)
[CA1500](ca1500-variable-names-should-not-match-field-names.md) | [https://github.com/dotnet/roslyn-analyzers/issues/432](https://github.com/dotnet/roslyn-analyzers/issues/432)
[CA1600](ca1600-do-not-use-idle-process-priority.md) | [https://github.com/dotnet/roslyn-analyzers/issues/438](https://github.com/dotnet/roslyn-analyzers/issues/438)
[CA1601](ca1601-do-not-use-timers-that-prevent-power-state-changes.md) | [https://github.com/dotnet/roslyn-analyzers/issues/439](https://github.com/dotnet/roslyn-analyzers/issues/439)
[CA1700](ca1700-do-not-name-enum-values-reserved.md) | [https://github.com/dotnet/roslyn-analyzers/issues/440](https://github.com/dotnet/roslyn-analyzers/issues/440)
[CA1704](ca1704-identifiers-should-be-spelled-correctly.md) | [https://github.com/dotnet/roslyn-analyzers/issues/443](https://github.com/dotnet/roslyn-analyzers/issues/443)
[CA1709](ca1709-identifiers-should-be-cased-correctly.md) | [https://github.com/dotnet/roslyn-analyzers/issues/445](https://github.com/dotnet/roslyn-analyzers/issues/445)
[CA1713](ca1713-events-should-not-have-before-or-after-prefix.md) | [https://github.com/dotnet/roslyn-analyzers/issues/449](https://github.com/dotnet/roslyn-analyzers/issues/449)
[CA1719](ca1719-parameter-names-should-not-match-member-names.md) | [https://github.com/dotnet/roslyn-analyzers/issues/453](https://github.com/dotnet/roslyn-analyzers/issues/453)
[CA1722](ca1722-identifiers-should-not-have-incorrect-prefix.md) | [https://github.com/dotnet/roslyn-analyzers/issues/455](https://github.com/dotnet/roslyn-analyzers/issues/455)
[CA1726](ca1726-use-preferred-terms.md) | [https://github.com/dotnet/roslyn-analyzers/issues/458](https://github.com/dotnet/roslyn-analyzers/issues/458)
[CA1804](ca1804.md) | [https://github.com/dotnet/roslyn-analyzers/issues/461](https://github.com/dotnet/roslyn-analyzers/issues/461)
[CA1811](ca1811.md) | [https://github.com/dotnet/roslyn-analyzers/issues/464](https://github.com/dotnet/roslyn-analyzers/issues/464)
[CA1900](ca1900.md) | [https://github.com/dotnet/roslyn-analyzers/issues/474](https://github.com/dotnet/roslyn-analyzers/issues/474)
[CA2001](ca2001.md) | [https://github.com/dotnet/roslyn-analyzers/issues/477](https://github.com/dotnet/roslyn-analyzers/issues/477)
[CA2004](ca2004.md) | [https://github.com/dotnet/roslyn-analyzers/issues/479](https://github.com/dotnet/roslyn-analyzers/issues/479)
[CA2006](ca2006.md) | [https://github.com/dotnet/roslyn-analyzers/issues/480](https://github.com/dotnet/roslyn-analyzers/issues/480)
[CA2109](ca2109.md) | [https://github.com/dotnet/roslyn-analyzers/issues/488](https://github.com/dotnet/roslyn-analyzers/issues/488)
[CA2204](ca2204.md) | [https://github.com/dotnet/roslyn-analyzers/issues/529](https://github.com/dotnet/roslyn-analyzers/issues/529)
[CA2205](ca2205.md) | [https://github.com/dotnet/roslyn-analyzers/issues/530](https://github.com/dotnet/roslyn-analyzers/issues/530)
[CA2212](ca2212.md) | [https://github.com/dotnet/roslyn-analyzers/issues/534](https://github.com/dotnet/roslyn-analyzers/issues/534)
[CA2215](ca2215.md) | [https://github.com/dotnet/roslyn-analyzers/issues/535](https://github.com/dotnet/roslyn-analyzers/issues/535)
[CA2232](ca2232.md) | [https://github.com/dotnet/roslyn-analyzers/issues/545](https://github.com/dotnet/roslyn-analyzers/issues/545)
[CA2236](ca2236.md) | [https://github.com/dotnet/roslyn-analyzers/issues/548](https://github.com/dotnet/roslyn-analyzers/issues/548)
[CA2238](ca2238.md) | [https://github.com/dotnet/roslyn-analyzers/issues/549](https://github.com/dotnet/roslyn-analyzers/issues/549)
[CA2239](ca2239.md) | [https://github.com/dotnet/roslyn-analyzers/issues/550](https://github.com/dotnet/roslyn-analyzers/issues/550)
[CA2240](ca2240.md) | [https://github.com/dotnet/roslyn-analyzers/issues/551](https://github.com/dotnet/roslyn-analyzers/issues/551)

### <a name="deprecated-rules"></a>Устаревшие правила

Следующие правила анализа прежних версий FxCop являются устаревшими и не будут реализованы как анализаторы. Дополнительные сведения можно найти по ИДЕНТИФИКАТОРу правила (например, **CA1009**) на [странице проблем Roslyn-Analyzers GitHub](https://github.com/dotnet/roslyn-analyzers/issues?utf8=%E2%9C%93&q=is:issue+label:FxCop-Port).

- [CA1009](ca1009-declare-event-handlers-correctly.md)
- [CA1020](ca1020-avoid-namespaces-with-few-types.md)
- [CA1025](ca1025-replace-repetitive-arguments-with-params-array.md)
- [CA1026](ca1026-default-parameters-should-not-be-used.md)
- [CA1035](ca1035-icollection-implementations-have-strongly-typed-members.md)
- [CA1038](ca1038-enumerators-should-be-strongly-typed.md)
- [CA1039](ca1039-lists-are-strongly-typed.md)
- [CA1059](ca1059-members-should-not-expose-certain-concrete-types.md)
- [CA1302](ca1302-do-not-hardcode-locale-specific-strings.md)
- [CA1400](ca1400-p-invoke-entry-points-should-exist.md)
- [CA1406](ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)
- [CA1504](ca1504-review-misleading-field-names.md)
- [CA1701](ca1701.md)
- [CA1702](ca1702.md)
- [CA1703](ca1703.md)
- [CA1800](ca1800.md)
- [CA1809](ca1809.md)
- [CA1901](ca1901.md)
- [CA1903](ca1903.md)
- [CA2003](ca2003.md)
- [CA2102](ca2102.md)
- [CA2103](ca2103.md)
- [CA2104](ca2104.md)
- [CA2105](ca2105.md)
- [CA2106](ca2106.md)
- [CA2107](ca2107.md)
- [CA2108](ca2108.md)
- [CA2111](ca2111.md)
- [CA2112](ca2112.md)
- [CA2114](ca2114.md)
- [CA2115](ca2115.md)
- [CA2116](ca2116.md)
- [CA2117](ca2117.md)
- [CA2118](ca2118.md)
- [CA2120](ca2120.md)
- [CA2121](ca2121.md)
- [CA2122](ca2122.md)
- [CA2123](ca2123.md)
- [CA2124](ca2124.md)
- [CA2126](ca2126.md)
- [CA2130](ca2130.md)
- [CA2131](ca2131.md)
- [CA2132](ca2132.md)
- [CA2133](ca2133.md)
- [CA2134](ca2134.md)
- [CA2135](ca2135.md)
- [CA2136](ca2136.md)
- [CA2137](ca2137.md)
- [CA2138](ca2138.md)
- [CA2139](ca2139.md)
- [CA2140](ca2140.md)
- [CA2141](ca2141.md)
- [CA2142](ca2142.md)
- [CA2143](ca2143.md)
- [CA2144](ca2144.md)
- [CA2145](ca2145.md)
- [CA2146](ca2146.md)
- [CA2147](ca2147.md)
- [CA2149](ca2149.md)
- [CA2151](ca2151.md)
- [CA2202](ca2202.md)
- [CA2210](ca2210.md)
- [CA2220](ca2220.md)
- [CA2221](ca2221.md)
- [CA2222](ca2222.md) ([обоснование](https://github.com/dotnet/roslyn-analyzers/issues/1378))
- [CA2223](ca2223.md)
- [CA2228](ca2228.md)
- [CA2230](ca2230.md)
- [CA2233](ca2233.md)
- [CA5122](ca5122.md)

## <a name="see-also"></a>См. также

- [Правила Microsoft. CodeAnalysis. Фкскопанализерс](https://github.com/dotnet/roslyn-analyzers/blob/master/src/Microsoft.CodeAnalysis.FxCopAnalyzers/Microsoft.CodeAnalysis.FxCopAnalyzers.md)
