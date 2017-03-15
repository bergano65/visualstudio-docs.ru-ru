---
title: "Перед оператором ElseIf должен быть указан соответствующий оператор If или ElseIf. | Microsoft Docs"
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
  - "bc36005"
  - "vbc36005"
helpviewer_keywords: 
  - "BC36005"
ms.assetid: bcebae85-b438-4839-bada-2f8f8dcc8a86
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Перед оператором ElseIf должен быть указан соответствующий оператор If или ElseIf.
Оператор `ElseIf` указан без соответствующего оператора `If`. Перед `ElseIf` всегда должен быть указан оператор `If` или другой оператор `ElseIf`.  
  
 **Идентификатор ошибки:** BC36005  
  
### Исправление ошибки  
  
1.  Если этот блок `If` является частью набора вложенных структур управления, убедитесь, что каждая структура завершается правильно.  
  
2.  Проверьте, правильно ли завершаются другие структуры управления в блоке `If`.  
  
3.  Убедитесь в том, что блок `If` имеет правильный формат.  
  
## См. также  
 [Оператор If...Then...Else](/dotnet/visual-basic/language-reference/statements/if-then-else-statement)   
 [Структуры решений](/dotnet/visual-basic/programming-guide/language-features/control-flow/decision-structures)