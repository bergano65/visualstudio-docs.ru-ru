---
title: Рекомендации и примеры (SAL) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: 666276fb-99c2-4dc9-8bac-d74861c203ea
caps.latest.revision: 14
author: mikeblome
ms.author: mblome
manager: jillfra
ms.openlocfilehash: 56e57d182a21429d73b8eae0b79f96532732ae7b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62428577"
---
# <a name="best-practices-and-examples-sal"></a>Рекомендации и примеры (SAL)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ниже приведены несколько способов получить доступ к большинству из языка заметки исходного кода (SAL) и избежать возникновения некоторых распространенных проблем.  
  
## <a name="in"></a>\_In\_
 Если предполагается, что функция записи в элемент, используйте `_Inout_` вместо `_In_`. Это особенно важно в случае автоматического преобразования из более старых макросов для SAL. Перед SAL, многие программисты использовали макросы как комментарии, макросы, которые были названы `IN`, `OUT`, `IN_OUT`, или вариаций этих имен. Несмотря на то, что мы рекомендуем преобразовывать эти макросы для SAL, мы также настоятельно рекомендуется проявлять осторожность при преобразовании, так как код может измениться, так как был написан первоначальным прототипом, и старые макросы могут больше не отражать, что делает код. Следует быть особенно осторожным `OPTIONAL` комментарий макрос, так как часто он помещается неправильно — например, на неверной стороне запятую.  
  
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
  
## <a name="opt"></a>\_opt\_  
 Если вызывающий объект не может передавать указатель null, используйте `_In_` или `_Out_` вместо `_In_opt_` или `_Out_opt_`. Это относится даже к функцию, которая проверяет свои параметры и возвращает ошибку, если он равен NULL, если его не следует. Несмотря на то, что наличие функции наличие параметра непредвиденное значение NULL и возвращать корректно является хорошей практикой защитного кодирования, это не означает, что Аннотация параметра может быть необязательным типа (\_*Xxx*_opt\_).  
  
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
  
## <a name="predefensive-and-postdefensive"></a>\_Pre_defensive\_ и \_Post_defensive\_  
 Если функция находится на границе доверия, то рекомендуется использовать примечание `_Pre_defensive_`.  Модификатор «защитных» изменяет некоторые заметки, чтобы указать, что, точке вызова, интерфейса, которые должны проверяться строго, но в тексте реализации его следует предполагать, что могут быть переданы неверные параметры. В этом случае, на границе доверия предпочитается макрос `_In_ _Pre_defensive_`, чтобы указать, что, хотя вызывающий объект получит ошибку, если он пытается передать значение NULL, тело функции проанализирует, может ли параметр принимать значение NULL, а все попытки разыменования указателя без проверки его на значение NULL будет отмечены.  Примечание `_Post_defensive_` также доступно для использования в обратных вызовах, где вызывающий код считается надежной стороной, а вызываемый код — ненадежной.  
  
## <a name="outwrites"></a>\_Out_writes\_  
 В следующем примере показано неправильное использование общих `_Out_writes_`.  
  
```cpp  
  
// Incorrect  
void Func1(_Out_writes_(size) CHAR *pb,   
    DWORD size  
);  
  
```  
  
 Заметка `_Out_writes_` означает, что у вас есть буфер. Он имеет `cb` байтов, выделенных с первого байта инициализирован при выходе. Эта заметка не является строго неправильный и полезно express выделенный размер. Тем не менее не показывает, сколько элементов инициализируются с помощью функции.  
  
 В следующем примере показано три правильных способа полностью определить точный размер инициализированный часть буфера.  
  
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
 Использование `_Out_ PSTR` почти всегда не так. Это значение интерпретируется как имеющий выходной параметр, указывающий на символьный буфер, и он заканчивается НУЛЕВЫМ байтом.  
  
