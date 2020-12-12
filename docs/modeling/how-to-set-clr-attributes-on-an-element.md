---
title: Практическое руководство. Задание атрибутов среды CLR для элемента
description: Узнайте, как можно добавить любой атрибут, наследуемый от класса System. Attribute.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.EditAttributesDialog
helpviewer_keywords:
- Domain-Specific Language, custom attrributes
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: df9f8b16edcbe575ebac67f4acde9111a9511b85
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363852"
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>Практическое руководство. Задание атрибутов среды CLR для элемента
Настраиваемые атрибуты — это специальные атрибуты, которые могут быть добавлены к элементам домена, фигурам, соединителям и схемам. Можно добавить любой атрибут, наследующий от `System.Attribute` класса.

### <a name="to-add-a-custom-attribute"></a>Добавление настраиваемого атрибута

1. В **обозревателе DSL** выберите элемент, к которому необходимо добавить настраиваемый атрибут.

2. В окне **Свойства** рядом со свойством **настраиваемые атрибуты** щелкните значок обзора (**...**).

     Откроется диалоговое окно **изменение атрибутов** .

3. В столбце **имя** щелкните **\<add attribute>** и введите имя атрибута. Нажмите клавишу ВВОД.

4. В строке под именем атрибута указаны круглые скобки. В этой строке введите тип параметра для атрибута (например, `string` ), а затем нажмите клавишу ВВОД.

5. В столбце **имя свойства** введите соответствующее имя, например `MyString` .

6. Нажмите кнопку **ОК**.

     Свойство **настраиваемые атрибуты** теперь отображает атрибут в следующем формате:

     `[`*AttributeName* `(` *ParameterName* `=` *Тип*`)]`

## <a name="see-also"></a>См. также раздел

- [Глоссарий средств предметно-ориентированных языков](/previous-versions/bb126564(v=vs.100))