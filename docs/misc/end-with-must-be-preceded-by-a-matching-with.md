---
title: "Оператору End With должен предшествовать соответствующий оператор With | Microsoft Docs"
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
  - "bc30093"
  - "vbc30093"
helpviewer_keywords: 
  - "BC30093"
ms.assetid: b0f1f7d5-0c33-4b97-8043-f0f5b40ca5d7
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Оператору End With должен предшествовать соответствующий оператор With
Оператор `End With` не имеет соответствующего оператора `With`. Оператору `End With` должен предшествовать соответствующий оператор `With`.  
  
 **Идентификатор ошибки:** BC30093  
  
### Исправление ошибки  
  
1.  Если этот блок `With` является частью набора вложенных блоков `With`, убедитесь в том, что каждый блок завершается правильно.  
  
2.  Убедитесь в том, что другие управляющие структуры в блоке `With` завершаются правильно.  
  
3.  Убедитесь в том, что блок `With` имеет правильный формат.  
  
## См. также  
 [Оператор With...End With](/dotnet/visual-basic/language-reference/statements/with-end-with-statement)