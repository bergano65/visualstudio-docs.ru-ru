---
title: Структуры Visual C++ в конструкторе классов | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fc9c09c5f92c4193d3d3f58c819f4bc0fc9aaebf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72646767"
---
# <a name="visual-c-structures-in-class-designer"></a>Структуры Visual C++ в конструкторе классов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Конструктор классов поддерживает те структуры C++, которые объявлены с использованием ключевого слова `struct`. Ниже приведен пример:

```
struct MyStructure
{
   char a;
   int i;
   long j;
};
```

 Дополнительные сведения об использовании типа `struct` см. в статье [struct](https://msdn.microsoft.com/library/3c6ba273-e248-4ff1-8c69-d2abcf1263c6).

 Фигура структуры C++ на схеме классов выглядит так же, как фигура класса, но при этом она содержит надпись **Структура** и имеет квадратные, а не скругленные углы.

|Code, элемент|Представление конструктора классов|
|------------------|-------------------------|
|`struct StructureName {};`|**StructureName**<br /><br /> Структура|

## <a name="see-also"></a>См. также:
 Работа с [структурами](https://msdn.microsoft.com/library/3c6ba273-e248-4ff1-8c69-d2abcf1263c6) [классов и](https://msdn.microsoft.com/library/516dd496-13fb-4f17-845a-e9ca45437873) структур [Visual C++ Code (конструктор классов)](../ide/working-with-visual-cpp-code-class-designer.md)
