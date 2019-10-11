---
title: Набор правил "Правила безопасности" для управляемого кода
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 564aeac6-03fa-41b0-b655-88179f0ab01b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 85bf4e140b3a379221c3b7e5a05428b29e3a985b
ms.sourcegitcommit: 535ef05b1e553f0fc66082cd2e0998817eb2a56a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/07/2019
ms.locfileid: "72018378"
---
# <a name="security-rules-rule-set-for-managed-code"></a>Набор правил "Правила безопасности" для управляемого кода

Используйте правило Microsoft Security Rules, установленное для устаревшего анализа кода, чтобы максимально увеличить количество потенциальных проблем безопасности, о которых сообщается.

|Правило|Описание|
|----------|-----------------|
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|Проверьте запросы SQL на наличие уязвимостей системы безопасности|
|[CA2102](../code-quality/ca2102-catch-non-clscompliant-exceptions-in-general-handlers.md)|Перехватывайте исключения, не являющиеся CLSCompliant, с помощью общих обработчиков|
|[CA2103](../code-quality/ca2103-review-imperative-security.md)|Проверьте принудительную безопасность|
|[CA2104](../code-quality/ca2104-do-not-declare-read-only-mutable-reference-types.md)|Не объявляйте изменяющиеся ссылочные типы только для чтения|
|[CA2105](../code-quality/ca2105-array-fields-should-not-be-read-only.md)|Поля массивов не должны быть доступны только для чтения|
|[CA2106](../code-quality/ca2106-secure-asserts.md)|Обеспечьте безопасность утверждений|
|[CA2107](../code-quality/ca2107-review-deny-and-permit-only-usage.md)|Проверьте использование Deny и Permit Only|
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|Проверьте объявляемые параметры безопасности типов значений|
|[CA2109](../code-quality/ca2109-review-visible-event-handlers.md)|Проверьте видимые обработчики событий|
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|Указатели не должны быть видимыми|
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|Защищенные типы не должны предоставлять поля|
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|Безопасность метода должна быть надмножеством типа|
|[CA2115](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)|Вызывайте GC.KeepAlive при использовании собственных ресурсов|
|[CA2116](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)|APTCA-методы должны вызывать только APTCA-методы|
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|APTCA-типы должны расширять только базовые APTCA-типы|
|[CA2118](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md)|Проверьте использование атрибута SuppressUnmanagedCodeSecurityAttribute|
|[CA2119](../code-quality/ca2119-seal-methods-that-satisfy-private-interfaces.md)|Запечатайте методы, соответствующие частным интерфейсам|
|[CA2120](../code-quality/ca2120-secure-serialization-constructors.md)|Обеспечьте безопасность конструкторов сериализации|
|[CA2121](../code-quality/ca2121-static-constructors-should-be-private.md)|Статические конструкторы должны быть частными|
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|Не используйте косвенное представление методов с требованиями ссылки|
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|Переопределяющие требования ссылки должны быть идентичны базовым|
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|Ограничьте уязвимые предложения finally во внешних блоках try|
|[CA2126](../code-quality/ca2126-type-link-demands-require-inheritance-demands.md)|Для требований ссылок на тип необходимы требования наследования|
|[CA2130](../code-quality/ca2130-security-critical-constants-should-be-transparent.md)|Важные константы безопасности должны быть прозрачными|
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|Критические для безопасности типы не могут участвовать в эквивалентности типов|
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|Конструкторы по умолчанию должны быть по меньшей мере такими же критическими, как конструкторы по умолчанию базового типа|
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|Делегаты должны быть привязаны к методам с соответствующей прозрачностью|
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|Методы должны сохранять одинаковую прозрачность при переопределении базовых методов|
|[CA2135](../code-quality/ca2135-level-2-assemblies-should-not-contain-linkdemands.md)|Сборки уровня 2 не должны содержать LinkDemands|
|[CA2136](../code-quality/ca2136-members-should-not-have-conflicting-transparency-annotations.md)|Члены не должны иметь противоречащие заметки прозрачности|
|[CA2137](../code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il.md)|Прозрачные методы должны содержать только поддающийся проверке промежуточный язык|
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|Прозрачные методы не должны вызывать методы с атрибутом SuppressUnmanagedCodeSecurity|
|[CA2139](../code-quality/ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute.md)|Прозрачные методы могут не использовать атрибут HandleProcessCorruptingExceptions|
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|Прозрачный код не должен ссылаться на критические для безопасности элементы|
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|Прозрачные методы не должны соответствовать требованиям LinkDemand|
|[CA2142](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)|Прозрачный код не должен быть защищен проверками LinkDemands|
|[CA2143](../code-quality/ca2143-transparent-methods-should-not-use-security-demands.md)|Прозрачные методы не должны использовать требования безопасности|
|[CA2144](../code-quality/ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays.md)|Прозрачный код не должен выполнять загрузку сборок из массивов байтов|
|[CA2145](../code-quality/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute.md)|Прозрачные методы не должны быть отмечены атрибутом SuppressUnmanagedCodeSecurityAttribute|
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|Типы должны быть по крайней мере настолько же критическими, как их базовые типы и интерфейсы|
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|Прозрачные методы могут не использовать утверждения безопасности|
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|Прозрачные методы не должны вызывать машинный код|
|[CA2210](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md)|Сборки должны иметь допустимые строгие имена|
|[CA2300](ca2300.md)|Не используйте небезопасный десериализатор BinaryFormatter|
|[CA2301](ca2301.md)|Не вызывайте BinaryFormatter.Deserialize, не задав предварительно BinaryFormatter.Binder|
|[CA2302](ca2302.md)|Убедитесь, что BinaryFormatter.Binder задан перед вызовом BinaryFormatter.Deserialize|
|[CA2305](ca2305.md)|Не используйте небезопасный десериализатор LosFormatter|
|[CA2310](ca2310.md)|Не используйте небезопасный десериализатор NetDataContractSerializer|
|[CA2311](ca2311.md)|Не десериализируйте, не задав предварительно NetDataContractSerializer.Binder|
|[CA2312](ca2312.md)|Убедитесь, что NetDataContractSerializer.Binder задан перед десериализацией|
|[CA2315](ca2315.md)|Не используйте небезопасный десериализатор ObjectStateFormatter|
|[CA2321](ca2321.md)|Не десериализируйте с помощью JavaScriptSerializer, используя SimpleTypeResolver|
|[CA2322](ca2322.md)|Убедитесь, что JavaScriptSerializer не был инициализирован с помощью SimpleTypeResolver до десериализации|
|[CA3001](../code-quality/ca3001.md)|Проверьте код на наличие уязвимостей к внедрению кода SQL|
|[CA3002](../code-quality/ca3002.md)|Проверьте код на наличие уязвимостей к межсайтовым сценариям (XSS)|
|[CA3003](../code-quality/ca3003.md)|Проверьте код на наличие уязвимостей к внедрению пути к файлу|
|[CA3004](../code-quality/ca3004.md)|Проверьте код на наличие уязвимостей к раскрытию информации|
|[CA3005](../code-quality/ca3005.md)|Проверьте код на наличие уязвимостей к внедрению LDAP|
|[CA3006](../code-quality/ca3006.md)|Проверьте код на наличие уязвимостей к внедрению команд процесса|
|[CA3007](../code-quality/ca3007.md)|Проверьте код на наличие уязвимостей к открытому перенаправлению|
|[CA3008](../code-quality/ca3008.md)|Проверьте код на наличие уязвимостей к внедрению кода XPath|
|[CA3009](../code-quality/ca3009.md)|Проверьте код на наличие уязвимостей к внедрению кода XML|
|[CA3010](../code-quality/ca3010.md)|Проверьте код на наличие уязвимостей к внедрению кода XAML|
|[CA3011](../code-quality/ca3011.md)|Проверьте код на наличие уязвимостей к внедрению DLL|
|[CA3012](../code-quality/ca3012.md)|Проверьте код на наличие уязвимостей к внедрению регулярных выражений|
