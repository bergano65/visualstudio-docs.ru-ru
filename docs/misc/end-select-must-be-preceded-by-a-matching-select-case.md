---
title: "Оператору End Select должен предшествовать соответствующий оператор Select Case | Microsoft Docs"
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
  - "bc30088"
  - "vbc30088"
helpviewer_keywords: 
  - "BC30088"
ms.assetid: 9de8c0d4-4ce9-45cf-98d6-8f68bba507a5
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Оператору End Select должен предшествовать соответствующий оператор Select Case
Оператор `End Select` не имеет соответствующего оператора `Select` или `Select Case`. Оператору `End Select` должен предшествовать оператор `Select` или `Select Case`.  
  
 **Идентификатор ошибки:** BC30088  
  
### Исправление ошибки  
  
1.  Если этот блок `Select` является частью набора вложенных блоков `Select`, убедитесь в том, что каждый блок завершается правильно.  
  
2.  Убедитесь в том, что другие управляющие структуры в блоке `Select` завершаются правильно.  
  
3.  Убедитесь в том, что блок `Select` имеет правильный формат.  
  
## См. также  
 [Оператор Select...Case](/dotnet/visual-basic/language-reference/statements/select-case-statement)