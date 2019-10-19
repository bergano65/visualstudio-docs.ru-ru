---
title: Как задать атрибуты среды CLR для элемента | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.dsltools.EditAttributesDialog
helpviewer_keywords:
- Domain-Specific Language, custom attrributes
ms.assetid: b3db3c74-920c-4701-9544-6f75cbe8b7c9
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 72ad9175729451c82fca3b61d06e449edaf8cf38
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662545"
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>Практическое руководство. Задание атрибутов среды CLR для элемента
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Настраиваемые атрибуты — это специальные атрибуты, которые могут быть добавлены к элементам домена, фигурам, соединителям и схемам. Можно добавить любой атрибут, наследующий от класса `System.Attribute`.

### <a name="to-add-a-custom-attribute"></a>Добавление настраиваемого атрибута

1. В **обозревателе DSL**выберите элемент, к которому необходимо добавить настраиваемый атрибут.

2. В окне **Свойства** рядом со свойством **настраиваемые атрибуты** щелкните значок обзора ( **...** ).

     Откроется диалоговое окно **изменение атрибутов** .

3. В столбце **имя** щелкните **\<add атрибут >** и введите имя атрибута. Нажмите клавишу ВВОД.

4. В строке под именем атрибута указаны круглые скобки. В этой строке введите тип параметра для атрибута (например, `string`) и нажмите клавишу ВВОД.

5. В столбце **имя свойства** введите соответствующее имя, например `MyString`.

6. Нажмите кнопку **ОК**.

     Свойство **настраиваемые атрибуты** теперь отображает атрибут в следующем формате:

     `[` *AttributeName* `(` *тип* `=` *ParameterName* `)]`

## <a name="see-also"></a>См. также раздел
 [Глоссарий средств предметно-ориентированных языков](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
