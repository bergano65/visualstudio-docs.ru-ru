---
title: "Перед End Operator должно быть указано соответствующее объявление Operator | Microsoft Docs"
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
  - "vbc33007"
  - "bc33007"
helpviewer_keywords: 
  - "BC33007"
ms.assetid: 57df3e01-0858-4cf7-9295-075a2c0c4bde
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Перед End Operator должно быть указано соответствующее объявление Operator
Оператору `End Operator` не предшествует соответствующее объявление `Operator`.  
  
 **Идентификатор ошибки:** BC33007  
  
### Исправление ошибки  
  
-   Удалите оператор `End Operator`, если он лишний.  
  
-   Добавьте процедуру `Operator`, если она отсутствует.  
  
-   Переместите оператор `End Operator` в соответствующее место кода.  
  
## См. также  
 [Оператор End \<ключевое\_слово\>](../Topic/End%20%3Ckeyword%3E%20Statement%20\(Visual%20Basic\).md)   
 [Процедуры операторов](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Оператор Operator](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [Практическое руководство. Определение оператора](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Практическое руководство. Определение оператора преобразования](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)