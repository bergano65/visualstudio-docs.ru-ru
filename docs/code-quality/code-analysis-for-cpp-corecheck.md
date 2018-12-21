---
title: Ссылка проверки C++ Core Guidelines
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
ms.openlocfilehash: c11386dcd742e64737a4b06f2db9f55145f535d7
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/07/2018
ms.locfileid: "53053390"
---
# <a name="c-core-guidelines-checker-reference"></a>Ссылка проверки C++ Core Guidelines

В этом разделе перечислены предупреждения проверки правила C++ Core. Сведения об анализе кода см. в разделе [/ analyze (анализ кода)](/cpp/build/reference/analyze-code-analysis) и [краткое руководство: анализ кода для C/C++](../code-quality/quick-start-code-analysis-for-c-cpp.md).

> [!NOTE]
> Некоторые предупреждения относятся к более чем одной группе, и не все предупреждения имеют полный справочник.

## <a name="ownerpointer-group"></a>OWNER_POINTER группы

[C26402 DONT_HEAP_ALLOCATE_MOVABLE_RESULT](C26402.md) при наличии конструктора перемещения должен возвращаться объект области, а не выделяемый в куче. См. в разделе [C++ Core Guidelines R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26403 RESET_OR_DELETE_OWNER](C26403.md) сбросьте или явно удалить владельца\<T > указатель «% variable %». См. в разделе [C++ Core Guidelines R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26404 DONT_DELETE_INVALID](C26404.md) не удаляйте объект owner\<T >, может быть в недопустимом состоянии. См. в разделе [C++ Core Guidelines R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26405 DONT_ASSIGN_TO_VALID](C26405.md) не присваивайте значение объекту owner\<T >, может быть в допустимом состоянии. См. в разделе [C++ Core Guidelines R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26406 DONT_ASSIGN_RAW_TO_OWNER](C26406.md) не присваивайте необработанный указатель объекту Owner\<T >. См. в разделе [C++ Core Guidelines R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26407 DONT_HEAP_ALLOCATE_UNNECESSARILY](C26407.md) предпочитать объектам, не кучи выделить без необходимости. См. в разделе [C++ Core Guidelines R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).

