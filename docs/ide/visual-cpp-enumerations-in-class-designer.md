---
title: "Перечисления Visual C++ в конструкторе классов | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Class Designer [Visual Studio], enumerations
ms.assetid: 11e90ba1-18cd-44f8-9e26-e3746a7a19d1
caps.latest.revision: 10
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 168e14b8f7e913a2dc4656f01f8cc5cc8ff80284
ms.lasthandoff: 04/05/2017

---
# <a name="visual-c-enumerations-in-class-designer"></a>Перечисления Visual C++ в конструкторе классов
Конструктор классов поддерживает типы C++ `enum` и ограниченные типы `enum class`. Ниже представлен пример:  
  
```  
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
 [Working with Visual C++ Code (Class Designer)](../ide/working-with-visual-cpp-code-class-designer.md)  (Работа с кодом Visual C++ (конструктор классов))  
 [Перечисления](/cpp/cpp/enumerations-cpp)
