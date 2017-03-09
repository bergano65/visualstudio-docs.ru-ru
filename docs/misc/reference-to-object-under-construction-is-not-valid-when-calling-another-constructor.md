---
title: "При вызове другого конструктора ссылки на объект, находящийся в процессе построения, недопустимы | Microsoft Docs"
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
  - "bc31095"
  - "vbc31095"
helpviewer_keywords: 
  - "BC31095"
ms.assetid: 68be49f1-e662-45c7-9998-e0006324535d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# При вызове другого конструктора ссылки на объект, находящийся в процессе построения, недопустимы
Использовалась ссылка на член объекта до того, как конструктор объекта закончил его создание.  
  
 **Идентификатор ошибки:** BC31095  
  
### Исправление ошибки  
  
-   Не используйте ключевые слова `MyBase`, `MyClass` или `Me` при вызове конструктора из другого конструктора.  
  
## См. также  
 [Время существования: создание и уничтожение объектов](../Topic/Object%20Lifetime:%20How%20Objects%20Are%20Created%20and%20Destroyed%20\(Visual%20Basic\).md)   
 [НЕ В СБОРКЕ. Использование конструкторов и деструкторов](http://msdn.microsoft.com/ru-ru/548eebe1-86c4-4377-b2f5-447cb8be3d90)