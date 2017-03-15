---
title: "Данное наследование приводит к циклической зависимости между &lt;тип1&gt; &quot;&lt;имя_типа1&gt;&quot; и вложенным в него &lt;тип2&gt; &quot;&lt;имя_типа2&gt;&quot;. | Microsoft Docs"
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
  - "vbc30907"
  - "bc30907"
helpviewer_keywords: 
  - "BC30907"
ms.assetid: 17d4f938-5895-4d33-943e-8abf0ceacdc9
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Данное наследование приводит к циклической зависимости между &lt;тип1&gt; &quot;&lt;имя_типа1&gt;&quot; и вложенным в него &lt;тип2&gt; &quot;&lt;имя_типа2&gt;&quot;.
Структура наследования приводит к циклической зависимости между вложенными классами, то есть к двум классам, наследующим друг друга.  
  
 К этой ошибке может привести следующий код.  
  
```  
Public Class c1 Inherits c3.c4 Public Class c2 End Class End Class Public Class c3 Inherits c1.c2 Public Class c4 End Class End Class  
```  
  
 В приведенном выше коде класс `c1` наследует от класса `c4`, но класс `c4` вложен в класс `c3`, который наследует от класса `c2`, вложенного в `c1`.  
  
 **Идентификатор ошибки:** BC30907  
  
### Исправление ошибки  
  
-   Измените структуру наследования таким образом, чтобы исключить циклическую зависимость.  
  
## См. также  
 [Основы наследования](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)