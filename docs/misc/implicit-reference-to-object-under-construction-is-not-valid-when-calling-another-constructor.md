---
title: "При вызове другого конструктора неявные ссылки на объект, находящийся в процессе построения, недопустимы. | Microsoft Docs"
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
  - "vbc31096"
  - "bc31096"
helpviewer_keywords: 
  - "BC31096"
ms.assetid: 558a2beb-aa5d-41a8-8655-ad3d16ac8acd
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# При вызове другого конструктора неявные ссылки на объект, находящийся в процессе построения, недопустимы.
Использовалась ссылка на член объекта до того, как конструктор объекта создал этот объект.  
  
 **Идентификатор ошибки:** BC31096  
  
### Исправление ошибки  
  
-   Не используйте ключевые слова `MyBase`, `MyClass` или `Me` при вызове конструктора из другого конструктора.  
  
## См. также  
 [Время существования: создание и уничтожение объектов](../Topic/Object%20Lifetime:%20How%20Objects%20Are%20Created%20and%20Destroyed%20\(Visual%20Basic\).md)   
 [НЕ В СБОРКЕ. Использование конструкторов и деструкторов](http://msdn.microsoft.com/ru-ru/548eebe1-86c4-4377-b2f5-447cb8be3d90)