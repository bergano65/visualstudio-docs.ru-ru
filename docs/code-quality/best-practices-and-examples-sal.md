---
title: Рекомендации и примеры (SAL)
ms.date: 11/04/2016
ms.topic: conceptual
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 27570e282c230d4bec47e70aa1bcdd053b75597c
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236748"
---
# <a name="best-practices-and-examples-sal"></a>Рекомендации и примеры (SAL)
Ниже приведены некоторые способы получения максимальной из языка аннотирования исходного кода (SAL) и устранения некоторых распространенных проблем.

## <a name="_in_"></a>\_In\_

Если функция должна выполнять запись в элемент, используйте `_Inout_` `_In_`вместо. Это особенно важно в случаях автоматического преобразования из старых макросов в SAL. До SAL многие программисты использовали макросы как комментарии — макросы с именами `IN` `IN_OUT`, `OUT`, или разновидностями этих имен. Хотя мы рекомендуем преобразовывать эти макросы в SAL, мы советуем соблюдать осторожность при их преобразовании, поскольку код мог быть изменен с момента написания первоначального прототипа, а старый макрос больше не будет отражать то, что делает код. Будьте особенно осторожны с `OPTIONAL` макросом комментариев, так как он часто размещается неправильно, например, на неправильной стороне запятой.

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

## <a name="_opt_"></a>\_opt\_

Если вызывающему объекту не разрешено передавать указатель `_In_` null, используйте оператор или `_Out_` вместо `_In_opt_` `_Out_opt_`. Это относится даже к функции, которая проверяет свои параметры и возвращает ошибку, если она не должна иметь значение NULL. Несмотря на то, что функция проверяет свой параметр на непредвиденное значение NULL и корректно возвращает хорошее защитное программирование, это не означает, что заметка параметра может иметь необязательный тип`_*Xxx*_opt_`().

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

## <a name="_pre_defensive_-and-_post_defensive_"></a>\_\_Предварительная\_ защитная\_и \_защищенная учетная запись\_

Если функция находится на границе доверия, то рекомендуется использовать примечание `_Pre_defensive_`.  Модификатор "защитное" изменяет определенные заметки, чтобы указать, что в момент вызова интерфейс должен проверяться строго, но в теле реализации он должен предположить, что могут быть переданы неверные параметры. В этом случае, на границе доверия предпочитается макрос `_In_ _Pre_defensive_`, чтобы указать, что, хотя вызывающий объект получит ошибку, если он пытается передать значение NULL, тело функции проанализирует, может ли параметр принимать значение NULL, а все попытки разыменования указателя без проверки его на значение NULL будет отмечены.  Примечание `_Post_defensive_` также доступно для использования в обратных вызовах, где вызывающий код считается надежной стороной, а вызываемый код — ненадежной.

## <a name="_out_writes_"></a>\_Исходящие\_операции записи\_

В следующем примере демонстрируется обычное неправильное использование `_Out_writes_`.

```cpp

// Incorrect
void Func1(_Out_writes_(size) CHAR *pb,
    DWORD size
);
```

Заметка `_Out_writes_` означает, что у вас есть буфер. В нем выделено байты с первым байтом, инициализированным при выходе. `cb` Эта аннотация не является строго неправильной и полезна для выражения выделенного размера. Однако он не указывает, сколько элементов инициализируется функцией.

В следующем примере показаны три правильных способа полного указания точного размера инициализированной части буфера.

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

## <a name="_out_-pstr"></a>\_\_ ПСТР

Использование параметра `_Out_ PSTR` практически всегда неверно. Это интерпретируется как наличие выходного параметра, указывающего на символьный буфер и заканчивающегося символом NULL.

```cpp

// Incorrect
void Func1(_Out_ PSTR pFileName, size_t n);

// Correct
void Func2(_Out_writes_(n) PSTR wszFileName, size_t n);
```

Аннотация, например `_In_ PCSTR` , является общей и полезной. Он указывает на входную строку с завершающим нулем, так как предварительное `_In_` условие разрешает распознавание строки, завершающейся нулем.

