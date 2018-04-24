---
title: Перечисления Visual C++ в конструкторе классов | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], enumerations
ms.assetid: 11e90ba1-18cd-44f8-9e26-e3746a7a19d1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: ac804f35c2d917e5443e61d4f2e53cde81165070
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="visual-c-enumerations-in-class-designer"></a>Перечисления Visual C++ в конструкторе классов
Конструктор классов поддерживает типы C++ `enum` и ограниченные типы `enum class`. Ниже представлен пример.  
  
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
[Работа с кодом на Visual C++](working-with-visual-cpp-code.md)   
[Перечисления](/cpp/cpp/enumerations-cpp)