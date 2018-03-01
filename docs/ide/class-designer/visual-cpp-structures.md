---
title: "Структуры Visual C++ в конструкторе классов | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d6f2aa3893a230abd52dd5cf19ed9d751e56e50c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
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