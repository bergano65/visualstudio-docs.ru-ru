---
title: Структуры C++ в конструкторе классов
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 65fb4738b3124daf48b501c6db416d3803da32ec
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748907"
---
# <a name="c-structures-in-class-designer"></a>Структуры C++ в конструкторе классов

**Конструктор классов** поддерживает те структуры C++, которые объявлены с использованием ключевого слова `struct`. Ниже представлен пример.

```cpp
struct MyStructure
{
   char a;
   int i;
   long j;
};
```

Дополнительные сведения об использовании типа `struct` см. в статье [struct](/cpp/cpp/struct-cpp).

Фигура структуры C++ на схеме классов выглядит так же, как фигура класса, но при этом она содержит надпись **Структура** и имеет квадратные, а не скругленные углы.

|Элемент кода|Представление конструктора классов|
|------------------| - |
|`struct StructureName {};`|**StructureName**<br /><br /> Структура|

## <a name="see-also"></a>См. также

- [Работа с кодом C++](working-with-visual-cpp-code.md)
- [Классы и структуры](/cpp/cpp/classes-and-structs-cpp)
- [struct](/cpp/cpp/struct-cpp)