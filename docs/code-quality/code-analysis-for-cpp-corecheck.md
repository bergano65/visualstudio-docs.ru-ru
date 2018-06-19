---
title: Средство проверки готовности рекомендации Справочник по Visual Studio C++ Core
ms.date: 03/22/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
helpviewer_keywords:
- code analysis, C++ core check
ms.assetid: f1429463-136e-41ed-8a75-a8dbf0b4fd89
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: 09abcf8b1ece1360056a479df568db3a4e569ff1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31917021"
---
# <a name="c-core-guidelines-checker-reference"></a>Справочные материалы по Проверка правила C++ основной

В этом разделе перечислены предупреждения C++ основные правила проверки. Сведения об анализе кода см. в разделе [/ analyze (анализ кода)](/cpp/build/reference/analyze-code-analysis) и [быстрый запуск: анализ кода для C/C++](../code-quality/quick-start-code-analysis-for-c-cpp.md).

> [!NOTE]
> Некоторые предупреждения относятся к более чем в одной группе, и не все предупреждения имеют полный справочном разделе.

## <a name="ownerpointer-group"></a>OWNER_POINTER группы

[C26402 DONT_HEAP_ALLOCATE_MOVABLE_RESULT](C26402.md) вернуть области объекта вместо размещенных в куче, если он имеет конструктор перемещения. В разделе [C++ основные рекомендации R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26403 RESET_OR_DELETE_OWNER](C26403.md) сброса или явно удалить владельца\<T > указатель «% переменная %». В разделе [C++ основные рекомендации R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26404 DONT_DELETE_INVALID](C26404.md) не удалить владельца\<T >, которые могут быть в недопустимом состоянии. В разделе [C++ основные рекомендации R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26405 DONT_ASSIGN_TO_VALID](C26405.md) владелец не назначается\<T >, которые могут быть в допустимом состоянии. В разделе [C++ основные рекомендации R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26406 DONT_ASSIGN_RAW_TO_OWNER](C26406.md) не назначается необработанный указатель владельца\<T >. В разделе [C++ основные рекомендации R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26407 DONT_HEAP_ALLOCATE_UNNECESSARILY](C26407.md) предпочтение объектов с областью, не кучи выделите без необходимости. В разделе [C++ основные рекомендации R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).