[C26429 USE_NOTNULL](C26429.md) символ «% символа %» никогда не проверяется наличия значений NULL, он может быть помечен как not_null. См. в разделе [C++ Core Guidelines F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26430 TEST_ON_ALL_PATHS](C26430.md) символ «% символа %» не прошла проверку наличия значений NULL во всех путях. См. в разделе [C++ Core Guidelines F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26431 DONT_TEST_NOTNULL](C26431.md) тип выражения «% % expr» уже gsl::not_null. Не проверяйте его на NULL. См. в разделе [C++ Core Guidelines F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

## <a name="rawpointer-group"></a>RAW_POINTER группы

[C26400 NO_RAW_POINTER_ASSIGNMENT](c26400.md) не присваивайте результат выделения или вызова функции с владельцем\<T > возвращаемого значения на необработанный указатель; используйте owner\<T > вместо этого. См. в разделе [C++ Core Guidelines I.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw).

[C26401 DONT_DELETE_NON_OWNER](c26401.md) не удаляйте необработанный указатель, который не является владельцем\<T >. См. в разделе [C++ Core Guidelines I.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw).

[C26402 DONT_HEAP_ALLOCATE_MOVABLE_RESULT](C26402.md)   при наличии конструктора перемещения должен возвращаться объект области, а не выделяемый в куче. См. в разделе [C++ Core Guidelines R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26408 NO_MALLOC_FREE](C26408.md) избежать malloc() и free(), предпочитать nothrow версию new с delete. См. в разделе [C++ Core Guidelines R.10](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-mallocfree).

[C26409 NO_NEW_DELETE](C26409.md) Избегайте вызова новых и удалять явно, используйте std::make_unique\<T > вместо этого. См. в разделе [C++ Core Guidelines R.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-newdelete).

[C26429 USE_NOTNULL](C26429.md) символ «% символа %» никогда не проверяется наличия значений NULL, он может быть помечен как not_null. См. в разделе [C++ Core Guidelines F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26430 TEST_ON_ALL_PATHS](C26430.md) символ «% символа %» не прошла проверку наличия значений NULL во всех путях. См. в разделе [C++ Core Guidelines F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26431 DONT_TEST_NOTNULL](C26431.md) тип выражения «% % expr» уже gsl::not_null. Не проверяйте его на NULL. См. в разделе [C++ Core Guidelines F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26481 NO_POINTER_ARITHMETIC](C26481.md) не используйте арифметику указателей. Вместо этого используйте диапазон. См. в разделе [Bounds.1 правила C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).

[C26485 NO_ARRAY_TO_POINTER_DECAY](C26485.md).
Выражение «% expr %»: массива в указатель затухания. См. в разделе [Bounds.3 правила C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).

## <a name="uniquepointer-group"></a>UNIQUE_POINTER группы

[C26410 NO_REF_TO_CONST_UNIQUE_PTR](C26410.md) параметра «% параметром %» является ссылкой на `const` уникальный указатель const T * или const T &. См. в разделе [C++ Core Guidelines R.32](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-uniqueptrparam).

[C26411 NO_REF_TO_UNIQUE_PTR](C26411.md) параметр «% параметром %» — это ссылка на уникальный указатель, и он никогда не переназначении или сбросе, используйте T * или T &. См. в разделе [C++ Core Guidelines R.33](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-reseat).

[C26414 RESET_LOCAL_SMART_PTR](C26414.md) перемещения, копирования, переназначьте или сбросьте локальный смарт-указатель «% символа %». См. в разделе [C++ Core Guidelines R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).

[C26415 SMART_PTR_NOT_NEEDED](C26415.md) интеллектуального указателя параметра «% символа %» используется только для доступа к автономной указатель. Используйте T * или T &. См. в разделе [C++ Core Guidelines R.30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam).

## <a name="sharedpointer-group"></a>SHARED_POINTER группы

[C26414 RESET_LOCAL_SMART_PTR](C26414.md) перемещения, копирования, переназначьте или сбросьте локальный смарт-указатель «% символа %». См. в разделе [C++ Core Guidelines R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).

[C26415 SMART_PTR_NOT_NEEDED](C26415.md) интеллектуального указателя параметра «% символа %» используется только для доступа к автономной указатель. Используйте T * или T &. См. в разделе [C++ Core Guidelines R.30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam).

[C26416 NO_RVALUE_REF_SHARED_PTR](C26416.md) параметр общего указателя «% символа %» передается по ссылке rvalue. Вместо передачи по значению. См. в разделе [C++ Core Guidelines R.34](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-owner).

[C26417 NO_LVALUE_REF_SHARED_PTR](C26417.md) параметр общего указателя «% символа %» передается по ссылке и не сбрасывается или переназначить. Используйте T * или T &. См. в разделе [C++ Core Guidelines R.35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam).

[C26418 NO_VALUE_OR_CONST_REF_SHARED_PTR](C26418.md) параметр общего указателя «% символа %» не копируется или перемещается. Используйте T * или T &. См. в разделе [C++ Core Guidelines R.36](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-const).

## <a name="declaration-group"></a>ОБЪЯВЛЕНИЕ группы

[C26426 NO_GLOBAL_INIT_CALLS](C26426.md) глобальный инициализатор вызывает функцию, не являющийся constexpr «% символа %». См. в разделе [C++ Core Guidelines I.22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects).

[C26427 NO_GLOBAL_INIT_EXTERNS](C26427.md) глобальный инициализатор обращается к внешнему объекту «% символа %». См. в разделе [C++ Core Guidelines I.22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects).

[C26444 NO_UNNAMED_RAII_OBJECTS](c26444.md) Избегайте безымянные объекты с настраиваемым созданием и уничтожением. См. в разделе [ES.84: не (повторите) объявите локальную переменную без имени](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).

## <a name="class-group"></a>Класс группы

[C26432 DEFINE_OR_DELETE_SPECIAL_OPS](C26432.md) Если вы определяете или удаляете любую операцию по умолчанию в типе «% символа %», определите или удалите их все. См. в разделе [C++ Core Guidelines C.21](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c21-if-you-define-or-delete-any-default-operation-define-or-delete-them-all).

[C26433 OVERRIDE_EXPLICITLY](c26433.md) функции «% символа %» должны быть помечены как «override». См. в разделе [C.128: виртуальные функции следует указать только один виртуальный, переопределение или окончательный](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c128-virtual-functions-should-specify-exactly-one-of-virtual-override-or-final).

[C26434 DONT_HIDE_METHODS](C26434.md) функции «% symbol_1%» скрывает невиртуальную функцию «% symbol_2%». См. в разделе [C++ Core Guidelines C.128](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c128-virtual-functions-should-specify-exactly-one-of-virtual-override-or-final).

[C26435 SINGLE_VIRTUAL_SPECIFICATION](c26435.md) функции «% символа %» следует указать только один из «virtual», «override» или «final». См. в разделе [C.128: виртуальные функции следует указать только один виртуальный, переопределение или окончательный](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).


[C26436 NEED_VIRTUAL_DTOR](C26436.md) тип «% % символ» с виртуальной функцией должен либо открытый виртуальный или защищенный невиртуальный деструктор. См. в разделе [C++ Core Guidelines C.35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c35-a-base-class-destructor-should-be-either-public-and-virtual-or-protected-and-nonvirtual).


[C26443 NO_EXPLICIT_DTOR_OVERRIDE](c26443.md) подмена деструктор не следует использовать явные указатели «override» или «virtual» описателей. См. в разделе [C.128: виртуальные функции следует указать только один виртуальный, переопределение или окончательный](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).


## <a name="type-group"></a>Тип группы

[C26437 DONT_SLICE](C26437.md) не используйте срезы. См. в разделе [C++ Core Guidelines ES.63](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es63-dont-slice).

## <a name="style-group"></a>Группе "СТИЛЬ"

[C26438 NO_GOTO](C26438.md) избежать `goto`. См. в разделе [C++ Core Guidelines ES.76](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es76-avoid-goto).

## <a name="function-group"></a>Группа ФУНКЦИЙ

[C26439 SPECIAL_NOEXCEPT](C26439.md) функций этого типа не может вызвать. Объявите его `noexcept`. См. в разделе [C++ Core Guidelines F.6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).

[C26440 DECLARE_NOEXCEPT](C26440.md) могут быть объявлены функции «% символа %» `noexcept`. См. в разделе [C++ Core Guidelines F.6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).

[C26447 DONT_THROW_IN_NOEXCEPT](c26447.md) функция объявлена **noexcept** , но вызывает функцию, которая может порождать исключения.
См. в разделе [C++ Core Guidelines: F.6: Если функция не может создавать, объявите его noexcept](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).

## <a name="concurrency-group"></a>Группа ПАРАЛЛЕЛИЗМА

[C26441 NO_UNNAMED_GUARDS](C26441.md) объекты защиты должны быть именованными. См. в разделе [C++ Core рекомендации cp.44](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#cp44-remember-to-name-your-lock_guards-and-unique_locks).

## <a name="const-group"></a>CONST группы

[C26460 USE_CONST_REFERENCE_ARGUMENTS](c26460.md) ссылочный аргумент «% аргумент %» для функции «% функция %» может быть помечен как `const`. См. в разделе [C++ Core рекомендации con.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref).

[C26461 USE_CONST_POINTER_ARGUMENTS](c26461.md): аргумент указателя «% аргумент %» функции «% функция %» может быть помечен как указатель на `const`. См. в разделе [C++ Core рекомендации con.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref).

[C26462 USE_CONST_POINTER_FOR_VARIABLE](c26462.md) значение, на которые указывают «% variable %» присваивается только один раз; пометьте ее как указатель на `const`. См. в разделе [C++ Core рекомендации con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26463 USE_CONST_FOR_ELEMENTS](c26463.md) элементы массива «% массива %» назначаются только один раз; пометьте элементы `const`. См. в разделе [C++ Core рекомендации con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26464 USE_CONST_POINTER_FOR_ELEMENTS](c26464.md) , на которые указывают элементы массива «% массива %» значения присваиваются только один раз; пометьте элементы как указатель на `const`. См. в разделе [C++ Core рекомендации con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26496 USE_CONST_FOR_VARIABLE](c26496.md) переменной «% variable %» присваивается только один раз; пометьте ее как `const`. См. в разделе [C++ Core рекомендации con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26497 USE_CONSTEXPR_FOR_FUNCTION](c26497.md) этой функции % функция может быть помечена `constexpr` Если требуется вычисление во время компиляции. См. в разделе [C++ Core Guidelines F.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rf-constexpr).

[C26498 USE_CONSTEXPR_FOR_FUNCTIONCALL](c26498.md) можно использовать функции % % этот вызов функции `constexpr` Если требуется вычисление во время компиляции. См. в разделе [C++ Core рекомендации con.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-constexpr).

## <a name="type-group"></a>Тип группы

[C26465 NO_CONST_CAST_UNNECESSARY](c26465.md) не используйте `const_cast` для снятия `const`. `const_cast` не является обязательным. снимает постоянство или изменчивость не удаляется с помощью этого преобразования. См. в разделе [Type.3 правила C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-constcast).

[C26466 NO_STATIC_DOWNCAST_POLYMORPHIC](c26466.md) не используйте `static_cast` нисходящее приведение типа. Приведении полиморфного типа следует использовать dynamic_cast. См. в разделе [Type.2 правила C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-downcast).

[C26471 NO_REINTERPRET_CAST_FROM_VOID_PTR](c26471.md) не используйте `reinterpret_cast`. Можно использовать приведения из void * `static_cast`. См. в разделе [Type.1 правила C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26472 NO_CASTS_FOR_ARITHMETIC_CONVERSION](C26472.md) не используйте `static_cast` преобразования. Использование фигурных скобок, gsl::narrow_cast или gsl::narow. См. в разделе [Type.1 правила C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26473 NO_IDENTITY_CAST](C26473.md) не используйте приведение типов указателей, где тип источника и целевого типа совпадают. См. в разделе [Type.1 правила C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26474 NO_IMPLICIT_CAST](C26474.md) не используйте приведение типов указателя, если преобразование может быть неявным. См. в разделе [Type.1 правила C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26475 NO_FUNCTION_STYLE_CASTS](C26475.md) не используется функция стиль приведения C в стиле. См. в разделе [C++ Core Guidelines ES.49](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es49-if-you-must-use-a-cast-use-a-named-cast).

[C26490 NO_REINTERPRET_CAST](c26490.md) не используйте `reinterpret_cast`. См. в разделе [Type.1 правила C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26491 NO_STATIC_DOWNCAST](c26490.md) не используйте `static_cast` нисходящее приведение типа. См. в разделе [Type.2 правила C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26492 NO_CONST_CAST](c26492.md) не используйте `const_cast` для снятия `const`. См. в разделе [Type.3 правила C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26493 NO_CSTYLE_CAST](c26493.md) не используйте приведение в стиле C. См. в разделе [Type.4 правила C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26494 VAR_USE_BEFORE_INIT](c26494.md) переменная «% variable %» не инициализирована. Всегда Инициализируйте объект. См. в разделе [Type.5 правила C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26495 MEMBER_UNINIT](c26495.md) переменная «% variable %» не инициализирована. Всегда инициализируйте переменную-член. См. в разделе [Type.6 правила C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

## <a name="bounds-group"></a>Группы ГРАНИЦ

[C26446 USE_GSL_AT](c26446.md) предпочитают использовать `gsl::at()` вместо непроверенного оператора. См. в разделе [C++ Core Guidelines: Bounds.4: не используйте функции стандартной библиотеки и типы, которые не являются контролем границ](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile).

[C26481 NO_POINTER_ARITHMETIC](C26481.md).
Не используйте арифметику указателей. Вместо этого используйте диапазон. См. в разделе [Bounds.1 правила C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26482 NO_DYNAMIC_ARRAY_INDEXING](c26482.md) только индексацию массивов с помощью константные выражения. См. в разделе [Bounds.2 правила C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26483 STATIC_INDEX_OUT_OF_RANGE](c26483.md) значение % value % находится вне границ (0, %, привязанных %) переменной «% variable %». Только индексы массивов с помощью константными выражениями, которые выходят за границы массива. См. в разделе [Bounds.2 правила C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26485 NO_ARRAY_TO_POINTER_DECAY](C26485.md) выражение «% expr %»: массива в указатель затухания. См. в разделе [Bounds.3 правила C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

## <a name="gsl-group"></a>GSL группы

[C26445 NO_SPAN_REF](c26445.md) ссылку `gsl::span` или `std::string_view` может означать наличие проблемы времени существования.
См. в разделе [GSL.view правила C++ Core: представления](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#gslview-views)

[C26446 USE_GSL_AT](c26446.md) предпочитают использовать `gsl::at()` вместо непроверенного оператора. См. в разделе [C++ Core Guidelines: Bounds.4: не используйте функции стандартной библиотеки и типы, которые не являются контролем границ](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile).

[C26448 USE_GSL_FINALLY ](c26448.md) рекомендуется использовать `gsl::finally` Если предполагается финальное действие. См. в разделе [C++ Core Guidelines: GSL.util: служебные программы](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-utilities).

[C26449 NO_SPAN_FROM_TEMPORARY](c26449.md) 
 `gsl::span` или `std::string_view` созданное на будут недействительными при временных становится недействительным. См. в разделе [C++ Core Guidelines: GSL.view: представления](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#gslview-views).


## <a name="deprecated-warnings"></a>Устаревшие предупреждения

Следующие предупреждения присутствуют в группе ранний экспериментальный правило проверки рекомендации core, но уже устарели и можно спокойно проигнорировать. Предупреждения заменяются предупреждения из приведенного выше списка.

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
[С помощью средства проверки C++ Core рекомендации](using-the-cpp-core-guidelines-checkers.md)
