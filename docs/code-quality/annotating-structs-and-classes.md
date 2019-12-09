---
title: Аннотация структур и классов
ms.date: 06/28/2019
ms.topic: conceptual
f1_keywords:
- _Field_size_bytes_part_
- _Field_size_bytes_full_opt_
- _Field_size_bytes_
- _Field_size_opt_
- _Field_size_part_
- _Field_size_bytes_part_opt_
- _Field_range_
- _Field_size_part_opt_
- _Field_size_
- _Field_size_bytes_opt_
- _Struct_size_bytes_
- _Field_size_bytes_full_
- _Field_size_full_
- _Field_size_full_opt_
- _Field_z_
ms.assetid: b8278a4a-c86e-4845-aa2a-70da21a1dd52
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- multiple
ms.openlocfilehash: 70dc130633e9f191811748b2ab316ad339ad4277
ms.sourcegitcommit: 174c992ecdc868ecbf7d3cee654bbc2855aeb67d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/06/2019
ms.locfileid: "74879260"
---
# <a name="annotating-structs-and-classes"></a>Аннотация структур и классов

Вы можете добавить примечание к структурам и членам классов, используя примечания, которые действуют как инварианты — предполагается, что они будут выполнены в любом вызове функции или функции входа и выхода, которая содержит включающую структуру в качестве значения параметров или результатов.

## <a name="struct-and-class-annotations"></a>Заметки структуры и класса

- `_Field_range_(low, high)`

     Поле находится в диапазоне (включающем) от `low` до `high`.  Эквивалент для `_Satisfies_(_Curr_ >= low && _Curr_ <= high)` применяется к аннотированному объекту с помощью соответствующих предусловий или постусловий.

- `_Field_size_(size)`, `_Field_size_opt_(size)`, `_Field_size_bytes_(size)`, `_Field_size_bytes_opt_(size)`

     Поле с записываемым размером в элементах (или байтах), как определено в `size`.

- `_Field_size_part_(size, count)`, `_Field_size_part_opt_(size, count)`,         `_Field_size_bytes_part_(size, count)`, `_Field_size_bytes_part_opt_(size, count)`

     Поле с записываемым размером в элементах (или байтах), как определено в `size` и `count` этих элементов (байт), которые доступны для чтения.

- `_Field_size_full_(size)`, `_Field_size_full_opt_(size)`, `_Field_size_bytes_full_(size)`, `_Field_size_bytes_full_opt_(size)`

     Поле с размером в элементах (или байт), доступных для записи и чтения, как определено в `size`.

- `_Field_z_`

     Поле, имеющее строку, завершающуюся нулем.

- `_Struct_size_bytes_(size)`

     Применяется к объявлению структуры или класса.  Указывает, что допустимый объект этого типа может быть больше объявленного типа с количеством байт, указанным в `size`.  Например:

    ```cpp

    typedef _Struct_size_bytes_(nSize)
    struct MyStruct {
        size_t nSize;
        ...
    };

    ```

     Размер буфера в байтах параметра, `pM` типа `MyStruct *`, принимается следующим образом:

    ```cpp
    min(pM->nSize, sizeof(MyStruct))
    ```

## <a name="example"></a>Пример

```cpp
#include <sal.h>

// This _Struct_size_bytes_ is equivalent to what below _Field_size_ means.
_Struct_size_bytes_(__builtin_offsetof(MyBuffer, buffer) + bufferSize * sizeof(int))
struct MyBuffer
{
    static int MaxBufferSize;
    
    _Field_z_
    const char* name;
    
    int firstField;

    // ... other fields

    _Field_range_(1, MaxBufferSize)
    int bufferSize;
    
    _Field_size_(bufferSize)        // Prefered way - easier to read and maintain.
    int buffer[]; // Using C99 Flexible array member
};
```

Примечания для этого примера:

- `_Field_z_` равно `_Null_terminated_`.  `_Field_z_` для поля имени указывает, что поле имени является строкой, завершающейся нулем.
- `_Field_range_` для `bufferSize` указывает, что значение `bufferSize` должно находиться в диапазоне от 1 до `MaxBufferSize` (оба включительно).
- Конечные результаты `_Struct_size_bytes_` и `_Field_size_` заметок эквивалентны. Для структур или классов с похожим макетом `_Field_size_` проще в чтении и обслуживании, так как он содержит меньше ссылок и вычислений, чем эквивалентная `_Struct_size_bytes_` Аннотация. `_Field_size_` не требует преобразования к размеру в байтах. Если размер Byte является единственным параметром, например для поля указателя void, можно использовать `_Field_size_bytes_`. Если оба `_Struct_size_bytes_` и `_Field_size_` существуют, они будут доступны для средств. Если две аннотации не согласны, это будет сделано с помощью инструмента.

## <a name="see-also"></a>См. также:

- [Использование аннотаций SAL для уменьшения количества дефектов в коде C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [Основные сведения о языке SAL](../code-quality/understanding-sal.md)
- [Создание примечаний к параметрам и возвращаемым значениям функций](../code-quality/annotating-function-parameters-and-return-values.md)
- [Аннотация поведения функций](../code-quality/annotating-function-behavior.md)
- [Аннотация поведения блокировки](../code-quality/annotating-locking-behavior.md)
- [Указание времени и места применения примечания](../code-quality/specifying-when-and-where-an-annotation-applies.md)
- [Встроенные функции](../code-quality/intrinsic-functions.md)
- [Рекомендации и примеры](../code-quality/best-practices-and-examples-sal.md)
