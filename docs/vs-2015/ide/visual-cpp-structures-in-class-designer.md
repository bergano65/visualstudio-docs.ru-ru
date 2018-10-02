---
title: Структуры Visual C++ в конструкторе классов | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a701aae6e9c504d24d149dd5941a0f9623111ce2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47559638"
---
# <a name="visual-c-structures-in-class-designer"></a>Структуры Visual C++ в конструкторе классов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [структуры Visual C++ в конструкторе классов](https://docs.microsoft.com/visualstudio/ide/visual-cpp-structures-in-class-designer).  
  
Конструктор классов поддерживает те структуры C++, которые объявлены с использованием ключевого слова `struct`. Ниже представлен пример.  
  
```  
struct MyStructure  
{  
   char a;  
   int i;  
   long j;  
};  
```  
  
 Дополнительные сведения об использовании типа `struct` см. в статье [struct](http://msdn.microsoft.com/library/3c6ba273-e248-4ff1-8c69-d2abcf1263c6).  
  
 Фигура структуры C++ на схеме классов выглядит так же, как фигура класса, но при этом она содержит надпись **Структура** и имеет квадратные, а не скругленные углы.  
  
|Элемент кода|Представление конструктора классов|  
|------------------|-------------------------|  
|`struct StructureName {};`|**StructureName**<br /><br /> Структура|  
  
## <a name="see-also"></a>См. также  
 [Working with Visual C++ Code (Class Designer)](../ide/working-with-visual-cpp-code-class-designer.md)  (Работа с кодом Visual C++ (конструктор классов))  
 [Классы и структуры](http://msdn.microsoft.com/library/516dd496-13fb-4f17-845a-e9ca45437873)   
 [struct](http://msdn.microsoft.com/library/3c6ba273-e248-4ff1-8c69-d2abcf1263c6)



