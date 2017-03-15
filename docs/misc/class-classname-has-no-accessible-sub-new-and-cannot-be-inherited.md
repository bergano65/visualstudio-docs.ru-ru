---
title: "У класса &quot;&lt;classname&gt;&quot; нет доступного &quot;Sub New&quot;, и его невозможно унаследовать | Microsoft Docs"
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
  - "vbc31399"
  - "BC31399"
helpviewer_keywords: 
  - "BC31399"
ms.assetid: 035b333f-ff6a-4fc4-bd36-82f40b1d8bab
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# У класса &quot;&lt;classname&gt;&quot; нет доступного &quot;Sub New&quot;, и его невозможно унаследовать
Классом используется [Инструкция Inherits](/dotnet/visual-basic/language-reference/statements/inherits-statement) для указания базового класса, но он не может получить доступ к какому\-либо конструктору этого базового класса.  
  
 Это может произойти, если требуемый базовый класс не содержит конструкторы или содержит конструкторы с уровнями доступа, которые предотвращают доступ из другого класса.  
  
 При наследовании класса ваш конструктор должен вызвать конструктор базового класса, используя [MyBase \- delete](http://msdn.microsoft.com/ru-ru/52491d06-6451-4f6f-9aa6-8fab59bbc2b9). Если вы не выполните этот вызов или не запишете явный конструктор, Visual Basic создаст неявный конструктор, который вызовет `MyBase.New()`.  
  
 **Идентификатор ошибки:** BC31399  
  
### Исправление ошибки  
  
1.  Если система управления версиями разрешает вам доступ к требуемому базовому классу, измените уровень доступа по крайней мере одного из конструкторов, чтобы другой класс мог получить доступ к нему.  
  
2.  Если вы не можете изменить уровни доступа конструкторов требуемого базового класса, унаследуйте от другого класса или ни от какого.  
  
## См. также  
 [Инструкция Inherits](/dotnet/visual-basic/language-reference/statements/inherits-statement)   
 [Основы наследования](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)   
 [MyBase \- delete](http://msdn.microsoft.com/ru-ru/52491d06-6451-4f6f-9aa6-8fab59bbc2b9)   
 [Оператор New](/dotnet/visual-basic/language-reference/operators/new-operator)   
 [Уровни доступа в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/access-levels)