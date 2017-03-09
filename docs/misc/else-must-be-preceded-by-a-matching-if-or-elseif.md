---
title: "Оператору Else должен предшествовать соответствующий оператор If или ElseIf. | Microsoft Docs"
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
  - "bc30086"
  - "vbc30086"
helpviewer_keywords: 
  - "BC30086"
ms.assetid: 5e76b3c6-571f-4a6f-b524-26150cb6e986
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Оператору Else должен предшествовать соответствующий оператор If или ElseIf.
Оператор `Else` не имеет соответствующего оператора `If`. Оператору `Else` должен предшествовать оператор `If`.  
  
 **Идентификатор ошибки:** BC30086  
  
### Исправление ошибки  
  
1.  Если этот блок `If` является частью набора вложенных блоков `If`, убедитесь в том, что каждый блок завершается правильно.  
  
2.  Убедитесь в том, что другие управляющие структуры в блоке `If` завершаются правильно.  
  
3.  Убедитесь в том, что блок `If` имеет правильный формат.  
  
## См. также  
 [Оператор If...Then...Else](/dotnet/visual-basic/language-reference/statements/if-then-else-statement)