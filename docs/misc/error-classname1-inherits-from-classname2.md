---
title: "&lt;ошибка&gt;: &quot;&lt;имя_класса1&gt;&quot; наследует от &quot;&lt;имя_класса2&gt;&quot; | Microsoft Docs"
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
  - "bc30256"
  - "vbc30256"
helpviewer_keywords: 
  - "BC30256"
ms.assetid: 170a12ee-87ef-4a49-8c84-ebf57fac435e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;ошибка&gt;: &quot;&lt;имя_класса1&gt;&quot; наследует от &quot;&lt;имя_класса2&gt;&quot;
Обнаружена циклическая иерархия наследования. Класс задан как наследующий от себя самого или от другого класса, который прямо или косвенно наследует от этого класса.  
  
 Это сообщение может появиться несколько раз, чтобы проследить путь циклического наследования.  
  
 **Идентификатор ошибки:** BC30256  
  
### Исправление ошибки  
  
-   Прервите это циклическое наследование, удалив по крайней мере один оператор `Inherits` в пути циклического наследования.  
  
## См. также  
 [Основы наследования](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)