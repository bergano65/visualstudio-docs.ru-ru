---
title: Перечисления C++ в конструкторе классов
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], enumerations
ms.assetid: 11e90ba1-18cd-44f8-9e26-e3746a7a19d1
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: ee56850c05e4b06ea4325ec238e56e99b38978d0
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114198"
---
# <a name="c-enumerations-in-class-designer"></a>Перечисления C++ в конструкторе классов

**Конструктор классов** поддерживает типы C++ `enum` и типы `enum class` с областью видимости. Ниже представлен пример.

```cpp
enum CardSuit {
   Diamonds = 1,
   Hearts = 2,
   Clubs = 3,
   Spades = 4
};

// or...
enum class CardSuit {
   Diamonds = 1,
   Hearts = 2,
   Clubs = 3,
   Spades = 4
};
```

Фигура перечисления C++ в схеме классов выглядит и работает подобно фигуре структуры, за исключением того, что она называется **Перечисление** или **Класс перечисления**, имеет розовый, а не синий цвет, и располагает цветной границей на левом и верхнем полях. Фигуры перечисления и структуры имеют прямые углы.

Дополнительные сведения об использовании типа `enum` см. в статье [Enumerations](/cpp/cpp/enumerations-cpp) (Перечисления).

## <a name="see-also"></a>См. также

- [Работа с кодом C++](working-with-visual-cpp-code.md)
- [Перечисления](/cpp/cpp/enumerations-cpp)
