---
title: "Оператору End While должен предшествовать соответствующий оператор While. | Microsoft Docs"
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
  - "vbc30090"
  - "bc30090"
helpviewer_keywords: 
  - "BC30090"
ms.assetid: 302b26b8-8fa4-4e49-86f0-d7c49fec485f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Оператору End While должен предшествовать соответствующий оператор While.
Оператор `End While` не имеет соответствующего оператора `While`. Оператору `End While` должен предшествовать соответствующий оператор `While`.  
  
 **Идентификатор ошибки:** BC30090  
  
### Исправление ошибки  
  
1.  Если этот блок `While` является частью набора вложенных блоков `While`, убедитесь в том, что каждый блок завершается правильно.  
  
2.  Убедитесь в том, что другие управляющие структуры в блоке `While` завершаются правильно.  
  
3.  Убедитесь в том, что блок `While` имеет правильный формат.  
  
## См. также  
 [Оператор While...End While](/dotnet/visual-basic/language-reference/statements/while-end-while-statement)