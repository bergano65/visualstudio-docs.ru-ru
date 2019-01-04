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
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 5b9a96f70febc6a33d80557a09cc8bc8e1adf2f4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53938086"
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