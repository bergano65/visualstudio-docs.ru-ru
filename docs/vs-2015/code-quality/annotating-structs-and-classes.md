---
title: Аннотация структур и классов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
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
ms.assetid: b8278a4a-c86e-4845-aa2a-70da21a1dd52
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: jillfra
ms.openlocfilehash: 42e9e050fb6417914d25e25927a248557e7905f8
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58990804"
---
# <a name="annotating-structs-and-classes"></a>Аннотация структур и классов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Вы можете добавить примечание к структурам и членам классов, используя примечания, которые действуют как инварианты — предполагается, что они будут выполнены в любом вызове функции или функции входа и выхода, которая содержит включающую структуру в качестве значения параметров или результатов.  
  
## <a name="struct-and-class-annotations"></a>Структура и класс заметки  
  
-   `_Field_range_(low, high)`  
  
     Поле находится в диапазоне (включительно) из `low` для `high`.  Эквивалент для `_Satisfies_(_Curr_ >= low && _Curr_ <= high)` применяется к аннотированному объекту с помощью соответствующих предусловий или постусловий.  
  
-   `_Field_size_(size)`, `_Field_size_opt_(size)`, `_Field_size_bytes_(size)`, `_Field_size_bytes_opt_(size)`  
  
     Поле с записываемым размером в элементах (или байтах), как определено в `size`.  
  
-   `_Field_size_part_(size, count)`, `_Field_size_part_opt_(size, count)`,         `_Field_size_bytes_part_(size, count)`, `_Field_size_bytes_part_opt_(size, count)`  
  
     Поле с записываемым размером в элементах (или байтах), как определено в `size` и `count` этих элементов (байт), которые доступны для чтения.  
  
-   `_Field_size_full_(size)`, `_Field_size_full_opt_(size)`, `_Field_size_bytes_full_(size)`, `_Field_size_bytes_full_opt_(size)`  
  
     Поле с размером в элементах (или байт), доступных для записи и чтения, как определено в `size`.  
  
-   `_Struct_size_bytes_(size)`  
  
     Поле с размером в элементах (или байт), доступных для записи и чтения, как определено в `size`.  
  
     Применяется к объявлению структуры или класса.  Указывает, что допустимый объект этого типа может быть больше объявленного типа с количеством байт, указанным в `size`.  Пример:  
  
    ```cpp  
  
    typedef _Struct_size_bytes_(nSize)  
    struct MyStruct {  
        size_t nSize;  
        …  
    };  
  
    ```  
  
     Размер буфера в байтах параметра `pM` типа `MyStruct *` затем принимается:  
  
    ```cpp  
    min(pM->nSize, sizeof(MyStruct))  
    ```  
  
## <a name="see-also"></a>См. также  
 [Использование аннотаций SAL для сокращения количества дефектов в коде C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Основные сведения о SAL](../code-quality/understanding-sal.md)   
 [Создание примечаний к функции параметров и возвращаемых значений](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Аннотация поведения функций](../code-quality/annotating-function-behavior.md)   
 [Аннотация поведения блокировки](../code-quality/annotating-locking-behavior.md)   
 [Указание времени и места применения примечания](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Встроенные функции](../code-quality/intrinsic-functions.md)   
 [Рекомендации и примеры](../code-quality/best-practices-and-examples-sal.md)
