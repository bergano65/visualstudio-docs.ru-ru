---
title: "Для оператора &quot;&lt;символ_оператора1&gt;&quot; требуется соответствующий оператор &quot;&lt;символ_оператора2&gt;&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc33033"
  - "vbc33033"
helpviewer_keywords: 
  - "BC33033"
ms.assetid: d2805e4f-08a8-4760-9539-565f51b88d13
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Для оператора &quot;&lt;символ_оператора1&gt;&quot; требуется соответствующий оператор &quot;&lt;символ_оператора2&gt;&quot;
Определяется оператор, но требуемый для него оператор не определен.  
  
 Следующие операторы должны определяться как пары:  
  
-   `=` и `<>`.  
  
-   `>` и `<`.  
  
-   `>=` и `<=`.  
  
-   `IsTrue` и `IsFalse`.  
  
 При определении любого из этих операторов в классе или структуре необходимо также определить соответствующий ему оператор в том же классе или структуре.  
  
 Даже если соответствующий оператор явно не используется, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] может потребоваться его использовать. Например, при определении класса или структуры, которые используются в качестве переменной\-счетчика в [Оператор For...Next](/dotnet/visual-basic/language-reference/statements/for-next-statement), [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] требует операторов `>=` и `<=` \(а также оператора `+`\).  
  
 **Идентификатор ошибки:** BC33033  
  
### Исправление ошибки  
  
-   Определите соответствующий оператор в том же классе или структуре. Приложите усилия, чтобы сделать его значимым, так как [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] может использовать его в непредвиденной ситуации.  
  
## См. также  
 [Процедуры операторов](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Оператор Operator](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [Практическое руководство. Определение оператора](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Практическое руководство. Определение оператора преобразования](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)   
 [Операторы и выражения](/dotnet/visual-basic/programming-guide/language-features/operators-and-expressions/index)