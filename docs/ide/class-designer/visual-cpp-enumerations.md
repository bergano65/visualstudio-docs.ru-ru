---
title: Перечисления Visual C++ в конструкторе классов
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], enumerations
ms.assetid: 11e90ba1-18cd-44f8-9e26-e3746a7a19d1
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: d5f02d899c9d81c8dd19aac879bed7ac9c1acdb8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54946832"
---
# <a name="visual-c-enumerations-in-class-designer"></a>Перечисления Visual C++ в конструкторе классов

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

- [Работа с кодом на Visual C++](working-with-visual-cpp-code.md)
- [Перечисления](/cpp/cpp/enumerations-cpp)