---
title: "Набор правил &quot;Расширенные нормы и правила разработки&quot; для управляемого кода | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a338caf2-b75d-4f23-a0f9-3024fa0bceac
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Набор правил &quot;Расширенные нормы и правила разработки&quot; для управляемого кода
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Набор правил "Расширенные правила и рекомендации по разработке Майкрософт" дополняет базовые правила и рекомендации по разработке с целью повысить число выдаваемых ошибок, связанных с удобством использования и удобством поддержки.  Особое внимание при этом уделяется рекомендациям по именованию.  Данный набора правил рекомендуется добавлять, если в проекте содержится код библиотек, или в случае необходимости принудительного применения наивысших стандартов написания простого в обслуживании кода.  
  
 В наборе "Расширенные правила и рекомендации по разработке" содержатся все правила из набора правил "Базовые правила и рекомендации по разработке корпорации Майкрософт".  В наборе "Базовые правила и рекомендации по разработке" содержатся все правила из набора правил "Минимальные правила и рекомендации корпорации Майкрософт".  Дополнительные сведения см. в разделах [Набор правил "Базовые нормы и правила разработки" для управляемого кода](../code-quality/basic-design-guideline-rules-rule-set-for-managed-code.md) и [Набор правил "Рекомендуемые правила для управляемого кода"](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md).  
  
 В следующей таблице описываются все правила набора правил "Расширенные правила и рекомендации по разработке Майкрософт".  
  
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
|[CA1000](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)|Не объявляйте статические члены в универсальных типах|  
|[CA1002](../Topic/CA1002:%20Do%20not%20expose%20generic%20lists.md)|Не предоставляйте универсальные списки|  
|[CA1003](../Topic/CA1003:%20Use%20generic%20event%20handler%20instances.md)|Используйте экземпляры обработчика универсальных событий|  
|[CA1004](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)|Универсальные методы должны предоставлять параметр типа|  
|[CA1005](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)|Не используйте слишком много параметров в универсальных типах|  
|[CA1006](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)|Не создавайте вложенных универсальных типов в сигнатурах членов|  
|[CA1007](../code-quality/ca1007-use-generics-where-appropriate.md)|Используйте универсальные объекты, если это уместно|  
|[CA1008](../code-quality/ca1008-enums-should-have-zero-value.md)|Перечисляемые типы должны иметь нулевое значение|  
|[CA1010](../code-quality/ca1010-collections-should-implement-generic-interface.md)|Коллекции должны реализовывать универсальный интерфейс|  
|[CA1011](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)|Попробуйте передать базовые типы в качестве параметров|  
|[CA1012](../code-quality/ca1012-abstract-types-should-not-have-constructors.md)|Абстрактные типы не должны иметь конструкторов|  
|[CA1013](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)|Перегружайте оператор равенства при перегрузке операторов сложения и вычитания|  
|[CA1014](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md)|Помечайте сборки атрибутом CLSCompliantAttribute|  
|[CA1017](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)|Помечайте сборки атрибутом ComVisibleAttribute|  
|[CA1018](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)|Помечайте атрибуты с помощью AttributeUsageAttribute|  
|[CA1019](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)|Определите методы доступа для аргументов атрибута|  
|[CA1023](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)|Индексы не должны быть многомерными|  
|[CA1024](../code-quality/ca1024-use-properties-where-appropriate.md)|Используйте свойства, если это уместно|  
|[CA1025](../Topic/CA1025:%20Replace%20repetitive%20arguments%20with%20params%20array.md)|Замените повторяющиеся аргументы массивом параметров|  
|[CA1026](../Topic/CA1026:%20Default%20parameters%20should%20not%20be%20used.md)|Не следует использовать параметры по умолчанию|  
|[CA1027](../code-quality/ca1027-mark-enums-with-flagsattribute.md)|Следует помечать перечисления атрибутом FlagsAttribute|  
|[CA1028](../code-quality/ca1028-enum-storage-should-be-int32.md)|Хранилище перечисляемых типов должно относиться к типу Int32|  
|[CA1030](../Topic/CA1030:%20Use%20events%20where%20appropriate.md)|Используйте события, если это уместно|  
|[CA1031](../Topic/CA1031:%20Do%20not%20catch%20general%20exception%20types.md)|Не перехватывайте типы общих исключений|  
|[CA1032](../code-quality/ca1032-implement-standard-exception-constructors.md)|Реализуйте стандартные конструкторы исключения|  
|[CA1034](../code-quality/ca1034-nested-types-should-not-be-visible.md)|Вложенные типы не должны быть видимыми|  
|[CA1035](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)|В составе реализаций ICollection есть строго типизированные элементы|  
|[CA1036](../code-quality/ca1036-override-methods-on-comparable-types.md)|Переопределите методы в сопоставимых типах|  
|[CA1038](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)|Перечислители должны быть строго типизированы|  
|[CA1039](../code-quality/ca1039-lists-are-strongly-typed.md)|Списки обладают строгой типизацией|  
|[CA1041](../Topic/CA1041:%20Provide%20ObsoleteAttribute%20message.md)|Укажите сообщение ObsoleteAttribute|  
|[CA1043](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)|Используйте целый или строковый аргумент для индексаторов|  
|[CA1044](../code-quality/ca1044-properties-should-not-be-write-only.md)|Свойства не должны быть доступны только на запись|  
|[CA1046](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)|Не перегружайте оператор равенства для ссылочных типов|  
|[CA1047](../code-quality/ca1047-do-not-declare-protected-members-in-sealed-types.md)|Не объявляйте защищенные члены в запечатанных типах|  
|[CA1048](../code-quality/ca1048-do-not-declare-virtual-members-in-sealed-types.md)|Не объявляйте виртуальные члены в запечатанных типах|  
|[CA1050](../code-quality/ca1050-declare-types-in-namespaces.md)|Объявляйте типы в пространствах имен|  
|[CA1051](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)|Не объявляйте видимые поля экземпляров|  
|[CA1052](../code-quality/ca1052-static-holder-types-should-be-sealed.md)|Типы со статическими заполнителями должны быть запечатаны|  
|[CA1053](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)|Типы со статическими заполнителями не должны иметь конструкторов|  
|[CA1054](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)|Параметры URI не должны быть строками|  
|[CA1055](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)|Возвращаемые значения URI не должны быть строками|  
|[CA1056](../code-quality/ca1056-uri-properties-should-not-be-strings.md)|Свойства URI не должны быть строками|  
|[CA1057](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)|Перегрузки строковых параметров URI вызывают перегрузки System.Uri|  
|[CA1058](../code-quality/ca1058-types-should-not-extend-certain-base-types.md)|Типы не должны расширять определенные базовые типы|  
|[CA1059](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)|Члены не должны предоставлять определенные конкретные типы|  
|[CA1064](../Topic/CA1064:%20Exceptions%20should%20be%20public.md)|Исключения должны быть общими|  
|[CA1500](../Topic/CA1500:%20Variable%20names%20should%20not%20match%20field%20names.md)|Имена переменных не должны совпадать с именами полей|  
|[CA1502](../code-quality/ca1502-avoid-excessive-complexity.md)|Избегайте чрезмерной сложности|  
|[CA1708](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)|Идентификаторы должны отличаться не только регистром|  
|[CA1716](../code-quality/ca1716-identifiers-should-not-match-keywords.md)|Идентификаторы не должны совпадать с ключевыми словами|  
|[CA1801](../Topic/CA1801:%20Review%20unused%20parameters.md)|Проверьте неиспользуемые параметры|  
|[CA1804](../code-quality/ca1804-remove-unused-locals.md)|Удалите неиспользуемые локальные переменные|  
|[CA1809](../code-quality/ca1809-avoid-excessive-locals.md)|Избегайте чрезмерного использования локальных переменных|  
|[CA1810](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)|Инициализируйте статические поля ссылочного типа встроенными средствами|  
|[CA1811](../code-quality/ca1811-avoid-uncalled-private-code.md)|Избегайте невызываемый закрытый код|  
|[CA1812](../Topic/CA1812:%20Avoid%20uninstantiated%20internal%20classes.md)|Избегайте неиспользуемых внутренних классов|  
|[CA1813](../code-quality/ca1813-avoid-unsealed-attributes.md)|Избегайте распечатанных атрибутов|  
|[CA1814](../code-quality/ca1814-prefer-jagged-arrays-over-multidimensional.md)|Используйте ступенчатые массивы вместо многомерных|  
|[CA1815](../Topic/CA1815:%20Override%20equals%20and%20operator%20equals%20on%20value%20types.md)|Следует переопределять равенства и операторы равенства в типах значений|  
|[CA1819](../code-quality/ca1819-properties-should-not-return-arrays.md)|Свойства не должны возвращать массивы|  
|[CA1820](../code-quality/ca1820-test-for-empty-strings-using-string-length.md)|Проверьте наличие пустых строк путем проверки длины строки|  
|[CA1822](../Topic/CA1822:%20Mark%20members%20as%20static.md)|Помечайте члены как статические|  
|[CA1823](../code-quality/ca1823-avoid-unused-private-fields.md)|Избегайте неиспользованных закрытых полей|  
|[CA2201](../code-quality/ca2201-do-not-raise-reserved-exception-types.md)|Не вызывайте зарезервированные типы исключений|  
|[CA2205](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)|Используйте управляемые эквиваленты API Win32|  
|[CA2208](../code-quality/ca2208-instantiate-argument-exceptions-correctly.md)|Правильно создавайте экземпляры исключений аргументов|  
|[CA2211](../code-quality/ca2211-non-constant-fields-should-not-be-visible.md)|Поля, не являющиеся константами, не должны быть видимыми|  
|[CA2217](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)|Не помечайте перечисления атрибутом FlagsAttribute|  
|[CA2219](../Topic/CA2219:%20Do%20not%20raise%20exceptions%20in%20exception%20clauses.md)|Не создавайте исключения в предложениях исключений|  
|[CA2221](../code-quality/ca2221-finalizers-should-be-protected.md)|Методы завершения должны быть защищены|  
|[CA2222](../code-quality/ca2222-do-not-decrease-inherited-member-visibility.md)|Не уменьшайте видимость унаследованных членов|  
|[CA2223](../Topic/CA2223:%20Members%20should%20differ%20by%20more%20than%20return%20type.md)|Члены должны различаться не только возвращаемым типом|  
|[CA2224](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)|Переопределите равенство при перегрузке оператора равенства|  
|[CA2225](../Topic/CA2225:%20Operator%20overloads%20have%20named%20alternates.md)|Для перезагрузок оператора существуют дополнения с именами|  
|[CA2226](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)|Перегрузки операторов должны быть симметричны|  
|[CA2227](../code-quality/ca2227-collection-properties-should-be-read-only.md)|Свойства коллекции должны иметь параметр "только для чтения"|  
|[CA2230](../code-quality/ca2230-use-params-for-variable-arguments.md)|Используйте params для переменного количества аргументов|  
|[CA2234](../Topic/CA2234:%20Pass%20System.Uri%20objects%20instead%20of%20strings.md)|Передавайте объекты System.Uri вместо строк|  
|[CA2239](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)|Предоставьте методы десериализации для необязательных полей|  
|[CA1020](../code-quality/ca1020-avoid-namespaces-with-few-types.md)|Не используйте пространства имен с несколькими типами|  
|[CA1021](../code-quality/ca1021-avoid-out-parameters.md)|Не используйте параметры out|  
|[CA1040](../Topic/CA1040:%20Avoid%20empty%20interfaces.md)|Избегайте пустых интерфейсов|  
|[CA1045](../code-quality/ca1045-do-not-pass-types-by-reference.md)|Не передавайте типы по ссылке|  
|[CA1062](../code-quality/ca1062-validate-arguments-of-public-methods.md)|Проверьте аргументы открытых методов|  
|[CA1501](../code-quality/ca1501-avoid-excessive-inheritance.md)|Избегайте излишнего наследования|  
|[CA1504](../code-quality/ca1504-review-misleading-field-names.md)|Проверьте имена полей, которые могут ввести в заблуждение|  
|[CA1505](../Topic/CA1505:%20Avoid%20unmaintainable%20code.md)|Избегайте кода, неудобного для поддержки|  
|[CA1506](../code-quality/ca1506-avoid-excessive-class-coupling.md)|Избегайте чрезмерной связи классов|  
|[CA1700](../code-quality/ca1700-do-not-name-enum-values-reserved.md)|Не следует называть значения перечислений именем "Reserved"|  
|[CA1701](../Topic/CA1701:%20Resource%20string%20compound%20words%20should%20be%20cased%20correctly.md)|Соблюдайте правильность регистра в составных словах строк ресурса|  
|[CA1702](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)|Для сложных слов следует использовать правильный регистр|  
|[CA1703](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)|Соблюдайте правильность написания строк ресурсов|  
|[CA1704](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)|Идентификаторы должны иметь правильное написание|  
|[CA1707](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)|Идентификаторы не должны содержать знак подчеркивания|  
|[CA1709](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)|Идентификаторы должны иметь правильный регистр|  
|[CA1710](../Topic/CA1710:%20Identifiers%20should%20have%20correct%20suffix.md)|Идентификаторы должны иметь правильные суффиксы|  
|[CA1711](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)|Идентификаторы не должны иметь неверных суффиксов|  
|[CA1712](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)|Не добавляйте имя типа перед перечисляемыми значениями|  
|[CA1713](../code-quality/ca1713-events-should-not-have-before-or-after-prefix.md)|Имена событий не должны содержать префикс "before" или "after"|  
|[CA1714](../code-quality/ca1714-flags-enums-should-have-plural-names.md)|Имена перечислений флагов должны быть во множественном числе|  
|[CA1715](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)|Идентификаторы должны иметь правильные префиксы|  
|[CA1717](../Topic/CA1717:%20Only%20FlagsAttribute%20enums%20should%20have%20plural%20names.md)|Только перечисления FlagsAttribute должны иметь имена во множественном числе|  
|[CA1719](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)|Имена параметров не должны совпадать с именами членов|  
|[CA1720](../code-quality/ca1720-identifiers-should-not-contain-type-names.md)|Идентификаторы не должны содержать имен типов|  
|[CA1721](../code-quality/ca1721-property-names-should-not-match-get-methods.md)|Имена свойств не должны совпадать с именами методов get|  
|[CA1722](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md)|Идентификаторы не должны иметь неверные префиксы|  
|[CA1724](../code-quality/ca1724-type-names-should-not-match-namespaces.md)|Имена типов не должны совпадать с именами пространства имен|  
|[CA1725](../code-quality/ca1725-parameter-names-should-match-base-declaration.md)|Имена параметров должны соответствовать базовому объявлению|  
|[CA1726](../code-quality/ca1726-use-preferred-terms.md)|Используйте предпочтительные термины|  
|[CA2204](../code-quality/ca2204-literals-should-be-spelled-correctly.md)|Литералы должны иметь правильное написание|