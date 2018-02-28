---
title: "Visual Studio C++ основные правила проверки ссылку | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code analysis, C++ core check
ms.assetid: f1429463-136e-41ed-8a75-a8dbf0b4fd89
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e0e12941db7f8e6f539c88014fc5fa9c55ca809c
ms.sourcegitcommit: 342e5ec5cec4d07864d65379c2add5cec247f3d6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/27/2018
---
# <a name="c-core-guidelines-checker-reference"></a>Справочные материалы по Проверка правила C++ основной
В этом разделе перечислены предупреждения C++ основные правила проверки. Сведения об анализе кода см. в разделе [/ analyze (анализ кода)](/cpp/build/reference/analyze-code-analysis) и [быстрый запуск: анализ кода для C/C++](../code-quality/quick-start-code-analysis-for-c-cpp.md).  
  
**Примечание**: некоторые предупреждения принадлежит нескольким группам, а не все предупреждения справочном разделе.

## <a name="ownerpointer-group"></a>OWNER_POINTER группы

[C26402 DONT_HEAP_ALLOCATE_MOVABLE_RESULT](C26402.md)  
  Возвращают объект с областью, вместо размещенных в куче, если он имеет конструктор перемещения. В разделе [C++ основные рекомендации R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr). 
     
[C26403 RESET_OR_DELETE_OWNER](C26403.md)  
  Сброс или явно удалить владельца\<T > указатель «% переменная %». В разделе [C++ основные рекомендации R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).  
     
[C26404 DONT_DELETE_INVALID](C26404.md)  
  Не удаляйте владельца\<T >, которые могут быть в недопустимом состоянии. В разделе [C++ основные рекомендации R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).  

[C26405 DONT_ASSIGN_TO_VALID](C26405.md)  
  Владелец не назначается\<T >, которые могут быть в допустимом состоянии. В разделе [C++ основные рекомендации R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).  

[C26406 DONT_ASSIGN_RAW_TO_OWNER](C26406.md)  
  Не присваивайте необработанный указатель владельца\<T >. В разделе [C++ основные рекомендации R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).  
  
[C26407 DONT_HEAP_ALLOCATE_UNNECESSARILY](C26407.md)  
  Предпочтение объектов с областью, не кучи выделить без необходимости. В разделе [C++ основные рекомендации R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).  

[C26429 USE_NOTNULL](C26429.md)  
  Символ «% символ» никогда не проверяется на наличие nullness, он может быть помечен как not_null. В разделе [C++ основные рекомендации F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).  

[C26430 TEST_ON_ALL_PATHS](C26430.md)  
  Символ «% символ» не тестировался на nullness во всех путях. В разделе [C++ основные рекомендации F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).  
  
[C26431 DONT_TEST_NOTNULL](C26431.md)  
  Тип выражения «% expr» уже gsl::not_null. Не выполняйте проверку его для nullness. В разделе [C++ основные рекомендации F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).  

## <a name="rawpointer-group"></a>RAW_POINTER группы
 
[C26400 NO_RAW_POINTER_ASSIGNMENT](c26400.md)  
Не присвоить результат выделение или вызов функции с владельцем\<T > возвращаемое значение к указателю необработанные; используйте владельца\<T > вместо него. В разделе [C++ основные рекомендации I.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw). 

[C26401 DONT_DELETE_NON_OWNER](c26401.md)  
Не удаляйте необработанный указатель, который не является владельцем\<T >. В разделе [C++ основные рекомендации I.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw). 

[C26402 DONT_HEAP_ALLOCATE_MOVABLE_RESULT](C26402.md)   вернуть области объекта вместо размещенных в куче, если он имеет конструктор перемещения. В разделе [C++ основные рекомендации R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr). 
 
[C26408 NO_MALLOC_FREE](C26408.md)  
  Избежать malloc() и free(), предпочтительно версии nothrow возможности удаления. В разделе [C++ основные рекомендации R.10](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-mallocfree).  
  
[C26409 NO_NEW_DELETE](C26409.md)  
  Старайтесь не вызывать новые и удалить явно, используйте std::make_unique\<T > вместо него. В разделе [C++ основные рекомендации R.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-newdelete).  

