---
title: Рекомендации и примеры (SAL)
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: d26f5329f530af2d6547f44b73ded82c5db53f4f
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="best-practices-and-examples-sal"></a>Рекомендации и примеры (SAL)
Ниже приведены несколько способов получить максимум из исходного кода заметки языка (SAL) и избежать некоторых распространенных проблем.

## <a name="in"></a>\_In\_

Если предполагается, что функция записи в элемент, используйте `_Inout_` вместо `_In_`. Это особенно важно в случае автоматического преобразования от старых макросов для SAL. Перед SAL, многие программисты использовать макросы в качестве комментарии, макросы, которые были названы `IN`, `OUT`, `IN_OUT`, или вариаций этих имен. Несмотря на то, что рекомендуется преобразовать эти макросы в SAL также настоятельно рекомендуется проявлять осторожность при преобразовании, поскольку код может измениться так, как был создан исходный прототип и старые макросы могут больше не отражать делает код. Следует быть особенно осторожным `OPTIONAL` комментарий макрос, поскольку часто размещаться неправильно — например, на стороне неправильный запятую.

```cpp

// Incorrect
void Func1(_In_ int *p1)
{
    if (p1 == NULL)
        return;

    *p1 = 1;
}

// Correct
void Func2(_Inout_ PCHAR p1)
{
    if (p1 == NULL)
        return;

    *p1 = 1;
}
```

## <a name="opt"></a>\_необязательно\_

Если вызывающий объект не может передать указатель null, используйте `_In_` или `_Out_` вместо `_In_opt_` или `_Out_opt_`. Это относится даже к функции, проверяет его параметры и возвращает ошибку, если он имеет значение NULL, если его не следует. Несмотря на то, что наличие функции проверки его параметр непредвиденное значение NULL и возврата корректно является хорошей практикой защитного кода, это не значит, что Аннотация параметра может быть необязательный тип (`_*Xxx*_opt_`).

```cpp

// Incorrect
void Func1(_Out_opt_ int *p1)
{
    *p = 1;
}

// Correct
void Func2(_Out_ int *p1)
{
    *p = 1;
}

```

## <a name="predefensive-and-postdefensive"></a>\_Pre\_защитного\_ и \_Post\_защитного\_

Если функция находится на границе доверия, то рекомендуется использовать примечание `_Pre_defensive_`.  Модификатор «защитного» изменяет некоторые заметки, чтобы указать, что, в момент вызова, интерфейс, должны проверяться строго, но в тексте реализацию его предполагается могут быть переданы неверные параметры. В этом случае, на границе доверия предпочитается макрос `_In_ _Pre_defensive_`, чтобы указать, что, хотя вызывающий объект получит ошибку, если он пытается передать значение NULL, тело функции проанализирует, может ли параметр принимать значение NULL, а все попытки разыменования указателя без проверки его на значение NULL будет отмечены.  Примечание `_Post_defensive_` также доступно для использования в обратных вызовах, где вызывающий код считается надежной стороной, а вызываемый код — ненадежной.

## <a name="outwrites"></a>\_Out\_записывает\_

В следующем примере показано неправильное использование общих `_Out_writes_`.

```cpp

// Incorrect
void Func1(_Out_writes_(size) CHAR *pb,
    DWORD size
);

```

Заметка `_Out_writes_` означает, что имеется буфера. Он имеет `cb` байтов, выделенных с первого байта инициализирован при выходе. Эта заметка не является строго неправильный и полезно express выделенный размер. Тем не менее не показывает, сколько элементов инициализируются с помощью функции.

В следующем примере показано три правильных способа полностью указать точный размер получаемого инициализированный часть буфера.

```cpp

// Correct
void Func1(_Out_writes_to_(size, *pCount) CHAR *pb,
    DWORD size,
    PDWORD pCount
);

void Func2(_Out_writes_all_(size) CHAR *pb,
    DWORD size
);

void Func3(_Out_writes_(size) PSTR pb,
    DWORD size
);

```

## <a name="out-pstr"></a>\_Out\_ PSTR

Использование `_Out_ PSTR` почти всегда неверна. Это значение интерпретируется как выходной параметр, указывающий на буфер символов и является символом NULL.

```cpp

// Incorrect
void Func1(_Out_ PSTR pFileName, size_t n);

// Correct
void Func2(_Out_writes_(n) PSTR wszFileName, size_t n);

```

Заметки, например `_In_ PCSTR` является распространенным и полезным. Он указывает на входную строку, которая имеет конечное значение NULL, так как условие из `_In_` позволяет распознавания строки с завершающим нулем.

## <a name="in-wchar-p"></a>\_В\_ WCHAR * p

`_In_ WCHAR* p` Определяет указатель ввода `p` , указывающий на один знак. В большинстве случаев это то, скорее всего, не спецификации, которая предназначена. Вместо этого возможно, ожидаемым является спецификацией завершающуюся нулевым значением; Чтобы сделать это, используйте `_In_ PWSTR`.

```cpp

// Incorrect
void Func1(_In_ WCHAR* wszFileName);

// Correct
void Func2(_In_ PWSTR wszFileName);

```

