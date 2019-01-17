---
title: Операторы typedef языка Visual C++ в конструкторе классов
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.typedef
- vs.classdesigner.aliasofline
helpviewer_keywords:
- Class Designer [Visual Studio], typedefs
ms.assetid: c1984108-71fc-4d3a-b4d4-3eac2c6b4ebf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: d0efbf39ec7000055bdaa978eab06417dae8b183
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53869194"
---
# <a name="visual-c-typedefs-in-class-designer"></a>Определения типов Visual C++ в конструкторе классов

Операторы [typedef](/cpp/cpp/aliases-and-typedefs-cpp#typedefs) создают один или несколько уровней косвенного обращения между именем и его базовым типом. **Конструктор классов** поддерживает те определения типов C++, которые объявлены с ключевым словом `typedef`, например:

```cpp
typedef class coord
{
   void P(x,y);
   unsigned x;
   unsigned y;
} COORD;
```

Затем можно использовать этот тип для объявления экземпляра:

`COORD OriginPoint;`

## <a name="class-and-struct-shapes"></a>Фигуры для классов и структур

В **конструкторе классов** определение типа C++ имеет форму типа, указанного в определении типа. Если источник объявляет `typedef class`, у фигуры будут скругленные углы и метка **класса**. У `typedef struct` фигура имеет квадратные углы и метку **Структура**.

Классы и структуры могут иметь вложенные определения типов, объявленные внутри них. В **конструкторе классов** фигуры классов и структур могут отображать вложенные объявления определений типов в виде вложенных фигур.

Фигуры определения типов поддерживают команды **Показывать как ассоциацию** и **Показывать как ассоциацию наборов** контекстного меню.

### <a name="class-typedef-example"></a>Пример определения типа класса

```cpp
class B {};
typedef B MyB;
```

![Определение типа класса C++ в конструкторе классов](media/cpp-class-typedef.png)

### <a name="struct-typedef-example"></a>Пример определения типа структуры

```cpp
typedef struct mystructtag
{
    int   i;
    double f;
} mystruct;
```

![Определение типа структуры C++ в конструкторе классов](media/cpp-struct-typedef.png)

## <a name="unnamed-typedefs"></a>Неименованные определения типов

Несмотря на то, что можно объявить определение типа без имени, **конструктор классов** не будет использовать указываемое имя тега. **Конструктор классов** будет использовать имя, созданное в **представлении классов**. Например, следующее объявление является допустимым, но оно отображается в **представлении классов** и **конструкторе классов** как объект с именем **__unnamed**:

```cpp
typedef class coord
{
   void P(x,y);
   unsigned x;
   unsigned y;
};
```

> [!NOTE]
> **Конструктор классов** не отображает определение типа, если его исходный тип является указателем на функцию.

## <a name="see-also"></a>См. также

- [Работа с кодом на Visual C++](working-with-visual-cpp-code.md)
- [Typedefs](/cpp/cpp/aliases-and-typedefs-cpp#typedefs)