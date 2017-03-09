---
title: "Оператору &quot;Next&quot; должен предшествовать соответствующий оператор &quot;For&quot;. | Microsoft Docs"
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
  - "vbc30092"
  - "bc30092"
helpviewer_keywords: 
  - "BC30092"
ms.assetid: 4bf49bb2-c69b-443d-aa58-cb40fcfb1370
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Оператору &quot;Next&quot; должен предшествовать соответствующий оператор &quot;For&quot;.
Оператор `Next` указан без соответствующего оператора `For` или `For Each`. Оператору `Next` должен предшествовать соответствующий оператор `For` или `For Each`.  
  
 **Идентификатор ошибки:** BC30092  
  
### Исправление ошибки  
  
1.  Если этот цикл `For` является частью набора вложенных циклов `For`, убедитесь, что каждый цикл завершен правильно.  
  
2.  Убедитесь в том, что другие управляющие структуры в цикле `For` завершены правильно.  
  
3.  Убедитесь, что цикл `For` имеет правильный формат.  
  
## См. также  
 [Оператор For...Next](/dotnet/visual-basic/language-reference/statements/for-next-statement)   
 [Оператор For Each...Next](/dotnet/visual-basic/language-reference/statements/for-each-next-statement)