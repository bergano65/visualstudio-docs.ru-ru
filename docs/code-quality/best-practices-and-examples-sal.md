---
title: "Рекомендации и примеры (SAL) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 666276fb-99c2-4dc9-8bac-d74861c203ea
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# Рекомендации и примеры (SAL)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ниже приведены некоторые способы для максимально эффективного использования языка аннотации исходного кода \(SAL\) и решения общих проблем.  
  
## \_In\_  
 Если функция, вероятно, будет писать в элемент, то используйте `_Inout_` вместо `_In_`.  Это особенно актуально в случае автоматического преобразования из более старых макросов в SAL.  До SAL, многие программисты использовали макросы в качестве комментариев — макросы, которые были названы `IN`, `OUT`, `IN_OUT` или вариантами этих имен.  Рекомендуется преобразовать эти макросы в SAL; кроме того, будьте осторожны при преобразовании, поскольку код мог измениться со времени написания исходного прототипа, и старые макросы могут более не отражать действия в коде.  Будьте особенно внимательны с макросом\-комментарием `OPTIONAL`, поскольку он зачастую располагается неправильно, например, на неверной стороне запятой.  
  
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
  
## \_opt\_  
 Если вызывающий объект не позволяет передать указатель null, используйте `_In_` или `_Out_` вместо `_In_opt_` или `_Out_opt_`.  Это применяется даже к функции, которая проверяет свои параметры и возвращает ошибку, если есть значение null, где его не должно быть.  Хотя проверка функцией своих параметров на непредвиденные значения NULL и аккуратный возврат — хорошая практика защитного кодирования, это не означает, что заметка параметра может быть необязательного типа \(\_*Xxx*\_opt\_\).  
  
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
  
## \_Pre\_defensive\_ и \_Post\_defensive\_  
 Если функция появится на границе доверия, то рекомендуется использовать заметку `_Pre_defensive_`.  Модификатор "защитный" изменяет некоторые заметки чтобы указать, что, с точки зрения вызова, интерфейс следует проверить строго, но в теле реализации учтено, что могут передаваться неверные параметры.  В этом случае, на границе доверия предпочитается макрос `_In_ _Pre_defensive_` чтобы указать, что, хотя вызывающий объект получит ошибку, если он пытается передать значение NULL, тело функции проанализирует, может ли параметр принимать значение NULL, а все попытки разыменования указателя без проверки его на значение NULL будет отмечены.  Примечание `_Post_defensive_` также доступно для использования в обратных вызовах, где вызывающий код считается надежной стороной, а вызываемый код — ненадежной.  
  
## \_Out\_writes\_  
 В следующем примере показано частое неправильное использование `_Out_writes_`.  
  
```cpp  
  
// Incorrect  
void Func1(_Out_writes_(size) CHAR *pb,   
    DWORD size  
);  
  
```  
  
 Примечание `_Out_writes_` означает, что буфер существует.  Она содержит `cb` выделенных байт, первый байт инициализируется при выходе.  Эта заметка не является строго неверной, и она полезна для представления выделенного размера.  Однако она не сообщает, сколько элементов инициализировано функцией.  
  
 Следующий пример показывает три правильных способа указания точного размера инициализированной части буфера.  
  
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
  
## \_Out\_ PSTR  
 Использование `_Out_ PSTR` почти всегда неверно.  Это интерпретируется как наличие выходного параметра, указывающего на символьный буфер с завершающим нулем.  
  
```cpp  
  
// Incorrect  
void Func1(_Out_ PSTR pFileName, size_t n);  
  
// Correct  
void Func2(_Out_writes_(n) PSTR wszFileName, size_t n);  
  
```  
  
 Аннотация `_In_ PCSTR` распространенная и полезная.  Она указывает на входную строку с завершающим нулем, так как предварительное условие `_In_` позволяет распознавание строки с завершающим нулем.  
  
