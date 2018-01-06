---
title: "Как: установить атрибуты среды CLR на элемент | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.dsltools.EditAttributesDialog
helpviewer_keywords: Domain-Specific Language, custom attrributes
ms.assetid: b3db3c74-920c-4701-9544-6f75cbe8b7c9
caps.latest.revision: "19"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: d18a19debb8208c53d23bc5c187e0044a1303f08
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
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
  
     `[`*AttributeName* `(` *Имя_параметра* `=` *тип*`)]`  
  
## <a name="see-also"></a>См. также  
 [Глоссарий инструменты доменного языка](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)