---
title: "Практическое руководство: Задание атрибутов среды CLR в элементе | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.dsltools.EditAttributesDialog
helpviewer_keywords:
- Domain-Specific Language, custom attrributes
ms.assetid: b3db3c74-920c-4701-9544-6f75cbe8b7c9
caps.latest.revision: 19
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 7dcbd0005b80887dae91249a6781a6982414b9e5
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-set-clr-attributes-on-an-element"></a>Практическое руководство. Задание атрибутов среды CLR для элемента
Пользовательские атрибуты — это специальные атрибуты, которые могут быть добавлены элементы домена, фигуры, соединители и схемы. Можно добавить любой атрибут, который наследует от `System.Attribute` класса.  
  
### <a name="to-add-a-custom-attribute"></a>Добавление настраиваемого атрибута  
  
1.  В **обозреватель DSL**, выберите элемент, к которому требуется добавить пользовательский атрибут.  
  
2.  В **свойства** рядом **пользовательские атрибуты** свойства, нажмите кнопку обзора (**... **) icon.  
  
     **Изменения атрибутов** откроется диалоговое окно.  
  
3.  В **имя** столбец, нажмите кнопку ** \<добавьте атрибут настроек** и введите имя атрибута. Нажмите клавишу ВВОД.  
  
4.  Строка с именем атрибута показывает круглые скобки. В этой строке введите тип параметра для атрибута (например, `string`), а затем нажмите клавишу ВВОД.  
  
5.  В **свойство Name** столбец, введите соответствующее имя, например `MyString`.  
  
6.  Нажмите кнопку **ОК**.  
  
     **Пользовательские атрибуты** свойство теперь отображает атрибут в следующем формате:  
  
     `[`*AttributeName* `(` *ParameterName* `=` *Type*`)]`  
  
## <a name="see-also"></a>См. также  
 [Глоссарий по средствам доменного языка](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)
