---
title: Операторы typedef языка Visual C++ в конструкторе классов | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.typedef
- vs.classdesigner.aliasofline
helpviewer_keywords:
- Class Designer [Visual Studio], typedefs
ms.assetid: c1984108-71fc-4d3a-b4d4-3eac2c6b4ebf
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 980c49aafba55e29714d786e492f7bb37a8ca621
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646752"
---
# <a name="visual-c-typedefs-in-class-designer"></a>Операторы typedef языка Visual C++ в конструкторе классов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Операторы typedef создают один или несколько уровней косвенного обращения между именем и его базовым типом. Конструктор классов поддерживает те определения типов C++, которые объявлены с ключевым словом `typedef`, например:

```
typedef class coord
{
   void P(x,y);
   unsigned x;
   unsigned y;
} COORD;
```

 Затем можно использовать этот тип для объявления экземпляра:

 `COORD OriginPoint;`

 Несмотря на то, что можно объявить определение типа без имени, конструктор классов не будет использовать указываемое имя тега. Он будет использовать имя, созданное представлением классов. Например, следующее объявление является допустимым, но оно отображается в представлении классов и конструкторе классов как объект с именем **__unnamed**:

```
typedef class coord
{
   void P(x,y);
   unsigned x;
   unsigned y;
};
```

 Дополнительные сведения об использовании `typedef` см. в статье [Спецификатор typedef](https://msdn.microsoft.com/cc96cf26-ba93-4179-951e-695d1f5fdcf1).

 Фигура определения типа C++ имеет форму типа, указанного в определении типа. Например, если источник объявляет `typedef class`, у фигуры будут скругленные углы и метка **класса**. У `typedef struct` фигура имеет квадратные углы и метку **Структура**.

 Классы и структуры могут иметь вложенные определения типов, объявленные в них. Таким образом, фигуры классов и структур могут отображать объявления вложенных определений типов как вложенные фигуры.

 Фигуры определения типов поддерживают команды **Показывать как ассоциацию** и **Показывать как ассоциацию наборов** контекстного меню.

 Ниже приведено несколько примеров типов typedef, которые поддерживает конструктор классов.

 `typedef type name`

 *имя*: *тип*

 typedef

 Рисует линию связи к типу *имя*, если это возможно.

 `typedef void (*func)(int)`

 `func: void (*)(int)`

 typedef

 Typedef для указателей на функции. Линия связи не рисуется.

 Конструктор классов не отображает typedef, если его исходный тип является указателем на функцию.

```
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

```
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

 Конструктор классов не поддерживает отображение такого вида отношений с помощью команды контекстного меню.

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

## <a name="see-also"></a>См. также
 Работа с [описателем typedef](https://msdn.microsoft.com/cc96cf26-ba93-4179-951e-695d1f5fdcf1) [ C++ визуального кода (конструктор классов)](../ide/working-with-visual-cpp-code-class-designer.md) (сборке)
