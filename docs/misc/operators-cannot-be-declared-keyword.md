---
title: "Операторы нельзя объявить как &quot;&lt;ключевое_слово&gt;&quot; | Microsoft Docs"
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
  - "vbc33013"
  - "bc33013"
helpviewer_keywords: 
  - "BC33013"
ms.assetid: bfd805f4-e30e-4553-9cb7-2690595f0480
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Операторы нельзя объявить как &quot;&lt;ключевое_слово&gt;&quot;
Оператор объявлен с ключевым словом, которое не является допустимым для определений оператора.  
  
 Каждый оператор должен быть объявлен как [Public](/dotnet/visual-basic/language-reference/modifiers/public) и как [Shared](/dotnet/visual-basic/language-reference/modifiers/shared). Кроме того, оператор преобразования должен объявляться с использованием ключевого слова [Widening](/dotnet/visual-basic/language-reference/modifiers/widening) или [Narrowing](/dotnet/visual-basic/language-reference/modifiers/narrowing), но не обоих этих ключевых слов. При необходимости в определение оператора можно включить ключевые слова [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads) или [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows). Никакие другие ключевые слова в операторе [Оператор Operator](/dotnet/visual-basic/language-reference/statements/operator-statement) не разрешены.  
  
 **Идентификатор ошибки:** BC33013  
  
### Исправление ошибки  
  
-   Удалите недопустимое ключевое слово из определения оператора.  
  
## См. также  
 [Процедуры операторов](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Практическое руководство. Определение оператора](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Практическое руководство. Определение оператора преобразования](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)