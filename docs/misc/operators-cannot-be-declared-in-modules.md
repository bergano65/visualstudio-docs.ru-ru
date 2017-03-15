---
title: "Операторы нельзя объявлять в модулях | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc33018"
  - "vbc33018"
helpviewer_keywords: 
  - "BC33018"
ms.assetid: 10a8fd2d-2af7-4f90-9f2a-50c07ebf7589
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Операторы нельзя объявлять в модулях
[Оператор Operator](/dotnet/visual-basic/language-reference/statements/operator-statement) появляется в определении модуля.  
  
 Оператор можно определить как часть класса или структуры, определяемых вами. В качестве хотя бы одного из операндов оператора должны использоваться класс или структура.  
  
 Оператор должен использовать экземпляр элемента программирования в качестве одного из своих операндов, но экземпляры имеют только классы и структуры. Поэтому невозможно определить оператор как часть любого другого элемента программирования.  
  
 **Идентификатор ошибки:** BC33018  
  
### Исправление ошибки  
  
-   Если требуется выполнить операцию с модулем, используйте [Оператор Function](/dotnet/visual-basic/language-reference/statements/function-statement) для определения процедуры `Function`, которая выполняет операцию.  
  
-   Можно также определить класс или структуру в модуле и определить оператор для этого класса или структуры. Однако оператор должен принимать в качестве хотя бы одного операнда экземпляр этого класса или структуры.  
  
## См. также  
 [Процедуры операторов](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Практическое руководство. Определение оператора](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Практическое руководство. Определение оператора преобразования](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)