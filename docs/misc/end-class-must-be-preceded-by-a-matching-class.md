---
title: "Оператору &quot;End Class&quot; должен предшествовать соответствующий оператор &quot;Class&quot; | Microsoft Docs"
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
  - "vbc30460"
  - "bc30460"
helpviewer_keywords: 
  - "BC30460"
ms.assetid: 0e6989da-f281-4ac4-8579-b6d627be8de8
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Оператору &quot;End Class&quot; должен предшествовать соответствующий оператор &quot;Class&quot;
Оператор `End Class` используется для завершения блока `Class`, поэтому он может присутствовать только в конце блока. В коде есть лишний оператор `End Class`, или оператор `End Class` находится за пределами границ соответствующего блока `Class`.  
  
 **Идентификатор ошибки:** BC30460  
  
### Исправление ошибки  
  
-   Найдите и удалите все лишние операторы `End Class`.  
  
-   Переместите оператор `End Class` в правильное место в коде.  
  
## См. также  
 [Оператор End \<ключевое\_слово\>](../Topic/End%20%3Ckeyword%3E%20Statement%20\(Visual%20Basic\).md)