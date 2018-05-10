---
title: Операторы typedef языка Visual C++ в конструкторе классов
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
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
ms.openlocfilehash: 8ce99a4e4c4899502bf1f63edf2dbc1ad0c93cd0
ms.sourcegitcommit: 56018fb1f52f17bf35ae2ce71c50c763486e6173
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="visual-c-typedefs-in-class-designer"></a>Определения типов Visual C++ в конструкторе классов

Операторы typedef создают один или несколько уровней косвенного обращения между именем и его базовым типом. **Конструктор классов** поддерживает те определения типов C++, которые объявлены с ключевым словом `typedef`, например:

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

Несмотря на то, что можно объявить определение типа без имени, **конструктор классов** не будет использовать указываемое имя тега. Он будет использовать имя, созданное представлением классов. Например, следующее объявление является допустимым, но оно отображается в **представлении классов** и **конструкторе классов** как объект с именем **__unnamed**:

```cpp
typedef class coord
{
   void P(x,y);
   unsigned x;
   unsigned y;
};
```

Дополнительные сведения об использовании типа `typedef` см. в разделе о [Typedefs](/cpp/cpp/aliases-and-typedefs-cpp#typedefs).

Фигура определения типа C++ имеет форму типа, указанного в определении типа. Например, если источник объявляет `typedef class`, у фигуры будут скругленные углы и метка **класса**. У `typedef struct` фигура имеет квадратные углы и метку **Структура**.

Классы и структуры могут иметь вложенные определения типов, объявленные в них. Таким образом, фигуры классов и структур могут отображать объявления вложенных определений типов как вложенные фигуры.

Фигуры определения типов поддерживают команды **Показывать как ассоциацию** и **Показывать как ассоциацию наборов** контекстного меню.

Ниже приведено несколько примеров типов typdef, которые поддерживает **конструктор классов**.

`typedef type name`

*имя*: *тип*

typedef

Рисует линию связи к типу *имя*, если это возможно.

`typedef void (*func)(int)`

`func: void (*)(int)`

typedef

Typedef для указателей на функции. Линия связи не рисуется.

**Конструктор классов** не отображает определение типа, если его исходный тип является указателем на функцию.

```cpp
typedef int MyInt;
class A {
   MyInt I;
};
```

`MyInt: int`

typedef

`A`

Класс

Рисует линию связи от фигуры исходного типа к фигуре целевого типа.

`Class B {};`

`typedef B MyB;`

`B`

Класс

`MyB : B`

typedef

При щелчке фигуры typedef правой кнопкой мыши и выборе команды **Показывать как ассоциацию** отображается определение типа или класс и **псевдоним** линии, соединяющей две фигуры (похожа на линию ассоциации).

`typedef B MyB;`

`typedef MyB A;`

`MyBar : Bar`

typedef

То же, что и выше.

```cpp
Class B {};
typedef B MyB;

class A {
   MyB B;
};
```

`B`

Класс

`MyB : B`

typedef

`A`

Класс

`MyB` является фигурой вложенного типа typedef.

`#include <vector>`

`...`

`using namespace std;`

`...`

`typedef vector<int> MyIntVect;`

`vector<T>`Класс

`MyIntVect : vector<int>`

typedef

`class B {};`

`typedef B MyB;`

`class A : MyB {};`

`MyB : B`

typedef

-> B

`B`

`A`

Класс

-> MyB

**Конструктор классов** не поддерживает отображение такого вида отношений с помощью команды контекстного меню.

`#include <vector>`

`Typedef MyIntVect std::vector<int>;`

`Class MyVect : MyIntVect {};`

`std::vector<T>`

Класс

`MyIntVect : std::vector<int>`

typedef

`MyVect`

Класс

-> MyIntVect

### <a name="see-also"></a>См. также

- [Работа с кодом на Visual C++](working-with-visual-cpp-code.md)  
- [Typedefs](/cpp/cpp/aliases-and-typedefs-cpp#typedefs)

