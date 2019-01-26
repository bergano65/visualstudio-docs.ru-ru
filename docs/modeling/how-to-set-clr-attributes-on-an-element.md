---
title: Как выполнить Задание атрибутов среды CLR для элемента
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.EditAttributesDialog
helpviewer_keywords:
- Domain-Specific Language, custom attrributes
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 54b4340fe72552f3287a5c6ebec55c9c9d326ac1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54932276"
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>Как выполнить Задание атрибутов среды CLR для элемента
Настраиваемые атрибуты являются специальные атрибуты, которые могут быть добавлены элементы домена, фигуры, соединители и схемы. Можно добавить любой атрибут, который наследует от `System.Attribute` класса.

### <a name="to-add-a-custom-attribute"></a>Чтобы добавить настраиваемый атрибут

1.  В **обозреватель DSL**, выберите элемент, к которому вы хотите добавить настраиваемый атрибут.

2.  В **свойства** окна, рядом с полем **пользовательские атрибуты** свойство, нажмите кнопку обзора (**...** ) значок.

     **Изменения атрибутов** откроется диалоговое окно.

3.  В **имя** столбец, нажмите кнопку  **\<добавить атрибут >** и введите имя атрибута. Нажмите клавишу ВВОД.

4.  Строка с именем атрибута показывает круглые скобки. В следующей строке введите тип параметра для атрибута (например, `string`), а затем нажмите клавишу ВВОД.

5.  В **свойство Name** столбца, введите соответствующее имя, например, `MyString`.

6.  Нажмите кнопку **ОК**.

     **Пользовательские атрибуты** свойство теперь отображает атрибут, в следующем формате:

     `[` *AttributeName* `(` *ParameterName* `=` *типа* `)]`

## <a name="see-also"></a>См. также

- [Глоссарий по средствам доменного языка работы](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)