```cpp  
  
// Incorrect  
void Func1(_Out_ PSTR pFileName, size_t n);  
  
// Correct  
void Func2(_Out_writes_(n) PSTR wszFileName, size_t n);  
  
```  
  
 Заметки, например `_In_ PCSTR` является распространенным и полезным. Он указывает на входную строку, которая имеет конечное значение NULL, так как предусловие `_In_` позволяет распознавание строку, завершающуюся символом NULL.  
  
## <a name="in-wchar-p"></a>\_В\_ WCHAR * p  
 `_In_ WCHAR* p` об отсутствии во входной указатель `p` , указывающего на один символ. Однако в большинстве случаев это скорее всего, не спецификации, которая предназначена. Вместо этого, скорее всего, назначения представляет собой спецификацию массива НУЛЕВЫМ байтом; Чтобы сделать это, используйте `_In_ PWSTR`.  
  
```cpp  
  
// Incorrect  
void Func1(_In_ WCHAR* wszFileName);  
  
// Correct  
void Func2(_In_ PWSTR wszFileName);  
  
```  
  
 Отсутствует спецификация правильное завершение знаком NULL является общим. Используйте соответствующий `STR` версии для замены типа, как показано в следующем примере.  
  
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
  
 `_Deref_out_range_(0, cbSize)` не является обязательным для некоторых средств, так как он может быть выведен из `_Out_writes_to_(cbSize,*pcbFilled)`, но представлено здесь для полноты картины.  
  
## <a name="wrong-context-in-when"></a>Неправильный контекст в \_при\_  
 Другой распространенной ошибкой является использование анализ после состояния для предварительных условий. В следующем примере `_Requires_lock_held_` является необходимым условием.  
  
```cpp  
  
// Incorrect  
_When_(return == 0, _Requires_lock_held_(p->cs))  
int Func1(_In_ MyData *p, int flag);  
  
// Correct  
_When_(flag == 0, _Requires_lock_held_(p->cs))  
int Func2(_In_ MyData *p, int flag);  
  
```  
  
 Выражение `result` ссылается на значение после состояния, которая недоступна в состоянии предварительной.  
  
## <a name="true-in-success"></a>Значение TRUE в \_успех\_  
 Если функция завершается успешно, если возвращаемое значение не равно нулю, используйте `return != 0` как условии успешного завершения, а не `return == TRUE`. Ненулевое значение не обязательно означает эквивалентности относительно фактического значения, компилятор предоставляет для `TRUE`. Параметр в `_Success_` — выражение и следующие выражения вычисляются как равные. `return != 0`, `return != false`, `return != FALSE` и `return` без параметров или сравнений.  
  
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
 Ссылку на переменную, предыдущей версии SAL используется неявный указатель в качестве цели заметки и требуется добавление `__deref` с аннотациями, к которым ссылку на переменную. Эта версия использует самого объекта и не требует дополнительной `_Deref_`.  
  
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
 В следующем примере показано распространенной проблемой в возвращаемое значение заметки.  
  
```cpp  
  
// Incorrect  
_Out_opt_ void *MightReturnNullPtr1();  
  
// Correct  
_Ret_maybenull_ void *MightReturnNullPtr2();  
  
```  
  
 В этом примере `_Out_opt_` говорит, что указатель может иметь значение NULL как часть предусловие. Тем не менее предварительные условия не может применяться к возвращаемому значению. В данном случае является правильной `_Ret_maybenull_`.  
  
## <a name="see-also"></a>См. также  
 [Использование аннотаций SAL для сокращения количества дефектов в коде C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Основные сведения о SAL](../code-quality/understanding-sal.md)   
 [Создание примечаний к функции параметров и возвращаемых значений](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Аннотация поведения функций](../code-quality/annotating-function-behavior.md)   
 [Аннотация структур и классов](../code-quality/annotating-structs-and-classes.md)   
 [Аннотация поведения блокировки](../code-quality/annotating-locking-behavior.md)   
 [Указание времени и места применения примечания](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Встроенные функции](../code-quality/intrinsic-functions.md)
