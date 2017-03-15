---
title: "Оператору &quot;End If&quot; должен предшествовать соответствующий оператор &quot;If&quot; | Microsoft Docs"
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
  - "bc30087"
  - "vbc30087"
helpviewer_keywords: 
  - "BC30087"
ms.assetid: 81c056bb-267e-44ef-9a44-3a41273090ea
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Оператору &quot;End If&quot; должен предшествовать соответствующий оператор &quot;If&quot;
Оператор `End If` не имеет соответствующего оператора `If`. Оператору `End If` должен предшествовать оператор `If`.  
  
 **Идентификатор ошибки:** BC30087  
  
### Исправление ошибки  
  
1.  Если этот блок `If` является частью набора вложенных блоков `If`, убедитесь в том, что каждый блок завершается правильно.  
  
2.  Убедитесь в том, что другие управляющие структуры в блоке `If` завершаются правильно.  
  
3.  Убедитесь в том, что блок `If` имеет правильный формат.  
  
## См. также  
 [Оператор If...Then...Else](/dotnet/visual-basic/language-reference/statements/if-then-else-statement)