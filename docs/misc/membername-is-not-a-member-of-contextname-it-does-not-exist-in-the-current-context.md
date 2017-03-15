---
title: "&quot;&lt;имя_члена&gt;&quot; не является членом &quot;&lt;имя_контекста&gt;&quot; и не существует в текущем контексте | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc36557"
  - "bc36557"
helpviewer_keywords: 
  - "BC36557"
ms.assetid: d8671f1c-d545-44da-89b3-7d892e01e8be
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;&lt;имя_члена&gt;&quot; не является членом &quot;&lt;имя_контекста&gt;&quot; и не существует в текущем контексте
Имя несуществующего члена присвоено свойству в объявлении анонимного типа. В приведенном ниже примере `.Prop1` и `.Prop2` являются свойствами анонимного типа. Попытка присвоить значение `.Prop3` свойству `.Prop2` вызывает ошибку.  
  
```vb#  
' Not valid.  
Dim anon1 = New With {.Prop1 = 27, .Prop2 = .Prop3}  
  
' The assignment is valid if the assigned property has been declared   
' and initialized.  
Dim anon2 = New With {.Prop1 = 27, .Prop2 = .Prop1}  
```  
  
 **Идентификатор ошибки:** BC36657  
  
### Исправление ошибки  
  
-   Проверьте код, чтобы определить, что следует присвоить. Имя переменной может быть написано неправильно, или оно требует квалификации, если это свойство другого объекта.  
  
## См. также  
 [Анонимные типы](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types)   
 [Практическое руководство. Выведение имен свойств и типов в объявлениях анонимных типов](../Topic/How%20to:%20Infer%20Property%20Names%20and%20Types%20in%20Anonymous%20Type%20Declarations%20\(Visual%20Basic\).md)