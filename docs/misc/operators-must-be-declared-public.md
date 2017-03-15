---
title: "Операторы необходимо объявить как Public | Microsoft Docs"
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
  - "vbc33011"
  - "bc33011"
helpviewer_keywords: 
  - "BC33011"
ms.assetid: 67fc0dee-4ef5-4afc-a63a-f7d20bce7954
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Операторы необходимо объявить как Public
[Оператор Operator](/dotnet/visual-basic/language-reference/statements/operator-statement) не включает ключевое слово [Public](/dotnet/visual-basic/language-reference/modifiers/public).  
  
 Процедуре `Operator` требуются ключевые слова `Public` и [Shared](/dotnet/visual-basic/language-reference/modifiers/shared), а для оператора преобразования также требуется ключевое слово [Widening](/dotnet/visual-basic/language-reference/modifiers/widening) или [Narrowing](/dotnet/visual-basic/language-reference/modifiers/narrowing).  
  
 **Идентификатор ошибки:** BC33011  
  
### Исправление ошибки  
  
-   Добавьте ключевое слово `Public` в оператор `Operator`.  
  
## См. также  
 [Процедуры операторов](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Оператор Operator](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [Практическое руководство. Определение оператора](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Практическое руководство. Определение оператора преобразования](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)