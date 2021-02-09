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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8e566eafce9b5763830c00659a860e6329671bcd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99922656"
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

6. Нажмите кнопку **OK**.

     Свойство **настраиваемые атрибуты** теперь отображает атрибут в следующем формате:

     `[`*AttributeName* `(` *ParameterName* `=` *Тип*`)]`

## <a name="see-also"></a>См. также раздел

- [Глоссарий средств предметно-ориентированных языков](/previous-versions/bb126564(v=vs.100))