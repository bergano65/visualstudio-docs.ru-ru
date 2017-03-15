---
title: "Нельзя задавать MustOverride в &quot;&lt;имя_процедуры&gt;&quot;, поскольку он находится в разделяемом типе, объявленном как NotInheritable в другом частичном определении. | Microsoft Docs"
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
  - "vbc30927"
  - "BC30927"
helpviewer_keywords: 
  - "BC30927"
ms.assetid: 5798dfda-3d7b-4f30-9715-40cbf52d6dc4
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Нельзя задавать MustOverride в &quot;&lt;имя_процедуры&gt;&quot;, поскольку он находится в разделяемом типе, объявленном как NotInheritable в другом частичном определении.
Процедура или свойство объявляется как `MustOverride` в классе, который определен в нескольких частичных объявлениях, но одно из частичных определений задает `NotInheritable` для этого класса.  
  
 После разделения определения класса на несколько частичных объявлений компилятор обрабатывает класс как объединение всех частичных объявлений. Это относится не только к членам, но и к реализации, наследованию и уровню доступа.  
  
 Чтобы переопределить процедуру или свойство, класс должен унаследовать этот объект от базового класса. Таким образом, чтобы указать `MustOverride` для процедуры или свойства в базовом классе, необходимо указать `MustInherit` для этого класса. Поскольку эти ключевые слова противоречат друг другу, вы не можете указать и `MustInherit`, и `NotInheritable` для одного и того же класса.  
  
 **Идентификатор ошибки:** BC30927  
  
### Исправление ошибки  
  
-   Если свойство или процедуру необходимо переопределить, удалите ключевое слово `NotInheritable` из частичного объявления, в котором оно находится.  
  
-   Если класс должен быть `NotInheritable`, удалите ключевое слово `MustOverride` из процедуры или свойства. Его нельзя переопределить, поскольку нельзя наследовать этот класс.  
  
## См. также  
 [Partial](/dotnet/visual-basic/language-reference/modifiers/partial)   
 [MustOverride](/dotnet/visual-basic/language-reference/modifiers/mustoverride)   
 [MustInherit](/dotnet/visual-basic/language-reference/modifiers/mustinherit)   
 [NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable)   
 [Основы наследования](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)