[C26429 USE_NOTNULL](C26429.md)  
  Символ «% символ» никогда не проверяется на наличие nullness, он может быть помечен как not_null. В разделе [C++ основные рекомендации F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).  
  
[C26430 TEST_ON_ALL_PATHS](C26430.md)  
  Символ «% символ» не тестировался на nullness во всех путях. В разделе [C++ основные рекомендации F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).  
  
[C26431 DONT_TEST_NOTNULL](C26431.md)  
  Тип выражения «% expr» уже gsl::not_null. Не выполняйте проверку его для nullness. В разделе [C++ основные рекомендации F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).  
  
[C26481 NO_POINTER_ARITHMETIC](C26481.md)  
  Не используйте арифметических операций над указателями. Вместо этого используйте диапазон. В разделе [Bounds.1 правила C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).  

[C26485 NO_ARRAY_TO_POINTER_DECAY](C26485.md)   
  Выражение «% expr»: нет массива критичной указателя. В разделе [Bounds.3 правила C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).  

## <a name="uniquepointer-group"></a>UNIQUE_POINTER группы
  
[C26410 NO_REF_TO_CONST_UNIQUE_PTR](C26410.md)  
  Параметр «% параметр %» является ссылкой на `const` уникальный указатель const T * или const T &. В разделе [C++ основные рекомендации R.32](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-uniqueptrparam).  
     
[C26411 NO_REF_TO_UNIQUE_PTR](C26411.md)  
  Параметр «% параметр %» является ссылкой на уникальный указатель, и никогда не переназначении или сбросе, используйте T * или T &. В разделе [C++ основные рекомендации R.33](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-reseat).  
     
[C26414 RESET_LOCAL_SMART_PTR](C26414.md)  
  Перемещения, копирования, переназначить или сбросить локального смарт-указатель «% символ». В разделе [C++ основные рекомендации R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).  
    
[C26415 SMART_PTR_NOT_NEEDED](C26415.md)  
  Интеллектуальный указатель параметр «% символ %» используется только для доступа содержится указатель. Используйте T * или T &. В разделе [C++ основные рекомендации R.30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam).  

## <a name="sharedpointer-group"></a>SHARED_POINTER группы

[C26414 RESET_LOCAL_SMART_PTR](C26414.md)  
  Перемещения, копирования, переназначить или сбросить локального смарт-указатель «% символ». В разделе [C++ основные рекомендации R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).  
    
[C26415 SMART_PTR_NOT_NEEDED](C26415.md)  
  Интеллектуальный указатель параметр «% символ %» используется только для доступа содержится указатель. Используйте T * или T &. В разделе [C++ основные рекомендации R.30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam).  
    
[C26416 NO_RVALUE_REF_SHARED_PTR](C26416.md)  
  Общий указатель параметр «% символ» передается по ссылке rvalue. Вместо передачи по значению. В разделе [C++ основные рекомендации R.34](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-owner).  
  
[C26417 NO_LVALUE_REF_SHARED_PTR](C26417.md)  
  Общий указатель параметр «% символ» передается по ссылке и не сбрасывается или переназначить. Используйте T * или T &. В разделе [C++ основные рекомендации R.35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam).  
  
[C26418 NO_VALUE_OR_CONST_REF_SHARED_PTR](C26418.md)  
  Общий указатель параметр «% символ» не копируется или перемещается. Используйте T * или T &. В разделе [C++ основные рекомендации R.36](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-const).  

## <a name="declaration-group"></a>ОБЪЯВЛЕНИЕ группы
    
[C26426 NO_GLOBAL_INIT_CALLS](C26426.md)  
  Глобальный инициализатор вызывает функцию, не являющийся constexpr '% символ». В разделе [C++ основные рекомендации I.22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects).  
  
[C26427 NO_GLOBAL_INIT_EXTERNS](C26427.md)  
  Глобальный инициализатор обращается к extern объекта «% символ». В разделе [C++ основные рекомендации I.22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects).  
  
[C26444 NO_UNNAMED_RAII_OBJECTS](c26444.md) Избегайте неименованные объектов, содержащих пользовательские построения и удаления. [ES.84: (Старайтесь) объявить локальную переменную без имени](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).

## <a name="class-group"></a>Класс группы
    
