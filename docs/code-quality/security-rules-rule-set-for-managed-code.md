---
title: Набор правил "Правила безопасности" для управляемого кода
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 564aeac6-03fa-41b0-b655-88179f0ab01b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 7d1f6b51f28ecbfac5f7a2b19fe7750d69ef322c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="security-rules-rule-set-for-managed-code"></a>Набор правил "Правила безопасности" для управляемого кода
Следует включить правила безопасности корпорации Майкрософт набора правил в максимально увеличить количество потенциальных проблем безопасности, включенные в отчет.

|Правило|Описание|
|----------|-----------------|
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|Проверка запросов SQL на наличие уязвимостей безопасности|
|[CA2102](../code-quality/ca2102-catch-non-clscompliant-exceptions-in-general-handlers.md)|Перехватывайте исключения, не являющиеся CLSCompliant, с помощью общих обработчиков|
|[CA2103](../code-quality/ca2103-review-imperative-security.md)|Проверьте императивную безопасность|
|[CA2104](../code-quality/ca2104-do-not-declare-read-only-mutable-reference-types.md)|Не объявляйте чтения только изменяемые ссылочные типы|
|[CA2105](../code-quality/ca2105-array-fields-should-not-be-read-only.md)|Поля массивов не должны считываться только|
|[CA2106 ОБЕСПЕЧЬТЕ](../code-quality/ca2106-secure-asserts.md)|Обеспечьте безопасность предположений|
|[CA2107](../code-quality/ca2107-review-deny-and-permit-only-usage.md)|Проверьте deny и permit только сведения об использовании|
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|Проверьте объявляемые параметры безопасности типов значений|
|[CA2109](../code-quality/ca2109-review-visible-event-handlers.md)|Проверьте видимые обработчики событий|
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|Указатели не должны быть видимыми|
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|Защищенные типы не должны предоставлять поля|
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|Безопасность метода должна быть надмножеством типа|
|[CA2115](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)|Вызывайте GC. KeepAlive при использовании собственных ресурсов|
|[CA2116](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)|Методы APTCA должны вызывать только методы APTCA|
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|APTCA-типы должны расширять только базовые APTCA-типы|
|[CA2118](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md)|Обзор использования SuppressUnmanagedCodeSecurityAttribute|
|[CA2119](../code-quality/ca2119-seal-methods-that-satisfy-private-interfaces.md)|Запечатайте методы, соответствующие частным интерфейсам|
|[CA2120](../code-quality/ca2120-secure-serialization-constructors.md)|Обеспечьте безопасность конструкторов сериализации|
|[CA2121](../code-quality/ca2121-static-constructors-should-be-private.md)|Статические конструкторы должны быть частными|
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|Не используйте косвенное представление методов с запросами компоновки|
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|Запросы компоновки переопределения должны быть идентичны базовым|
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|Помещайте уязвимые предложения finally во внешний блок try|
|[CA2126](../code-quality/ca2126-type-link-demands-require-inheritance-demands.md)|Запросы компоновки типа требуют запросы наследования|
|[CA2130](../code-quality/ca2130-security-critical-constants-should-be-transparent.md)|Константы критической безопасности должны быть прозрачными|
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|Типы критической безопасности могут не участвовать в эквивалентности типа|
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|Конструкторы по умолчанию должно быть по крайней мере такой критический, как конструкторы по умолчанию базового типа|
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|Делегаты должны привязываться к методам с согласованной прозрачностью|
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|Методы должны сохранять согласованную прозрачность при переопределении базовых методов|
|[CA2135](../code-quality/ca2135-level-2-assemblies-should-not-contain-linkdemands.md)|Сборки уровня 2 не должны содержать требования LinkDemand|
|[CA2136](../code-quality/ca2136-members-should-not-have-conflicting-transparency-annotations.md)|Элементы не должны иметь конфликтующие пометки прозрачности|
|[CA2137](../code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il.md)|Прозрачные методы должны содержать только проверяемые IL|
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|Прозрачные методы не должны вызывать методы с атрибутом SuppressUnmanagedCodeSecurity|
|[CA2139](../code-quality/ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute.md)|Прозрачные методы не могут использовать атрибут HandleProcessCorruptingExceptions|
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|Прозрачный код не должен ссылаться на критические для безопасности элементы|
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|Прозрачные методы не должны удовлетворять требования LinkDemand|
|[CA2142](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)|Прозрачный код не должен быть защищен с помощью требований LinkDemand|
|[CA2143](../code-quality/ca2143-transparent-methods-should-not-use-security-demands.md)|Прозрачные методы не должны использовать требования безопасности|
|[CA2144](../code-quality/ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays.md)|Прозрачный код не должен загружать сборки из массивов байтов|
|[CA2145](../code-quality/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute.md)|Прозрачные методы не должны быть отмечены атрибутом SuppressUnmanagedCodeSecurityAttribute.|
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|Типы должны быть настолько же критическими, как их базовые типы и интерфейсы|
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|Прозрачные методы не могут использовать безопасность утверждений|
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|Прозрачные методы не следует вызывать в машинном коде|
|[CA2210](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md)|Сборки должны иметь допустимые строгие имена|