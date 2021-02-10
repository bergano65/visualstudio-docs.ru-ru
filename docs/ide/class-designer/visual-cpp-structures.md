---
title: Структуры C++ в конструкторе классов
description: Сведения о поддержке структур C++, объявленных с помощью ключевого слова struct, в конструкторе классов.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: 3ca35f9e1c3c1340330ddbbe36ede540fe1e547d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879960"
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
