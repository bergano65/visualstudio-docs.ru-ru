---
title: "Не удается инициализировать член &quot;&lt;имя_члена&gt;&quot; в выражении инициализатора объекта, поскольку он не является полем или свойством | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30990"
  - "vbc30990"
helpviewer_keywords: 
  - "BC30990"
ms.assetid: 3be2c135-20f6-49b2-a324-d213cfdf9ee3
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Не удается инициализировать член &quot;&lt;имя_члена&gt;&quot; в выражении инициализатора объекта, поскольку он не является полем или свойством
Список инициализаторов объектов не может содержать общие члены, константы или вызовы методов. Элементы в списке инициализаторов должны быть полями или свойствами, и члены свойств не должны требовать аргументы.  
  
 **Идентификатор ошибки:** BC30990  
  
### Исправление ошибки  
  
-   Удалите из списка инициализаторов объектов все общие члены, константы, вызовы методов или свойства, имеющие параметры.  
  
## См. также  
 [Инициализаторы объектов: именованные и анонимные типы](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [НЕ В СБОРКЕ. Общие члены в Visual Basic](http://msdn.microsoft.com/ru-ru/dbc3783f-83a2-4225-995d-c2d6d025663d)   
 [НЕ В СБОРКЕ. Свойства и процедуры свойств](http://msdn.microsoft.com/ru-ru/23e2a1ec-7e9d-4109-8940-c703d981077b)   
 [НЕ В СБОРКЕ. Свойства по умолчанию](http://msdn.microsoft.com/ru-ru/a70f2a27-8176-4858-935e-f25afdd43ab5)   
 [NotInBuild. Члены объекта](http://msdn.microsoft.com/ru-ru/dfc2cc12-0e66-44fb-a78e-14f931db2309)   
 [Оператор Const](/dotnet/visual-basic/language-reference/statements/const-statement)