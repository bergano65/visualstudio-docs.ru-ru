---
title: "End RaiseEvent должен быть первым оператором в строке | Microsoft Docs"
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
  - "vbc31120"
  - "bc31120"
helpviewer_keywords: 
  - "BC31120"
ms.assetid: 51aea522-5c4c-4ec0-8850-03f6ecebd6bc
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# End RaiseEvent должен быть первым оператором в строке
Оператор `End RaiseEvent` следует за разделителем операторов в виде двоеточия \(:\).`End RaiseEvent` должен быть единственным оператором в своей строке исходного кода.  
  
 **Идентификатор ошибки:** BC31120  
  
### Исправление ошибки  
  
-   Разместите несколько операторов в отдельных строках.  
  
## См. также  
 [Практическое руководство. Разбиение и объединение инструкций в коде](../Topic/How%20to:%20Break%20and%20Combine%20Statements%20in%20Code%20\(Visual%20Basic\).md)   
 [Оператор RaiseEvent](/dotnet/visual-basic/language-reference/statements/raiseevent-statement)   
 [Оператор Event](/dotnet/visual-basic/language-reference/statements/event-statement)