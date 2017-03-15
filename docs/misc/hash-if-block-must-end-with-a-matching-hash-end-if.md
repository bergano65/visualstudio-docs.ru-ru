---
title: "Блок #If должен завершаться соответствующим оператором #End If | Microsoft Docs"
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
  - "vbc30012"
  - "bc30012"
helpviewer_keywords: 
  - "BC30012"
ms.assetid: 9d51f3be-d2c3-4918-a36d-0d9e9763e47b
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Блок #If должен завершаться соответствующим оператором #End If
`#If` является директивой условной компиляции. Блок `#If` не завершается директивой `#End If`.  
  
 **Идентификатор ошибки:** BC30012  
  
### Исправление ошибки  
  
-   Добавьте директиву `#End If` в конец блока условной компиляции.  
  
## См. также  
 [Директивы \#If...Then...\#Else](/dotnet/visual-basic/language-reference/directives/if-then-else-directives)