---
title: "Типы, допускающие значение NULL, не разрешены в выражениях условной компиляции | Microsoft Docs"
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
  - "bc33111"
  - "vbc33111"
helpviewer_keywords: 
  - "BC33111"
ms.assetid: 2c2587e5-2179-4a31-bcf7-7004db6f2d73
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Типы, допускающие значение NULL, не разрешены в выражениях условной компиляции
Тип, допускающий значение null, не может использоваться в выражениях директивы условной компиляции. Например, следующий код вызывает эту ошибку.  
  
```vb#  
'#Const triggerPoint = 0 '' Not valid. '#If CType(triggerpoint, Boolean?) = True Then '        ' Body of the conditional directive. '#End If  
```  
  
 **Идентификатор ошибки:** BC33111  
  
### Исправление ошибки  
  
-   Удалите назначение типа, допускающего значения NULL.  
  
## См. также  
 [Типы значения, допускающие Null](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types)   
 [Директивы \#If...Then...\#Else](/dotnet/visual-basic/language-reference/directives/if-then-else-directives)   
 [Условная компиляция](/dotnet/visual-basic/programming-guide/program-structure/conditional-compilation)