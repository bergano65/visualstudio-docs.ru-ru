---
title: "Класс &quot;&lt;имя_класса1&gt;&quot; не может наследовать от &lt;тип&gt; &quot;&lt;имя_класса2&gt;&quot;, поскольку класс &quot;&lt;имя_класса2&gt;&quot; объявлен как NotInheritable. | Microsoft Docs"
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
  - "vbc30299"
  - "bc30299"
helpviewer_keywords: 
  - "BC30299"
ms.assetid: 627d50f5-9e75-495d-93f7-50096ba2ea08
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Класс &quot;&lt;имя_класса1&gt;&quot; не может наследовать от &lt;тип&gt; &quot;&lt;имя_класса2&gt;&quot;, поскольку класс &quot;&lt;имя_класса2&gt;&quot; объявлен как NotInheritable.
Класс пытается наследовать от другого класса, однако нужный базовый класс был определен как `NotInheritable`. Классы `NotInheritable` используются в основном для предотвращения случайного наследования.  
  
 **Идентификатор ошибки:** BC30299  
  
### Исправление ошибки  
  
-   Удалите ключевое слово `NotInheritable` из определения нужного базового класса или удалите оператор `Inherits`.  
  
## См. также  
 [Основы наследования](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)   
 [NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable)   
 [Инструкция Inherits](/dotnet/visual-basic/language-reference/statements/inherits-statement)