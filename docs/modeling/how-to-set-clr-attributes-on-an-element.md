---
title: Практическое руководство. Задание атрибутов среды CLR для элемента
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.EditAttributesDialog
helpviewer_keywords:
- Domain-Specific Language, custom attrributes
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: ceca2556e269d554d40e025e5edcb91753149622
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31948916"
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>Практическое руководство. Задание атрибутов среды CLR для элемента
Пользовательские атрибуты — это специальные атрибуты, которые могут быть добавлены элементы домена, фигур, соединители и схемы. Можно добавить любой атрибут, который наследует от `System.Attribute` класса.

### <a name="to-add-a-custom-attribute"></a>Чтобы добавить настраиваемый атрибут

1.  В **обозреватель DSL**, выберите элемент, к которому требуется добавить пользовательский атрибут.

2.  В **свойства** рядом **настраиваемые атрибуты** свойства, нажмите кнопку обзора (**...** ) значок.

     **Изменения атрибутов** откроется диалоговое окно.

3.  В **имя** столбец, нажмите кнопку  **\<добавьте атрибут >** и введите имя атрибута. Нажмите клавишу ВВОД.

4.  Строка с именем атрибута показывает круглые скобки. В этой строке введите тип параметра атрибута (например, `string`), а затем нажмите клавишу ВВОД.

5.  В **свойство Name** столбца, введите соответствующее имя, например, `MyString`.

6.  Нажмите кнопку **ОК**.

     **Настраиваемые атрибуты** свойство теперь отображает атрибут, в следующем формате:

     `[` *AttributeName* `(` *Имя_параметра* `=` *типа* `)]`

## <a name="see-also"></a>См. также

- [Глоссарий инструменты доменного языка](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)