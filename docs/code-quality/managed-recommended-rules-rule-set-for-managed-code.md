---
title: "Набор правил &quot;Рекомендуемые правила для управляемого кода&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1d1160f8-4e51-4e70-99cd-82ad10ee7b32
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Набор правил &quot;Рекомендуемые правила для управляемого кода&quot;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Набор правил "Рекомендуемые правила Майкрософт для управляемого кода" используется для того, чтобы сосредоточиться на наиболее критических проблемах управляемого кода, включая возможные бреши в системе безопасности, сбои приложения и другие важные ошибки логики и проектирования.  Данный набор правил должен входить в любой настраиваемый набор правил проекта.  
  
|Правило|Описание|  
|-------------|--------------|  
|[CA1001](../Topic/CA1001:%20Types%20that%20own%20disposable%20fields%20should%20be%20disposable.md)|Типы, которым принадлежат освобождаемые поля, должны быть освобождаемыми|  
|[CA1009](../code-quality/ca1009-declare-event-handlers-correctly.md)|Правильно объявите обработчики событий|  
|[CA1016](../code-quality/ca1016-mark-assemblies-with-assemblyversionattribute.md)|Пометьте сборки атрибутом AssemblyVersionAttribute|  
|[CA1033](../Topic/CA1033:%20Interface%20methods%20should%20be%20callable%20by%20child%20types.md)|Методы интерфейса должны быть доступны для вызова дочерним типам|  
|[CA1049](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)|Типы, которым принадлежат собственные ресурсы, должны быть освобождаемыми|  
|[CA1060](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)|Переместите P\/Invokes в класс NativeMethods|  
|[CA1061](../code-quality/ca1061-do-not-hide-base-class-methods.md)|Не скрывайте методы базового класса|  
|[CA1063](../code-quality/ca1063-implement-idisposable-correctly.md)|Следует правильно реализовывать IDisposable|  
|[CA1065](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)|Не вызывайте исключения в непредвиденных местах|  
|[CA1301](../Topic/CA1301:%20Avoid%20duplicate%20accelerators.md)|Избегайте повторяющихся сочетаний клавиш быстрого доступа|  
|[CA1400](../Topic/CA1400:%20P-Invoke%20entry%20points%20should%20exist.md)|Необходимо наличие точек входа P\/Invoke|  
|[CA1401](../Topic/CA1401:%20P-Invokes%20should%20not%20be%20visible.md)|Методы P\/Invoke не должны быть видимыми|  
|[CA1403](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)|Типы макета Auto не должны быть видимыми для COM|  
|[CA1404](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)|Вызовите GetLastError сразу после P\/Invoke|  
|[CA1405](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md)|Базовые типы, относящиеся к типу видимых COM\-клиенту, должны быть видимыми для COM|  
|[CA1410](../code-quality/ca1410-com-registration-methods-should-be-matched.md)|Методы регистрации COM должны быть согласованы|  
|[CA1415](../code-quality/ca1415-declare-p-invokes-correctly.md)|Правильно объявите методы P\/Invoke|  
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Удалите пустые методы завершения|  
|[CA1900](../code-quality/ca1900-value-type-fields-should-be-portable.md)|Поля типа значения должны быть переносимыми|  
|[CA1901](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|Объявления P\/Invoke должны быть переносимыми|  
|[CA2002](../Topic/CA2002:%20Do%20not%20lock%20on%20objects%20with%20weak%20identity.md)|Не блокируйте объекты со слабой идентификацией|  
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|Проанализируйте SQL\-запросы с целью выявления уязвимостей безопасности|  
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|Укажите тип маршалинга для строковых аргументов P\/Invoke|  
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|Проверьте объявляемые параметры безопасности типов значений|  
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|Указатели не должны быть видимыми|  
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|Защищенные типы не должны предоставлять поля|  
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|Безопасность метода должна быть надмножеством типа|  
|[CA2116](../Topic/CA2116:%20APTCA%20methods%20should%20only%20call%20APTCA%20methods.md)|APTCA\-методы должны вызывать только APTCA\-методы|  
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|APTCA\-типы должны расширять только базовые APTCA\-типы|  
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|Не используйте косвенное представление методов с требованиями ссылки|  
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|Переопределяющие требования ссылки должны быть идентичны базовым|  
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|Ограничьте уязвимые предложения finally во внешних блоках try|  
|[CA2126](../Topic/CA2126:%20Type%20link%20demands%20require%20inheritance%20demands.md)|Для требований ссылок на тип необходимы требования наследования|  
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|Критические с точки зрения безопасности типы могут не участвовать в эквивалентности типов|  
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|Конструкторы по умолчанию должны быть по меньшей мере такими же критическими, как конструкторы по умолчанию базового типа|  
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|Делегаты должны привязываться к методам с соответствующей прозрачностью|  
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|Методы должны сохранять согласованную прозрачность при переопределении базовых методов|  
|[CA2137](../Topic/CA2137:%20Transparent%20methods%20must%20contain%20only%20verifiable%20IL.md)|Прозрачные методы должны содержать только поддающийся проверке IL|  
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|Прозрачные методы не должны вызывать методы с атрибутом SuppressUnmanagedCodeSecurity|  
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|Прозрачный код не должен ссылаться на элементы, критичные в плане безопасности|  
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|Прозрачные методы не должны удовлетворять требования LinkDemand|  
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|Типы должны быть настолько же критическими, как их базовые типы и интерфейсы.|  
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|Прозрачные методы могут не использовать утверждения безопасности|  
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|Прозрачные методы не должны вызывать машинный код|  
|[CA2200](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)|Следует повторно вызывать исключение для сохранения сведений о стеке|  
|[CA2202](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)|Не удаляйте объекты несколько раз|  
|[CA2207](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)|Используйте встроенную инициализацию статических полей типов значений|  
|[CA2212](../code-quality/ca2212-do-not-mark-serviced-components-with-webmethod.md)|Не помечайте обслуживаемые компоненты атрибутом WebMethod|  
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Высвободите высвобождаемые поля|  
|[CA2214](../Topic/CA2214:%20Do%20not%20call%20overridable%20methods%20in%20constructors.md)|Не вызывайте переопределяемые методы в конструкторах|  
|[CA2216](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)|Высвобождаемые типы должны объявлять метод завершения|  
|[CA2220](../code-quality/ca2220-finalizers-should-call-base-class-finalizer.md)|Методы завершения должны вызывать метод завершения базового класса|  
|[CA2229](../code-quality/ca2229-implement-serialization-constructors.md)|Реализуйте конструкторы сериализации|  
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Перегружать равенство операторов следует при перегрузке ValueType.Equals|  
|[CA2232](../code-quality/ca2232-mark-windows-forms-entry-points-with-stathread.md)|Отметьте точки входа Windows Forms меткой STAThread|  
|[CA2235](../code-quality/ca2235-mark-all-non-serializable-fields.md)|Пометьте все несериализуемые поля|  
|[CA2236](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)|Вызовите методы базового класса для типов ISerializable|  
|[CA2237](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)|Пометьте типы ISerializable атрибутом SerializableAttribute|  
|[CA2238](../code-quality/ca2238-implement-serialization-methods-correctly.md)|Правильно реализуйте методы сериализации|  
|[CA2240](../Topic/CA2240:%20Implement%20ISerializable%20correctly.md)|Правильно реализуйте ISerializable|  
|[CA2241](../code-quality/ca2241-provide-correct-arguments-to-formatting-methods.md)|Предоставьте правильные аргументы методам форматирования|  
|[CA2242](../code-quality/ca2242-test-for-nan-correctly.md)|Правильно выполните проверку NaN|