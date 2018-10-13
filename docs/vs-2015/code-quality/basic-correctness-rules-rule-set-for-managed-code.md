---
title: Набор базовые правила определения правильности правил для управляемого кода | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 631f0daf-1d42-4c90-a7dc-1a6a9de64c93
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 4b435d813ad1e7c9308bfa6a7d8d243b877d6d6b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49184597"
---
# <a name="basic-correctness-rules-rule-set-for-managed-code"></a>Набор правил "Базовые правила определения правильности" для управляемого кода
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Набор правил базовые правила определения правильности посвящена логических ошибок и общие ошибки в использовании API платформы. Базовые правила определения правильности включить правила в наборе правил минимальные правила и рекомендации. Дополнительные сведения см. в разделе [набора правил управляемых рекомендуемые правила для управляемого кода](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md) следует включать это правило, задать, чтобы расширить список предупреждений, что минимального набора правил.  
  
 В следующей таблице описаны все правила в наборе правил базовые правила определения правильности Майкрософт.  
  
|Правило|Описание|  
|----------|-----------------|  
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|Типы, которым принадлежат освобождаемые поля, должны быть освобождаемыми|  
|[CA1009](../code-quality/ca1009-declare-event-handlers-correctly.md)|Правильно объявите обработчики событий|  
|[CA1016](../code-quality/ca1016-mark-assemblies-with-assemblyversionattribute.md)|Пометьте сборки атрибутом AssemblyVersionAttribute|  
|[CA1033](../code-quality/ca1033-interface-methods-should-be-callable-by-child-types.md)|Методы интерфейса должны быть дочерним типам|  
|[CA1049](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)|Типы, которым принадлежат собственные ресурсы, должны быть освобождаемыми|  
|[CA1060](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)|Переместите P/Invokes в класс NativeMethods|  
|[CA1061](../code-quality/ca1061-do-not-hide-base-class-methods.md)|Не следует скрывать методы базового класса|  
|[CA1063](../code-quality/ca1063-implement-idisposable-correctly.md)|Правильно реализуйте IDisposable|  
|[CA1065](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)|Не вызывайте исключения в непредвиденных местах|  
|[CA1301](../code-quality/ca1301-avoid-duplicate-accelerators.md)|Не|  
|[CA1400](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)|Должны существовать точки входа P/Invoke|  
|[CA1401](../code-quality/ca1401-p-invokes-should-not-be-visible.md)|P/Invoke не должны быть видимыми|  
|[CA1403](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)|Типы с автомакетом не должны быть видимыми для COM|  
|[CA1404](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)|Вызывайте GetLastError сразу после P/Invoke|  
|[CA1405](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md)|Базовые типы типу видимых COM должны быть видимыми для COM|  
|[CA1410](../code-quality/ca1410-com-registration-methods-should-be-matched.md)|Методы регистрации COM должны быть соответствующими|  
|[CA1415](../code-quality/ca1415-declare-p-invokes-correctly.md)|Правильно объявляйте методы P/Invoke|  
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Удалите пустые завершающие методы|  
|[CA1900](../code-quality/ca1900-value-type-fields-should-be-portable.md)|Поля типа значения должны быть переносимыми|  
|[CA1901](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|Объявления P/Invoke должны быть переносимыми|  
|[CA2002](../code-quality/ca2002-do-not-lock-on-objects-with-weak-identity.md)|Не блокировать объекты со слабой идентификацией|  
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|Проверка запросов SQL на наличие уязвимостей безопасности|  
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|Укажите тип маршалинга для строковых аргументов P/Invoke|  
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|Проверьте объявляемые параметры безопасности типов значений|  
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|Указатели не должны быть видимыми|  
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|Защищенные типы не должны предоставлять поля|  
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|Безопасность метода должна быть надмножеством типа|  
|[CA2116](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)|Методы APTCA должны вызывать только методы APTCA|  
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|APTCA-типы должны расширять только базовые APTCA-типы|  
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|Не используйте косвенное представление методов с запросами компоновки|  
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|Компоновки переопределения должны быть идентичны базовым|  
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|Помещайте уязвимые предложения finally во внешний блок try|  
|[CA2126](../code-quality/ca2126-type-link-demands-require-inheritance-demands.md)|Запросы компоновки типа требуют запросы наследования|  
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|Типы критической безопасности могут не участвовать в эквивалентности типа|  
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|Конструкторы по умолчанию должно быть по крайней мере настолько критичными, как конструкторы базовых типов по умолчанию|  
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|Делегаты должны привязываться к методам с согласованной прозрачностью|  
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|Методы должны сохранять согласованную прозрачность при переопределении базовых методов|  
|[CA2137](../code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il.md)|Прозрачные методы должны содержать только проверяемые IL|  
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|Прозрачные методы не должны вызывать методы с атрибутом SuppressUnmanagedCodeSecurity|  
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|Прозрачный код не должна ссылаться на элементы, критичные безопасности|  
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|Прозрачные методы не должны удовлетворять требования LinkDemand|  
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|Типы должны быть по крайней мере настолько критичными, как их базовые типы и интерфейсы|  
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|Прозрачные методы не могут использовать безопасность утверждений|  
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|Прозрачные методы не следует вызывать в машинном коде|  
|[CA2200](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)|Исключение для сохранения сведений о стеке|  
|[CA2202](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)|Не удаляйте объекты несколько раз|  
|[CA2207](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)|Инициализируйте статические поля типа значений встроенными средствами|  
|[CA2212](../code-quality/ca2212-do-not-mark-serviced-components-with-webmethod.md)|Не следует помечать обслуживаемые компоненты атрибутом WebMethod|  
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Следует высвобождать высвобождаемые поля|  
|[CA2214](../code-quality/ca2214-do-not-call-overridable-methods-in-constructors.md)|Не вызывайте переопределяемые методы в конструкторах|  
|[CA2216](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)|Высвобождаемые типы должны объявлять метод завершения|  
|[CA2220](../code-quality/ca2220-finalizers-should-call-base-class-finalizer.md)|Методы завершения должны вызывать метод завершения базового класса|  
|[CA2229](../code-quality/ca2229-implement-serialization-constructors.md)|Применяйте конструкторы сериализации|  
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Перегрузка оператора равенства на переопределяющем типе ValueType.Equals|  
|[CA2232](../code-quality/ca2232-mark-windows-forms-entry-points-with-stathread.md)|Точки входа Марк Windows Forms меткой STAThread|  
|[CA2235](../code-quality/ca2235-mark-all-non-serializable-fields.md)|Помечайте все несериализуемые поля|  
|[CA2236](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)|Вызывайте методы базового класса для типов ISerializable|  
|[CA2237](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)|Пометьте типы ISerializable атрибутом SerializableAttribute|  
|[CA2238](../code-quality/ca2238-implement-serialization-methods-correctly.md)|Правильно реализовывать методы сериализации|  
|[CA2240](../code-quality/ca2240-implement-iserializable-correctly.md)|Правильно реализуйте ISerializable|  
|[CA2241](../code-quality/ca2241-provide-correct-arguments-to-formatting-methods.md)|Предоставьте правильные аргументы методам форматирования|  
|[CA2242](../code-quality/ca2242-test-for-nan-correctly.md)|Правильно выполняйте проверку NaN|  
|[CA1008](../code-quality/ca1008-enums-should-have-zero-value.md)|Перечисления должны иметь нулевое значение|  
|[CA1013](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)|Перегружайте оператор равенства при перегрузке Добавление и вычитание|  
|[CA1303](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)|Не следует передавать литералы в виде локализованных параметров|  
|[CA1308](../code-quality/ca1308-normalize-strings-to-uppercase.md)|Строки следует нормализовать в верхний регистр|  
|[CA1806](../code-quality/ca1806-do-not-ignore-method-results.md)|Не игнорируйте результаты метода|  
|[CA1816](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)|Вызовите GC. SuppressFinalize правильно|  
|[CA1819](../code-quality/ca1819-properties-should-not-return-arrays.md)|Свойства не должны возвращать массивы|  
|[CA1820](../code-quality/ca1820-test-for-empty-strings-using-string-length.md)|Проверьте наличие пустых строк, длины строки|  
|[CA1903](../code-quality/ca1903-use-only-api-from-targeted-framework.md)|Используйте API-Интерфейс только из целевой версии .NET framework|  
|[CA2004](../code-quality/ca2004-remove-calls-to-gc-keepalive.md)|Удалите вызов GC. KeepAlive|  
|[CA2006](../code-quality/ca2006-use-safehandle-to-encapsulate-native-resources.md)|Используйте SafeHandle для инкапсуляции машинных ресурсов|  
|[CA2102](../code-quality/ca2102-catch-non-clscompliant-exceptions-in-general-handlers.md)|Перехватывайте исключения, не являющиеся CLSCompliant, с помощью общих обработчиков|  
|[CA2104](../code-quality/ca2104-do-not-declare-read-only-mutable-reference-types.md)|Не объявляйте чтения только изменяемые ссылочные типы|  
|[CA2105](../code-quality/ca2105-array-fields-should-not-be-read-only.md)|Поля массивов не должны считываться только|  
|[CA2106 ОБЕСПЕЧЬТЕ](../code-quality/ca2106-secure-asserts.md)|Обеспечьте безопасность утверждений|  
|[CA2115](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)|Вызовите GC. KeepAlive при использовании машинных ресурсов|  
|[CA2119](../code-quality/ca2119-seal-methods-that-satisfy-private-interfaces.md)|Запечатайте методы, соответствующие частным интерфейсам|  
|[CA2120](../code-quality/ca2120-secure-serialization-constructors.md)|Обеспечьте безопасность конструкторов сериализации|  
|[CA2121](../code-quality/ca2121-static-constructors-should-be-private.md)|Статические конструкторы должны быть частными|  
|[CA2130](../code-quality/ca2130-security-critical-constants-should-be-transparent.md)|Константы критической безопасности должны быть прозрачными|  
|[CA2205](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)|Используйте управляемые эквиваленты Win32 API|  
|[CA2215](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)|Методы Dispose должны вызывать метод dispose базового класса|  
|[CA2221](../code-quality/ca2221-finalizers-should-be-protected.md)|Методы завершения должны быть защищены|  
|[CA2222](../code-quality/ca2222-do-not-decrease-inherited-member-visibility.md)|Не уменьшайте видимость унаследованных членов|  
|[CA2223](../code-quality/ca2223-members-should-differ-by-more-than-return-type.md)|Члены должны различаться не только возвращаемым типом|  
|[CA2224](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)|Переопределяйте равенство при перегрузке оператора равенства|  
|[CA2226](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)|Операторы должны быть симметричны|  
|[CA2227](../code-quality/ca2227-collection-properties-should-be-read-only.md)|Свойства коллекции должны быть только для чтения|  
|[CA2239](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)|Предоставляйте методы десериализации для необязательных полей|