## \_In\_ WCHAR\* p  
 `_In_ WCHAR* p` указывает, что есть входной указатель `p`, который указывает на один знак.  Однако в большинстве случаев это не является спецификацией, которая задумана.  Вместо этого, вероятнее, задумана спецификация массива с завершающим нулем; для этого используйте `_In_ PWSTR`.  
  
```cpp  
  
// Incorrect  
void Func1(_In_ WCHAR* wszFileName);  
  
// Correct  
void Func2(_In_ PWSTR wszFileName);  
  
```  
  
 Отсутствие корректной спецификации завершающего нуля достаточно распространено.  Используйте соответствующую версию `STR` чтобы заменить тип, как показано в следующем примере.  
  
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
  
## \_Out\_range\_  
 Если параметр является указателем, и нужно указать диапазон значений элементов, на которые указывает указатель, используйте `_Deref_out_range_` вместо `_Out_range_`.  В следующем примере указан диапазон \*pcbFilled, а не диапазон pcbFilled.  
  
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
  
 `_Deref_out_range_(0, cbSize)` не является строго необходимым для некоторых средств, поскольку он может быть выведен из `_Out_writes_to_(cbSize,*pcbFilled)`, но он показан здесь для полноты.  
  
## Неправильный контекст в \_When\_  
 Другая общая ошибка заключается в использовании вычислений последующих состояний в предварительных условиях.  В следующем примере `_Requires_lock_held_` является предусловием .  
  
```cpp  
  
// Incorrect  
_When_(return == 0, _Requires_lock_held_(p->cs))  
int Func1(_In_ MyData *p, int flag);  
  
// Correct  
_When_(flag == 0, _Requires_lock_held_(p->cs))  
int Func2(_In_ MyData *p, int flag);  
  
```  
  
 Выражение `result` относится к значению последующего состояния, которое недоступно в более раннем состоянии.  
  
## Значение TRUE в \_Success\_  
 Если функция завершается успешно при возвращаемом значении, не равном нулю, используйте в условии успешного завершения `return != 0` вместо `return == TRUE`.  Ненулевое значение не обязательно означает равенство с действительным значением, которое компилятор предоставляет для `TRUE`.  Параметр в `_Success_` \- выражение и следующие выражения вычисляются как равные. `return != 0`, `return != false`, `return != FALSE` и `return` без параметров или сравнений.  
  
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
  
## Ссылочная переменная  
 Для ссылочной переменной предыдущая версия SAL использует неявный указатель в качестве цели аннотации и требует добавочного макроса `__deref` к аннотациям, которые присоединены к ссылочной переменной.  Эта версия использует сам объект и не требует дополнительного макроса `_Deref_`.  
  
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
  
## Аннотации для возвращаемых значений  
 В следующем примере показаны общие проблемы в аннотациях к возвращаемым значениям.  
  
```cpp  
  
// Incorrect  
_Out_opt_ void *MightReturnNullPtr1();  
  
// Correct  
_Ret_maybenull_ void *MightReturnNullPtr2();  
  
```  
  
 В этом примере `_Out_opt_` указывает, что указатель может иметь значение NULL в качестве части предварительного условия.  Однако предварительные условия невозможно применить к возвращаемому значению.  В этом случае корректной аннотацией будет `_Ret_maybenull_`.  
  
## См. также  
 [Использование аннотаций SAL для сокращения количества дефектов в коде C\/C\+\+](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Основные сведения о языке SAL](../code-quality/understanding-sal.md)   
 [Создание примечаний к параметрам и возвращаемым значениям функций](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Аннотация поведения функций](../code-quality/annotating-function-behavior.md)   
 [Аннотация структур и классов](../code-quality/annotating-structs-and-classes.md)   
 [Аннотация поведения блокировки](../code-quality/annotating-locking-behavior.md)   
 [Указание времени и места применения примечания](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Встроенные функции](../code-quality/intrinsic-functions.md)