[C26432 DEFINE_OR_DELETE_SPECIAL_OPS](C26432.md)  
  При определении или удалить все операции по умолчанию в типе «% символ», определение или удалите их все. В разделе [C++ основные рекомендации C.21](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c21-if-you-define-or-delete-any-default-operation-define-or-delete-them-all).  


[C26433 OVERRIDE_EXPLICITLY](c26433.md) функции «% символ» должен быть помечен как «override». В разделе [ C.128: виртуальные функции следует указывать только один виртуальный, переопределения или последний](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c128-virtual-functions-should-specify-exactly-one-of-virtual-override-or-final). 

  
[C26434 DONT_HIDE_METHODS](C26434.md)  
  Функция «% symbol_1» скрывает невиртуальной функции «% symbol_2%». В разделе [C++ основные рекомендации C.128](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c128-virtual-functions-should-specify-exactly-one-of-virtual-override-or-final).  
  

[C26435 SINGLE_VIRTUAL_SPECIFICATION](c26435.md) функции «% символ» следует указать только один из «virtual», «override» или «final». В разделе [ C.128: виртуальные функции следует указывать только один виртуальный, переопределения или последний](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md). 


[C26436 NEED_VIRTUAL_DTOR](C26436.md)  
  Тип «% % символ» виртуальная функция должен либо открытый виртуальных и защищенных невиртуальный деструктор. В разделе [C++ основные рекомендации C.35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c35-a-base-class-destructor-should-be-either-public-and-virtual-or-protected-and-nonvirtual).  


[C26443 NO_EXPLICIT_DTOR_OVERRIDE](c26443.md) переопределение деструктор не следует использовать явное «override» и «virtual» описателей. В разделе [C.128: виртуальные функции следует указывать только один виртуальный, переопределения или последний](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).


## <a name="type-group"></a>Тип группы
    
[C26437 DONT_SLICE](C26437.md)  
  Не срез. В разделе [C++ основные рекомендации ES.63](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es63-dont-slice).  

## <a name="style-group"></a>СТИЛЬ группы  
[C26438 NO_GOTO](C26438.md)  
  Избегайте `goto`. В разделе [C++ основные рекомендации ES.76](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es76-avoid-goto).  
  
## <a name="function-group"></a>Группа ФУНКЦИЙ
    
[C26439 SPECIAL_NOEXCEPT](C26439.md)  
  Не может создавать функций этого типа. Он объявляется `noexcept`. В разделе [C++ основные рекомендации F.6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).  
  
[C26440 DECLARE_NOEXCEPT](C26440.md)  
  Функция «% символ» могут быть объявлены `noexcept`. В разделе [C++ основные рекомендации F.6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).  

## <a name="concurrency-group"></a>Группы с ПАРАЛЛЕЛИЗМОМ
    