[C26429 USE_NOTNULL](C26429.md) символ «% символ» никогда не проверяется на наличие nullness, он может быть помечен как not_null. В разделе [C++ основные рекомендации F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26430 TEST_ON_ALL_PATHS](C26430.md) символ «% символ» не проверяется на наличие nullness во всех путях. В разделе [C++ основные рекомендации F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26431 DONT_TEST_NOTNULL](C26431.md) уже gsl::not_null тип выражения «% expr». Не выполняйте проверку его для nullness. В разделе [C++ основные рекомендации F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

## <a name="rawpointer-group"></a>RAW_POINTER группы

[C26400 NO_RAW_POINTER_ASSIGNMENT](c26400.md) не присвоить результат выделение или вызов функции с владельцем\<T > возвращаемое значение к указателю необработанные; используйте владельца\<T > вместо. В разделе [C++ основные рекомендации I.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw).

[C26401 DONT_DELETE_NON_OWNER](c26401.md) не удалить исходный указатель, который не является владельцем\<T >. В разделе [C++ основные рекомендации I.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw).

[C26402 DONT_HEAP_ALLOCATE_MOVABLE_RESULT](C26402.md)   вернуть области объекта вместо размещенных в куче, если он имеет конструктор перемещения. В разделе [C++ основные рекомендации R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26408 NO_MALLOC_FREE](C26408.md) избежать malloc() и free(), предпочтительно версии nothrow возможности удаления. В разделе [C++ основные рекомендации R.10](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-mallocfree).

[C26409 NO_NEW_DELETE](C26409.md) Избегайте вызова новые и удалить явно, используйте std::make_unique\<T > вместо него. В разделе [C++ основные рекомендации R.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-newdelete).

[C26429 USE_NOTNULL](C26429.md) символ «% символ» никогда не проверяется на наличие nullness, он может быть помечен как not_null. В разделе [C++ основные рекомендации F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26430 TEST_ON_ALL_PATHS](C26430.md) символ «% символ» не проверяется на наличие nullness во всех путях. В разделе [C++ основные рекомендации F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26431 DONT_TEST_NOTNULL](C26431.md) уже gsl::not_null тип выражения «% expr». Не выполняйте проверку его для nullness. В разделе [C++ основные рекомендации F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26481 NO_POINTER_ARITHMETIC](C26481.md) не используйте арифметических операций над указателями. Вместо этого используйте диапазон. В разделе [Bounds.1 правила C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).

[C26485 NO_ARRAY_TO_POINTER_DECAY](C26485.md).
Выражение «% expr»: нет массива критичной указателя. В разделе [Bounds.3 правила C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).

## <a name="uniquepointer-group"></a>UNIQUE_POINTER группы

[C26410 NO_REF_TO_CONST_UNIQUE_PTR](C26410.md) параметр «% параметр %» является ссылкой на `const` уникальный указатель const T * или const T &. В разделе [C++ основные рекомендации R.32](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-uniqueptrparam).

[C26411 NO_REF_TO_UNIQUE_PTR](C26411.md) параметр «% параметр %» является ссылкой на уникальный указатель, и никогда не переназначении или сбросе, используйте T * или T &. В разделе [C++ основные рекомендации R.33](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-reseat).

[C26414 RESET_LOCAL_SMART_PTR](C26414.md) перемещения, копирования, переназначить или сбросить локального смарт-указатель «% символ». В разделе [C++ основные рекомендации R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).

[C26415 SMART_PTR_NOT_NEEDED](C26415.md) интеллектуального указателя параметр «% символ» используется только для доступа к автономной указателя. Используйте T * или T &. В разделе [C++ основные рекомендации R.30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam).

## <a name="sharedpointer-group"></a>SHARED_POINTER группы

[C26414 RESET_LOCAL_SMART_PTR](C26414.md) перемещения, копирования, переназначить или сбросить локального смарт-указатель «% символ». В разделе [C++ основные рекомендации R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).

[C26415 SMART_PTR_NOT_NEEDED](C26415.md) интеллектуального указателя параметр «% символ» используется только для доступа к автономной указателя. Используйте T * или T &. В разделе [C++ основные рекомендации R.30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam).

[C26416 NO_RVALUE_REF_SHARED_PTR](C26416.md) общий параметр-указатель «% символ» передается по ссылке rvalue. Вместо передачи по значению. В разделе [C++ основные рекомендации R.34](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-owner).

[C26417 NO_LVALUE_REF_SHARED_PTR](C26417.md) общий параметр-указатель «% символ» передается по ссылке и не сброса или переназначить. Используйте T * или T &. В разделе [C++ основные рекомендации R.35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam).

[C26418 NO_VALUE_OR_CONST_REF_SHARED_PTR](C26418.md) общий параметр-указатель «% символ» не копируется или перемещается. Используйте T * или T &. В разделе [C++ основные рекомендации R.36](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-const).

## <a name="declaration-group"></a>ОБЪЯВЛЕНИЕ группы

[C26426 NO_GLOBAL_INIT_CALLS](C26426.md) глобальный инициализатор вызывает функцию, не являющийся constexpr '% символ». В разделе [C++ основные рекомендации I.22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects).

[C26427 NO_GLOBAL_INIT_EXTERNS](C26427.md) глобальный инициализатор обращается к объекту extern «% символ». В разделе [C++ основные рекомендации I.22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects).

[C26444 NO_UNNAMED_RAII_OBJECTS](c26444.md) Избегайте неименованные объектов, содержащих пользовательские построения и удаления. В разделе [ES.84: (старайтесь) объявить локальную переменную без имени](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).

## <a name="class-group"></a>Класс группы

[C26432 DEFINE_OR_DELETE_SPECIAL_OPS](C26432.md) при определении или удалить все операции по умолчанию в типе «% символ», определение или удалите их все. В разделе [C++ основные рекомендации C.21](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c21-if-you-define-or-delete-any-default-operation-define-or-delete-them-all).

[C26433 OVERRIDE_EXPLICITLY](c26433.md) функции «% символ» должен быть помечен как «override». В разделе [C.128: виртуальные функции следует указывать только один виртуальный, переопределения или последний](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c128-virtual-functions-should-specify-exactly-one-of-virtual-override-or-final).

[C26434 DONT_HIDE_METHODS](C26434.md) функция «% symbol_1» скрывает невиртуальной функции «% symbol_2%». В разделе [C++ основные рекомендации C.128](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c128-virtual-functions-should-specify-exactly-one-of-virtual-override-or-final).

[C26435 SINGLE_VIRTUAL_SPECIFICATION](c26435.md) функции «% символ» следует указать только один из «virtual», «override» или «final». В разделе [C.128: виртуальные функции следует указывать только один виртуальный, переопределения или последний](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).


[C26436 NEED_VIRTUAL_DTOR](C26436.md) тип «% % символ» виртуальная функция, должен либо открытый виртуальных и защищенных невиртуальный деструктор. В разделе [C++ основные рекомендации C.35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c35-a-base-class-destructor-should-be-either-public-and-virtual-or-protected-and-nonvirtual).


[C26443 NO_EXPLICIT_DTOR_OVERRIDE](c26443.md) переопределение деструктор не следует использовать явное «override» и «virtual» описателей. В разделе [C.128: виртуальные функции следует указывать только один виртуальный, переопределения или последний](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).


## <a name="type-group"></a>Тип группы

[C26437 DONT_SLICE](C26437.md) не среза. В разделе [C++ основные рекомендации ES.63](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es63-dont-slice).

## <a name="style-group"></a>СТИЛЬ группы

[C26438 NO_GOTO](C26438.md) избежать `goto`. В разделе [C++ основные рекомендации ES.76](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es76-avoid-goto).

## <a name="function-group"></a>Группа ФУНКЦИЙ

[C26439 SPECIAL_NOEXCEPT](C26439.md) этого вида функции не может вызвать исключение. Он объявляется `noexcept`. В разделе [C++ основные рекомендации F.6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).

[C26440 DECLARE_NOEXCEPT](C26440.md) можно объявить функцию «% символ» `noexcept`. В разделе [C++ основные рекомендации F.6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).

[C26447 DONT_THROW_IN_NOEXCEPT](c26447.md) функция объявлена **noexcept** , но вызывает функцию, который может выдавать исключения.
В разделе [основные правила C++: F.6: Если функция не может создавать, объявите его noexcept](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).

## <a name="concurrency-group"></a>Группы с ПАРАЛЛЕЛИЗМОМ

[C26441 NO_UNNAMED_GUARDS](C26441.md) Guard объекты должны иметь имена. В разделе [C++ основные рекомендации cp.44](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#cp44-remember-to-name-your-lock_guards-and-unique_locks).

## <a name="const-group"></a>CONST группы

[C26460 USE_CONST_REFERENCE_ARGUMENTS](c26460.md) ссылочный аргумент «% аргумента %» для функции «% функции» может быть помечен как `const`. В разделе [C++ основные рекомендации con.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref).

[C26461 USE_CONST_POINTER_ARGUMENTS](c26461.md): аргумент указателя «% аргумента %» для функции «% функции» может быть помечен как указатель на `const`. В разделе [C++ основные рекомендации con.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref).

[C26462 USE_CONST_POINTER_FOR_VARIABLE](c26462.md) только один раз присваивается значение, на который указывает «% переменная %», пометьте его как указатель на `const`. В разделе [C++ основные рекомендации con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26463 USE_CONST_FOR_ELEMENTS](c26463.md) элементы массива «% массива» назначаются только один раз, элементы пометить `const`. В разделе [C++ основные рекомендации con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26464 USE_CONST_POINTER_FOR_ELEMENTS](c26464.md) значения, на который указывает элементы массива «% массива» назначаются только один раз, элементы пометить как указатель на `const`. В разделе [C++ основные рекомендации con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26496 USE_CONST_FOR_VARIABLE](c26496.md) переменной «% переменная %» присваивается только один раз, пометьте его как `const`. В разделе [C++ основные рекомендации con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26497 USE_CONSTEXPR_FOR_FUNCTION](c26497.md) этой функции % функции могут быть помечены `constexpr` при необходимости вычисление во время компиляции. В разделе [C++ основные рекомендации F.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rf-constexpr).

[C26498 USE_CONSTEXPR_FOR_FUNCTIONCALL](c26498.md) можно использовать функции % % этот вызов функции `constexpr` при необходимости вычисление во время компиляции. В разделе [C++ основные рекомендации con.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-constexpr).

## <a name="type-group"></a>Тип группы

[C26465 NO_CONST_CAST_UNNECESSARY](c26465.md) не используют `const_cast` для снятия `const`. `const_cast` не является обязательным. потерей постоянства или неустойчивости не удаляется с этого преобразования. В разделе [Type.3 правила C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-constcast).

[C26466 NO_STATIC_DOWNCAST_POLYMORPHIC](c26466.md) не используют `static_cast` downcasts. Приведение из полиморфного типа следует использовать dynamic_cast. В разделе [Type.2 правила C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-downcast).

[C26471 NO_REINTERPRET_CAST_FROM_VOID_PTR](c26471.md) не используют `reinterpret_cast`. Можно использовать приведение из void * `static_cast`. В разделе [Type.1 правила C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26472 NO_CASTS_FOR_ARITHMETIC_CONVERSION](C26472.md) не используют `static_cast` преобразования. Использование фигурных скобок, gsl::narrow_cast или gsl::narow. В разделе [Type.1 правила C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26473 NO_IDENTITY_CAST](C26473.md) не приведения между типами указателей, где тип источника и целевого типа совпадают. В разделе [Type.1 правила C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26474 NO_IMPLICIT_CAST](C26474.md) не приведения между типами указателей, если может иметь неявное преобразование. В разделе [Type.1 правила C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26475 NO_FUNCTION_STYLE_CASTS](C26475.md) не используется функция стиль приведения типов C. В разделе [C++ основные рекомендации ES.49](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es49-if-you-must-use-a-cast-use-a-named-cast).

[C26490 NO_REINTERPRET_CAST](c26490.md) не используют `reinterpret_cast`. В разделе [Type.1 правила C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26491 NO_STATIC_DOWNCAST](c26490.md) не используют `static_cast` downcasts. В разделе [Type.2 правила C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26492 NO_CONST_CAST](c26492.md) не используют `const_cast` для снятия `const`. В разделе [Type.3 правила C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26493 NO_CSTYLE_CAST](c26493.md) не используйте C-стиль приведения. В разделе [Type.4 правила C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26494 VAR_USE_BEFORE_INIT](c26494.md) переменной «% переменная %» не инициализирован. Всегда Инициализируйте объект. В разделе [Type.5 правила C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26495 MEMBER_UNINIT](c26495.md) переменной «% переменная %» не инициализирован. Всегда инициализируйте переменную-член. В разделе [Type.6 правила C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

## <a name="bounds-group"></a>Группы ГРАНИЦ

[C26446 USE_GSL_AT](c26446.md) предпочитают использовать `gsl::at()` вместо unchecked оператор индекса. В разделе [C++ основные рекомендации: Bounds.4: не используйте Стандартная библиотека функций и типов, которые не являются контролем границ](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile).

[C26481 NO_POINTER_ARITHMETIC](C26481.md).
Не используйте арифметических операций над указателями. Вместо этого используйте диапазон. В разделе [Bounds.1 C++ основные рекомендации](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26482 NO_DYNAMIC_ARRAY_INDEXING](c26482.md) индексировать только в массивы, с помощью константных выражений. В разделе [Bounds.2 C++ основные рекомендации](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26483 STATIC_INDEX_OUT_OF_RANGE](c26483.md) значение % значение находится за пределами (0, привязанные %) переменной «% переменная %». Только индексы массивов с помощью константными выражениями, которые находятся в пределах границ массива. В разделе [Bounds.2 C++ основные рекомендации](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26485 NO_ARRAY_TO_POINTER_DECAY](C26485.md) выражение «% expr»: нет массива критичной указателя. В разделе [Bounds.3 C++ основные рекомендации](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

## <a name="gsl-group"></a>GSL группы

[C26445 NO_SPAN_REF](c26445.md) ссылку на `gsl::span` или `std::string_view` может означать наличие проблемы времени существования.
В разделе [GSL.view C++ основные рекомендации: представлений](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#gslview-views)

[C26446 USE_GSL_AT](c26446.md) предпочитают использовать `gsl::at()` вместо unchecked оператор индекса. В разделе [C++ основные рекомендации: Bounds.4: не используйте Стандартная библиотека функций и типов, которые не являются контролем границ](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile).

[C26448 USE_GSL_FINALLY ](c26448.md) рекомендуется использовать `gsl::finally` Если финальное действие будет выполняться. В разделе [C++ основные рекомендации: GSL.util: служебные программы](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-utilities).

[C26449 NO_SPAN_FROM_TEMPORARY](c26449.md) 
 `gsl::span` или `std::string_view` создан из временного станет недействительным при временный становится недействительным. В разделе [C++ основные рекомендации: GSL.view: представлений](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#gslview-views).


## <a name="deprecated-warnings"></a>Устаревшие предупреждения

Следующие предупреждения присутствуют в набор раннее экспериментальный правило проверки правила основных компонентов, но теперь считается устаревшим и можно спокойно проигнорировать. Предупреждения заменяются предупреждения из приведенного выше списка.

- 26412 DEREF_INVALID_POINTER
- 26413 DEREF_NULLPTR
- 26420 ASSIGN_NONOWNER_TO_EXPLICIT_OWNER
- 26421 ASSIGN_VALID_OWNER
- 26422 VALID_OWNER_LEAVING_SCOPE
- 26423 ALLOCATION_NOT_ASSIGNED_TO_OWNER
- 26424 VALID_ALLOCATION_LEAVING_SCOPE
- 26425 ASSIGNING_TO_STATIC
- 26499 NO_LIFETIME_TRACKING

## <a name="see-also"></a>См. также
[С помощью средства проверки правила C++ Core](using-the-cpp-core-guidelines-checkers.md)
