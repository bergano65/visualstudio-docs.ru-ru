---
title: "End RemoveHandler должен быть первым оператором в строке | Microsoft Docs"
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
  - "bc31119"
  - "vbc31119"
helpviewer_keywords: 
  - "BC31119"
ms.assetid: 4a7e2a71-02d1-41fe-a126-3674288e6efc
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# End RemoveHandler должен быть первым оператором в строке
Оператор `End RemoveHandler` следует за разделителем операторов в виде двоеточия \(:\).`End RemoveHandler` должен быть единственным оператором в своей строке исходного кода.  
  
 **Идентификатор ошибки:** BC31119  
  
### Исправление ошибки  
  
-   Разместите несколько операторов в отдельных строках.  
  
## См. также  
 [Практическое руководство. Разбиение и объединение инструкций в коде](../Topic/How%20to:%20Break%20and%20Combine%20Statements%20in%20Code%20\(Visual%20Basic\).md)   
 [Оператор RemoveHandler](/dotnet/visual-basic/language-reference/statements/removehandler-statement)   
 [Оператор Event](/dotnet/visual-basic/language-reference/statements/event-statement)