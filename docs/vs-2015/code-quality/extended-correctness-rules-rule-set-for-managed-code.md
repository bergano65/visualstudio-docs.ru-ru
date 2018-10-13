---
title: Набор расширенные правила определения правильности правил для управляемого кода | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5b181f5b-6c7a-4e46-a783-360e1da427a0
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: cebb3f492bb3aec873f503c2efcacb7220ec9739
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49187434"
---
# <a name="extended-correctness-rules-rule-set-for-managed-code"></a>Набор правил "Расширенные правила определения правильности" для управляемого кода
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Набор правил расширенные правила определения правильности Майкрософт развертывает ошибок использования логики и платформы, имена которых присутствуют в процессе анализа кода. Дополнительный акцент делается на определенных сценариях, таких как COM-взаимодействие и мобильные приложения. Рекомендуется включить это правило, если один из этих сценариев применяется к вашему проекту или для поиска дополнительных ошибок в проекте.  
  
 Расширенные правила определения правильности Майкрософт набор правил содержит правила, заданные в правиле базовые правила определения правильности Майкрософт. Базовые правила определения правильности включения правил, заданных в правиле минимальные правила и рекомендации Майкрософт. Дополнительные сведения см. в разделе [набор базовые правила определения правильности правил для управляемого кода](../code-quality/basic-correctness-rules-rule-set-for-managed-code.md) и [набора правил управляемых рекомендуемые правила для управляемого кода](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md)  
  
 В следующей таблице описаны все правила в наборе правил расширенные правила определения правильности Майкрософт.  
  
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
|[CA1032](../code-quality/ca1032-implement-standard-exception-constructors.md)|Реализуйте стандартные конструкторы исключения|  
|[CA1054](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)|Параметры URI не должны быть строками|  
|[CA1055](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)|URI возвращать значения не должны быть строками|  
|[CA1056](../code-quality/ca1056-uri-properties-should-not-be-strings.md)|Свойства URI не должны быть строками|  
|[CA1057](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)|Строка URI вызывают перегрузки System.Uri|  
|[CA1402](../code-quality/ca1402-avoid-overloads-in-com-visible-interfaces.md)|Не используйте перегрузки в интерфейсах, видимых COM|  
|[CA1406](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)|Не используйте аргументы Int64 для клиентов Visual Basic 6|  
|[CA1407](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)|Не используйте статические члены в видимых COM типах|  
|[CA1408](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)|Не используйте AutoDual ClassInterfaceType|  
|[CA1409](../code-quality/ca1409-com-visible-types-should-be-creatable.md)|Видимые COM-типы должны быть создаваемыми|  
|[CA1411](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)|Методы регистрации COM не должны быть видимыми|  
|[CA1412](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)|Помечайте интерфейсы ComSource как IDispatch|  
|[CA1413](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)|Избегайте не открытых полей в видимых типах значений COM|  
|[CA1414](../code-quality/ca1414-mark-boolean-p-invoke-arguments-with-marshalas.md)|Пометьте логические аргументы P/Invoke с помощью атрибута MarshalAs|  
|[CA1600](../code-quality/ca1600-do-not-use-idle-process-priority.md)|Не используйте приоритет процессов|  
|[CA1601](../code-quality/ca1601-do-not-use-timers-that-prevent-power-state-changes.md)|Не используйте таймеры, препятствующие изменению состояния электропитания|  
|[CA1824 СЛЕДУЕТ](../code-quality/ca1824-mark-assemblies-with-neutralresourceslanguageattribute.md)|Пометьте сборки атрибутом NeutralResourcesLanguageAttribute|  
|[CA2001](../code-quality/ca2001-avoid-calling-problematic-methods.md)|Избегайте вызовов проблемных методов|  
|[CA2003](../code-quality/ca2003-do-not-treat-fibers-as-threads.md)|Не следует обрабатывать нити как потоки|  
|[CA2135 СБОРКИ](../code-quality/ca2135-level-2-assemblies-should-not-contain-linkdemands.md)|Уровень 2 не должны содержать требования LinkDemand|  
|[CA2136](../code-quality/ca2136-members-should-not-have-conflicting-transparency-annotations.md)|Элементы не должны иметь конфликтующие пометки прозрачности|  
|[CA2139](../code-quality/ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute.md)|Прозрачные методы не могут использовать атрибут HandleProcessCorruptingExceptions|  
|[CA2142](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)|Прозрачный код не должен быть защищен с помощью требований LinkDemand|  
|[CA2143](../code-quality/ca2143-transparent-methods-should-not-use-security-demands.md)|Прозрачные методы не должны использовать требования безопасности|  
|[CA2144](../code-quality/ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays.md)|Прозрачный код не должен загружать сборки из массивов байтов|  
|[CA2145](../code-quality/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute.md)|Прозрачные методы не должны быть снабжены атрибутом SuppressUnmanagedCodeSecurityAttribute|  
|[CA2204](../code-quality/ca2204-literals-should-be-spelled-correctly.md)|Литералы должны иметь правильное правописание|  
|[CA2211](../code-quality/ca2211-non-constant-fields-should-not-be-visible.md)|Неконстантные поля не должны быть видимыми|  
|[CA2217](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)|Не следует помечать перечисления атрибутом FlagsAttribute|  
|[CA2218](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)|Переопределяйте GetHashCode при переопределении Equals|  
|[CA2219](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)|Не вызывайте исключения в предложениях исключений|  
|[CA2225](../code-quality/ca2225-operator-overloads-have-named-alternates.md)|Оператор дополнения с именами|  
|[CA2228](../code-quality/ca2228-do-not-ship-unreleased-resource-formats.md)|Не следует поставлять невыпущенные форматы ресурсов|  
|[CA2230](../code-quality/ca2230-use-params-for-variable-arguments.md)|Используйте параметры для аргументов переменной|  
|[CA2233](../code-quality/ca2233-operations-should-not-overflow.md)|Операции не должно быть переполнений|  
|[CA2234](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)|Передавайте объекты System.Uri вместо строк|  
|[CA2243](../code-quality/ca2243-attribute-string-literals-should-parse-correctly.md)|Синтаксический анализ строковых литералов атрибута должен правильно|



