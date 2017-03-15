---
title: "Только операторы преобразования могут быть объявлены как &quot;&lt;ключевое_слово&gt;&quot;. | Microsoft Docs"
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
  - "bc33019"
  - "vbc33019"
helpviewer_keywords: 
  - "BC33019"
ms.assetid: 946266fe-a909-41b1-aad4-f85dc8050b88
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Только операторы преобразования могут быть объявлены как &quot;&lt;ключевое_слово&gt;&quot;.
Оператор [Оператор Operator](/dotnet/visual-basic/language-reference/statements/operator-statement) указывает [Widening](/dotnet/visual-basic/language-reference/modifiers/widening) или [Narrowing](/dotnet/visual-basic/language-reference/modifiers/narrowing), когда этот оператор не является оператором преобразования.  
  
 Каждый оператор должен быть объявлен как [Public](/dotnet/visual-basic/language-reference/modifiers/public) и [Shared](/dotnet/visual-basic/language-reference/modifiers/shared). Однако только оператор преобразования может быть объявлен с [Widening](/dotnet/visual-basic/language-reference/modifiers/widening) или [Narrowing](/dotnet/visual-basic/language-reference/modifiers/narrowing), но не с обоими этими ключевыми словами.  
  
 При необходимости в определение оператора можно включить ключевые слова [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads) и [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows). Никакие другие ключевые слова в операторе [Оператор Operator](/dotnet/visual-basic/language-reference/statements/operator-statement) не разрешены.  
  
 **Идентификатор ошибки:** BC33019  
  
### Исправление ошибки  
  
1.  Удалите ключевое слово `Widening` или `Narrowing` из определения оператора. Они не применяются, поскольку преобразование типа не выполняется.  
  
## См. также  
 [Процедуры операторов](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Оператор Operator](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [Практическое руководство. Определение оператора](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Практическое руководство. Определение оператора преобразования](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)   
 [Преобразование типов в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/type-conversions)