Чаще всего отсутствует правильную спецификацию конечное значение NULL. Используйте соответствующую `STR` версии для замены типа, как показано в следующем примере.

```cpp

// Incorrect
BOOL StrEquals1(_In_ PCHAR p1, _In_ PCHAR p2)
{
    return strcmp(p1, p2) == 0;
}

// Correct
BOOL StrEquals2(_In_ PSTR p1, _In_ PSTR p2)
{
    return strcmp(p1, p2) == 0;
}

```

## <a name="outrange"></a>\_Out_range\_

Если параметр является указателем, и необходимо представить диапазон значение элемента, на которую указывает указатель, использовать `_Deref_out_range_` вместо `_Out_range_`. В следующем примере диапазон * выражается pcbFilled, не pcbFilled.

```cpp

// Incorrect
void Func1(
    _Out_writes_bytes_to_(cbSize, *pcbFilled) BYTE *pb,
    DWORD cbSize,
    _Out_range_(0, cbSize) DWORD *pcbFilled
);

// Correct
void Func2(
    _Out_writes_bytes_to_(cbSize, *pcbFilled) BYTE *pb,
    DWORD cbSize,
    _Deref_out_range_(0, cbSize) _Out_ DWORD *pcbFilled
);

```

 `_Deref_out_range_(0, cbSize)` не является обязательным для некоторых средств, так как он может быть выведен из `_Out_writes_to_(cbSize,*pcbFilled)`, но приведен ниже для полноты.

## <a name="wrong-context-in-when"></a>Неправильный контекст в \_при\_

Другой распространенной ошибкой является использование после состояние оценки для предварительных условий. В следующем примере `_Requires_lock_held_` является предварительным условием.

```cpp

// Incorrect
_When_(return == 0, _Requires_lock_held_(p->cs))
int Func1(_In_ MyData *p, int flag);

// Correct
_When_(flag == 0, _Requires_lock_held_(p->cs))
int Func2(_In_ MyData *p, int flag);

```

 Выражение `result` ссылается на значение после состояния, который доступен не в состоянии предварительной.

## <a name="true-in-success"></a>Значение TRUE в \_успех\_

Если функция выполняется успешно, если возвращаемое значение имеет ненулевое значение, используйте `return != 0` как условие успешности вместо `return == TRUE`. Ненулевое значение не обязательно означает эквивалентности действительное значение, которое компилятор предоставляет для `TRUE`. Параметр в `_Success_` — выражение и следующие выражения вычисляются как равные. `return != 0`, `return != false`, `return != FALSE` и `return` без параметров или сравнений.

```cpp

// Incorrect
_Success_(return == TRUE, _Acquires_lock_(*lpCriticalSection))
BOOL WINAPI TryEnterCriticalSection(
  _Inout_ LPCRITICAL_SECTION lpCriticalSection
);

// Correct
_Success_(return != 0, _Acquires_lock_(*lpCriticalSection))
BOOL WINAPI TryEnterCriticalSection(
  _Inout_ LPCRITICAL_SECTION lpCriticalSection
);

```

## <a name="reference-variable"></a>Ссылочная переменная

Используется в качестве цели заметки неявный указатель предыдущей версии SAL ссылочную переменную и требуется добавление `__deref` аннотации, которые присоединены к ссылочную переменную. Эта версия использует сам объект и не требует дополнительного `_Deref_`.

```cpp

// Incorrect
void Func1(
    _Out_writes_bytes_all_(cbSize) BYTE *pb,
    _Deref_ _Out_range_(0, 2) _Out_ DWORD &cbSize
);

// Correct
void Func2(
    _Out_writes_bytes_all_(cbSize) BYTE *pb,
    _Out_range_(0, 2) _Out_ DWORD &cbSize
);

```

## <a name="annotations-on-return-values"></a>Заметки на возвращаемые значения

В следующем примере показано распространенная проблема в возвращаемое значение заметки.

```cpp

// Incorrect
_Out_opt_ void *MightReturnNullPtr1();

// Correct
_Ret_maybenull_ void *MightReturnNullPtr2();

```

В этом примере `_Out_opt_` говорит, что указатель может быть NULL как часть необходимое условие. Тем не менее предварительные условия не может применяться к возвращаемому значению. В этом случае правильный Аннотация не `_Ret_maybenull_`.

## <a name="see-also"></a>См. также

[Использовании аннотаций SAL для сокращения дефектов в коде C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
[основные сведения о SAL](../code-quality/understanding-sal.md)
[Аннотация параметров функции и возвращаемых значений](../code-quality/annotating-function-parameters-and-return-values.md) 
 [Аннотация поведения функций](../code-quality/annotating-function-behavior.md)
[Аннотация структур и классов](../code-quality/annotating-structs-and-classes.md)
[Аннотация поведения блокировки](../code-quality/annotating-locking-behavior.md) 
 [Указание времени и места применения примечания](../code-quality/specifying-when-and-where-an-annotation-applies.md)
[встроенные функции](../code-quality/intrinsic-functions.md)