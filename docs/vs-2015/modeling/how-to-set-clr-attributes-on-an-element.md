---
title: 'Практическое: Задание атрибутов среды CLR для элемента | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.dsltools.EditAttributesDialog
helpviewer_keywords:
- Domain-Specific Language, custom attrributes
ms.assetid: b3db3c74-920c-4701-9544-6f75cbe8b7c9
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: afcbadd7c7b3a18c94228e7221eda32b7117a2ed
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47557928"
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>Практическое руководство. Задание атрибутов среды CLR для элемента
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как: задать атрибуты среды CLR для элемента](https://docs.microsoft.com/visualstudio/modeling/how-to-set-clr-attributes-on-an-element).  
  
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
 [Глоссарий по средствам доменного языка работы](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)



