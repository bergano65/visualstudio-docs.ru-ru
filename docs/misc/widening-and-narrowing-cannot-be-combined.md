---
title: "&quot;Widening&quot; и &quot;Narrowing&quot; нельзя использовать вместе. | Microsoft Docs"
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
  - "bc33001"
  - "vbc33001"
helpviewer_keywords: 
  - "BC33001"
ms.assetid: 1c576344-083c-45ad-bc71-0489bd3976be
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;Widening&quot; и &quot;Narrowing&quot; нельзя использовать вместе.
Оператор [Оператор Operator](/dotnet/visual-basic/language-reference/statements/operator-statement) указывает оба ключевых слова [Widening](/dotnet/visual-basic/language-reference/modifiers/widening) и [Narrowing](/dotnet/visual-basic/language-reference/modifiers/narrowing).  
  
 При определении оператора преобразования необходимо объявить его как `Widening` или `Narrowing`. Это взаимно исключающие характеристики, поэтому их нельзя указывать вместе.  
  
 **Идентификатор ошибки:** BC33001  
  
### Исправление ошибки  
  
-   Удалите ключевое слово `Widening` или `Narrowing` из оператора `Operator`. Необходимо указать то или другое ключевое слово.  
  
## См. также  
 [Процедуры операторов](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Оператор Operator](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [Практическое руководство. Определение оператора](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Практическое руководство. Определение оператора преобразования](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)