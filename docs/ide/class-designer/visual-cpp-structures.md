---
title: Структуры Visual C++ в конструкторе классов | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: d0621b5a2a82786a41e8d566954f03341affa905
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="visual-c-structures-in-class-designer"></a>Структуры Visual C++ в конструкторе классов
Конструктор классов поддерживает те структуры C++, которые объявлены с использованием ключевого слова `struct`. Ниже представлен пример.  
  
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
|------------------|-------------------------|  
|`struct StructureName {};`|**StructureName**<br /><br /> Структура|  
  
## <a name="see-also"></a>См. также
[Работа с кодом на Visual C++](working-with-visual-cpp-code.md)   
[Классы и структуры](/cpp/cpp/classes-and-structs-cpp)   
[struct](/cpp/cpp/struct-cpp)