## <a name="_in_-wchar-p"></a>\_В\_ WCHAR * p

`_In_ WCHAR* p`говорит, что существует входной указатель `p` , указывающий на один символ. Однако в большинстве случаев это не является требуемой спецификацией. Вместо этого, скорее всего, используется спецификация массива, заканчивающегося нулем; для этого используйте `_In_ PWSTR`.

```cpp

// Incorrect
void Func1(_In_ WCHAR* wszFileName);

// Correct
void Func2(_In_ PWSTR wszFileName);
```

Отсутствие правильной спецификации завершения NULL является наиболее распространенным. Используйте соответствующую `STR` версию для замены типа, как показано в следующем примере.

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

## <a name="_out_range_"></a>\_Исходящий\_диапазон\_

Если параметр является указателем и необходимо выразить диапазон значения элемента, на который указывает указатель, используйте `_Deref_out_range_` `_Out_range_`вместо. В следующем примере диапазон * Пкбфиллед выражается, а не Пкбфиллед.

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

`_Deref_out_range_(0, cbSize)`не является строго обязательным для некоторых средств, так как он может быть выведен `_Out_writes_to_(cbSize,*pcbFilled)`из, но он показан здесь для полноты.

## <a name="wrong-context-in-_when_"></a>Неправильный контекст в \_when\_

Еще одна распространенная ошибка — использование вычисления после состояния для предусловий. В следующем примере `_Requires_lock_held_` — это предварительное условие.

```cpp

// Incorrect
_When_(return == 0, _Requires_lock_held_(p->cs))
int Func1(_In_ MyData *p, int flag);

// Correct
_When_(flag == 0, _Requires_lock_held_(p->cs))
int Func2(_In_ MyData *p, int flag);
```

Выражение `result` ссылается на значение после состояния, которое недоступно в предварительном состоянии.

## <a name="true-in-_success_"></a>TRUE в \_случае успеха\_

Если функция завершается успешно, если возвращаемое значение не равно нулю `return != 0` , используйте в качестве условия успеха `return == TRUE`, а не. Ненулевое значение не обязательно означает эквивалентность фактического значения, предоставляемого `TRUE`компилятором. Параметр в `_Success_` — выражение и следующие выражения вычисляются как равные. `return != 0`, `return != false`, `return != FALSE` и `return` без параметров или сравнений.

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

Для ссылочной переменной предыдущая версия SAL использовала подразумеваемый указатель в качестве целевого объекта заметки и требовал добавления `__deref` к заметкам, которые присоединены к ссылочной переменной. Эта версия использует сам объект и не требует дополнительного `_Deref_`.

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

## <a name="annotations-on-return-values"></a>Аннотации для возвращаемых значений

В следующем примере показана общая проблема в аннотациях возвращаемого значения.

```cpp

// Incorrect
_Out_opt_ void *MightReturnNullPtr1();

// Correct
_Ret_maybenull_ void *MightReturnNullPtr2();
```

В этом примере `_Out_opt_` говорит, что указатель может иметь значение NULL в составе предусловия. Однако предусловия нельзя применить к возвращаемому значению. В этом случае правильная Аннотация имеет `_Ret_maybenull_`значение.

## <a name="see-also"></a>См. также

[Использование аннотаций SAL для уменьшения количества дефектов в коде C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)  
[Основные сведения о языке SAL](../code-quality/understanding-sal.md)  
[Создание примечаний к параметрам и возвращаемым значениям функций](../code-quality/annotating-function-parameters-and-return-values.md)  
[Аннотация поведения функций](../code-quality/annotating-function-behavior.md)  
[Аннотация структур и классов](../code-quality/annotating-structs-and-classes.md)  
[Аннотация поведения блокировки](../code-quality/annotating-locking-behavior.md)  
[Указание времени и места применения примечания](../code-quality/specifying-when-and-where-an-annotation-applies.md)  
[Встроенные функции](../code-quality/intrinsic-functions.md)  
