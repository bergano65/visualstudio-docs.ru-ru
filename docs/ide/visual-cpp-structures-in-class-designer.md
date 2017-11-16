---
title: "Структуры Visual C++ в конструкторе классов | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 85e2068e00f2164b44feb9aae61a47de426be735
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="visual-c-structures-in-class-designer"></a>Структуры Visual C++ в конструкторе классов
Конструктор классов поддерживает те структуры C++, которые объявлены с использованием ключевого слова `struct`. Ниже представлен пример:  
  
```  
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
 [Working with Visual C++ Code (Class Designer)](../ide/working-with-visual-cpp-code-class-designer.md)  (Работа с кодом Visual C++ (конструктор классов))  
 [Классы и структуры](/cpp/cpp/classes-and-structs-cpp)   
 [struct](/cpp/cpp/struct-cpp)