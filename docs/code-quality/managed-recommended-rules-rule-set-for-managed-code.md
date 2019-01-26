---
title: Набор правил "Рекомендуемые правила для управляемого кода"
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
ms.assetid: 1d1160f8-4e51-4e70-99cd-82ad10ee7b32
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: fa15f79be09b9663fb8fc98e32e09e20a030a5d4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55009600"
---
# <a name="managed-recommended-rules-rule-set-for-managed-code"></a>Набор правил "Рекомендуемые правила для управляемого кода"
Можно использовать Microsoft управляемых рекомендуемые правила набора правил в сосредоточиться на наиболее важными проблемами в управляемом коде, включая возможные уязвимости безопасности, сбои приложения и другие важные ошибки логики и проектирования. Следует включать этот набор правил во все пользовательские наборы правил, создаваемые для проектов.

|Правило|Описание:|
|----------|-----------------|
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|Типы, которым принадлежат освобождаемые поля, должны быть освобождаемыми|
|[CA1009](../code-quality/ca1009-declare-event-handlers-correctly.md)|Правильно объявляйте обработчики событий|
|[CA1016](../code-quality/ca1016-mark-assemblies-with-assemblyversionattribute.md)|Пометьте сборки с помощью AssemblyVersionAttribute|
|[CA1033](../code-quality/ca1033-interface-methods-should-be-callable-by-child-types.md)|Методы интерфейса должны быть доступны для вызова дочерними типами|
|[CA1049](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)|Типы, которым принадлежат собственные ресурсы, должны быть освобождаемыми|
|[CA1060](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)|Переместите методы P/Invoke в класс NativeMethods|
|[CA1061](../code-quality/ca1061-do-not-hide-base-class-methods.md)|Не скрывайте методы базовых классов|
|[CA1063](../code-quality/ca1063-implement-idisposable-correctly.md)|Правильно реализуйте IDisposable|
|[CA1065](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)|Не вызывайте исключения в непредвиденных местах|
|[CA1301](../code-quality/ca1301-avoid-duplicate-accelerators.md)|Избегайте повторяющихся акселераторов|
|[CA1400](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)|Для методов P/Invoke должны существовать точки входа|
|[CA1401](../code-quality/ca1401-p-invokes-should-not-be-visible.md)|Методы P/Invoke не должны быть видимыми|
|[CA1403](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)|Типы с автомакетом не должны быть видимыми для COM|
|[CA1404](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)|Вызывайте GetLastError сразу после P/Invoke|
|[CA1405](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md)|Базовые типы, относящиеся к типу, видимому для COM, должны быть видимыми для COM|
|[CA1410](../code-quality/ca1410-com-registration-methods-should-be-matched.md)|Методы регистрации COM должны быть согласованными|
|[CA1415](../code-quality/ca1415-declare-p-invokes-correctly.md)|Правильно объявляйте методы P/Invoke|
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Удалите пустые методы завершения|
|[CA1900](../code-quality/ca1900-value-type-fields-should-be-portable.md)|Поля типов значений должны быть переносимыми|
|[CA1901](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|Объявления P/Invoke должны быть переносимыми|
|[CA2002](../code-quality/ca2002-do-not-lock-on-objects-with-weak-identity.md)|Не блокируйте объекты с ненадежными удостоверениями|
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|Проверьте запросы SQL на наличие уязвимостей системы безопасности|
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|Укажите тип маршалинга для строковых аргументов P/Invoke|
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|Проверьте объявляемые параметры безопасности типов значений|
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|Указатели не должны быть видимыми|
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|Защищенные типы не должны предоставлять поля|
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|Безопасность метода должна быть надмножеством типа|
|[CA2116](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)|APTCA-методы должны вызывать только APTCA-методы|
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|APTCA-типы должны расширять только базовые APTCA-типы|
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|Не используйте косвенное представление методов с требованиями ссылки|
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|Переопределяющие требования ссылки должны быть идентичны базовым|
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|Ограничьте уязвимые предложения finally во внешних блоках try|
|[CA2126](../code-quality/ca2126-type-link-demands-require-inheritance-demands.md)|Для требований ссылок на тип необходимы требования наследования|
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|Критические для безопасности типы не могут участвовать в эквивалентности типов|
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|Конструкторы по умолчанию должны быть по меньшей мере такими же критическими, как конструкторы по умолчанию базового типа|
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|Делегаты должны быть привязаны к методам с соответствующей прозрачностью|
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|Методы должны сохранять одинаковую прозрачность при переопределении базовых методов|
|[CA2137](../code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il.md)|Прозрачные методы должны содержать только поддающийся проверке промежуточный язык|
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|Прозрачные методы не должны вызывать методы с атрибутом SuppressUnmanagedCodeSecurity|
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|Прозрачный код не должен ссылаться на критические для безопасности элементы|
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|Прозрачные методы не должны удовлетворять требования LinkDemand|
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|Типы должны быть по крайней мере настолько же критическими, как их базовые типы и интерфейсы|
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|Прозрачные методы могут не использовать утверждения безопасности|
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|Прозрачные методы не должны вызывать машинный код|
|[CA2200](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)|Повторно порождайте исключения для сохранения сведений стека|
|[CA2202](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)|Не ликвидируйте объекты несколько раз|
|[CA2207](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)|Используйте встроенную инициализацию статических полей типов значений|
|[CA2212](../code-quality/ca2212-do-not-mark-serviced-components-with-webmethod.md)|Не помечайте обслуживаемые компоненты с помощью WebMethod|
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Следует высвобождать высвобождаемые поля|
|[CA2214](../code-quality/ca2214-do-not-call-overridable-methods-in-constructors.md)|Не вызывайте переопределяемые методы в конструкторах|
|[CA2216](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)|Высвобождаемые типы должны объявлять методы завершения|
|[CA2220](../code-quality/ca2220-finalizers-should-call-base-class-finalizer.md)|Методы завершения должны вызывать метод завершения базового класса|
|[CA2229](../code-quality/ca2229-implement-serialization-constructors.md)|Реализуйте конструкторы сериализации|
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Перегрузите оператор равенства на переопределяющем типе ValueType.Equals|
|[CA2232](../code-quality/ca2232-mark-windows-forms-entry-points-with-stathread.md)|Отметьте точки входа Windows Forms меткой STAThread|
|[CA2235](../code-quality/ca2235-mark-all-non-serializable-fields.md)|Пометьте все несериализуемые поля|
|[CA2236](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)|Вызывайте методы базового класса для типов ISerializable|
|[CA2237](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)|Пометьте типы ISerializable атрибутом SerializableAttribute|
|[CA2238](../code-quality/ca2238-implement-serialization-methods-correctly.md)|Правильно реализуйте методы сериализации|
|[CA2240](../code-quality/ca2240-implement-iserializable-correctly.md)|Правильно реализуйте ISerializable|
|[CA2241](../code-quality/ca2241-provide-correct-arguments-to-formatting-methods.md)|Задайте правильные аргументы для методов форматирования|
|[CA2242](../code-quality/ca2242-test-for-nan-correctly.md)|Правильно выполняйте проверку NaN|