[C26441 NO_UNNAMED_GUARDS](C26441.md)  
 Система безопасности объектов должны быть именованными. В разделе [C++ основные рекомендации cp.44](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#cp44-remember-to-name-your-lock_guards-and-unique_locks).  

## <a name="const-group"></a>CONST группы
    
C26460 USE_CONST_REFERENCE_ARGUMENTS  
  Аргумент ссылки «% аргумента %» для функции «% функции» может быть помечен как `const`. В разделе [C++ основные рекомендации con.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref).  
  
C26461 USE_CONST_POINTER_ARGUMENTS: аргумент указателя «% аргумента %» для функции «% функции» может быть помечен как указатель на `const`. В разделе [C++ основные рекомендации con.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref).  
  
C26462 USE_CONST_POINTER_FOR_VARIABLE  
  Только один раз присваивается значение, на который указывает «% переменная %», пометьте его как указатель на `const`. В разделе [C++ основные рекомендации con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).  
  
C26463 USE_CONST_FOR_ELEMENTS  
  Элементы массива «% массива» назначаются только один раз, элементы пометить `const`. В разделе [C++ основные рекомендации con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).  
  
C26464 USE_CONST_POINTER_FOR_ELEMENTS  
  Значения, на который указывает элементы массива «% массива» назначаются только один раз, элементы пометить как указатель на `const`. В разделе [C++ основные рекомендации con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).  

C26496 USE_CONST_FOR_VARIABLE  
  Переменной «% переменная %» присваивается только один раз, пометьте его как `const`. В разделе [C++ основные рекомендации con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).  
  
C26497 USE_CONSTEXPR_FOR_FUNCTION  
  Это функция % функции могут быть помечены `constexpr` при необходимости вычисление во время компиляции. В разделе [C++ основные рекомендации F.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rf-constexpr).  
  
C26498 USE_CONSTEXPR_FOR_FUNCTIONCALL  
  Можно использовать функции % % этот вызов функции `constexpr` при необходимости вычисление во время компиляции. В разделе [C++ основные рекомендации con.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-constexpr).  

## <a name="type-group"></a>Тип группы
C26465 NO_CONST_CAST_UNNECESSARY  
  Не используйте `const_cast` для снятия `const`. `const_cast` не является обязательным. потерей постоянства или неустойчивости не удаляется с этого преобразования. В разделе [Type.3 правила C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-constcast).  
  
C26466 NO_STATIC_DOWNCAST_POLYMORPHIC  
  Не используйте `static_cast` downcasts. Приведение из полиморфного типа следует использовать dynamic_cast. В разделе [Type.2 правила C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-downcast).  
  
C26471 NO_REINTERPRET_CAST_FROM_VOID_PTR  
  Не используйте `reinterpret_cast`. Можно использовать приведение из void * `static_cast`. В разделе [Type.1 правила C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).  
  
[C26472 NO_CASTS_FOR_ARITHMETIC_CONVERSION](C26472.md)  
  Не используйте `static_cast` преобразования. Использование фигурных скобок, gsl::narrow_cast или gsl::narow. В разделе [Type.1 правила C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).  
  
[C26473 NO_IDENTITY_CAST](C26473.md)  
  Не выполнять приведение между типами указателей, где тип источника и целевого типа совпадают. В разделе [Type.1 правила C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).  
  
[C26474 NO_IMPLICIT_CAST](C26474.md)  
  Не выполнять приведение между типами указателей, если может иметь неявное преобразование. В разделе [Type.1 правила C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).  
  
[C26475 NO_FUNCTION_STYLE_CASTS](C26475.md)  
  Не следует использовать стиль функции C приведения. В разделе [C++ основные рекомендации ES.49](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es49-if-you-must-use-a-cast-use-a-named-cast).  
     
C26490 NO_REINTERPRET_CAST  
  Не используйте `reinterpret_cast`. В разделе [Type.1 правила C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).  
  
C26491 NO_STATIC_DOWNCAST  
  Не используйте `static_cast` downcasts. В разделе [Type.2 правила C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).  
  
C26492 NO_CONST_CAST  
  Не используйте `const_cast` для снятия `const`. В разделе [Type.3 правила C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).  
    
C26493 NO_CSTYLE_CAST  
  Не используйте C-стиль приведения. В разделе [Type.4 правила C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type). 
     
C26494 VAR_USE_BEFORE_INIT  
  Переменная «% переменная %» не инициализирован. Всегда Инициализируйте объект. В разделе [Type.5 правила C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).  
  
C26495 MEMBER_UNINIT  
  Переменная «% переменная %» не инициализирован. Всегда инициализируйте переменную-член. В разделе [Type.6 правила C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).  
  
## <a name="bounds-group"></a>Группы ГРАНИЦ

[C26481 NO_POINTER_ARITHMETIC](C26481.md)   
  Не используйте арифметических операций над указателями. Вместо этого используйте диапазон. В разделе [Bounds.1 правила C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).  
  
C26482 NO_DYNAMIC_ARRAY_INDEXING  
  Только индексы массивов с помощью константных выражений. В разделе [Bounds.2 правила C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).  
  
C26483 STATIC_INDEX_OUT_OF_RANGE  
  Значение % значение находится за пределами (0, привязанные %) переменной «% переменная %». Только индексы массивов с помощью константными выражениями, которые находятся в пределах границ массива. В разделе [Bounds.2 правила C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).  

[C26485 NO_ARRAY_TO_POINTER_DECAY](C26485.md)   
  Выражение «% expr»: нет массива критичной указателя. В разделе [Bounds.3 правила C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).  

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
