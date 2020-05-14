---
title: Структуры C++ в конструкторе классов
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 2aa8014835df2b5b2bd3dc68e2aaf0b079e001e8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590688"
---
# <a name="c-structures-in-class-designer"></a>Структуры C++ в конструкторе классов

**Конструктор классов** поддерживает те структуры C++, которые объявлены с использованием ключевого слова `struct`. Ниже приведен пример:

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

## <a name="see-also"></a>См. также раздел

- [Работа с кодом C++](working-with-visual-cpp-code.md)
- [Классы и структуры](/cpp/cpp/classes-and-structs-cpp)
- [struct](/cpp/cpp/struct-cpp)
