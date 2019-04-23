---
title: Практическое руководство. Задание атрибутов среды CLR для элемента | Документация Майкрософт
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 54c3bd854f824818d9656a33ccf30391f750a491
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60080726"
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>Практическое руководство. Задание атрибутов среды CLR для элемента
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Настраиваемые атрибуты являются специальные атрибуты, которые могут быть добавлены элементы домена, фигуры, соединители и схемы. Можно добавить любой атрибут, который наследует от `System.Attribute` класса.  
  
### <a name="to-add-a-custom-attribute"></a>Чтобы добавить настраиваемый атрибут  
  
1. В **обозреватель DSL**, выберите элемент, к которому вы хотите добавить настраиваемый атрибут.  
  
2. В **свойства** окна, рядом с полем **пользовательские атрибуты** свойство, нажмите кнопку обзора (**...** ) значок.  
  
     **Изменения атрибутов** откроется диалоговое окно.  
  
3. В **имя** столбец, нажмите кнопку  **\<добавить атрибут >** и введите имя атрибута. Нажмите клавишу ВВОД.  
  
4. Строка с именем атрибута показывает круглые скобки. В следующей строке введите тип параметра для атрибута (например, `string`), а затем нажмите клавишу ВВОД.  
  
5. В **свойство Name** столбца, введите соответствующее имя, например, `MyString`.  
  
6. Нажмите кнопку **ОК**.  
  
     **Пользовательские атрибуты** свойство теперь отображает атрибут, в следующем формате:  
  
     `[` *AttributeName* `(` *ParameterName* `=` *типа* `)]`  
  
## <a name="see-also"></a>См. также  
 [Глоссарий средств предметно-ориентированных языков](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
