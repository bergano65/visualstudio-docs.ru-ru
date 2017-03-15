---
title: "Оператор &quot;Exit Operator&quot; является недопустимым. Используйте &quot;Return&quot;, чтобы выйти из процедуры Operator | Microsoft Docs"
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
  - "bc33008"
  - "vbc33008"
helpviewer_keywords: 
  - "BC33008"
ms.assetid: 8c44456b-8fd2-4168-ad8c-b6da129242ba
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Оператор &quot;Exit Operator&quot; является недопустимым. Используйте &quot;Return&quot;, чтобы выйти из процедуры Operator
Оператор `Exit Operator` находится в процедуре `Operator`.  
  
 Вы должны использовать [Оператор Return](/dotnet/visual-basic/language-reference/statements/return-statement) для возврата из процедуры `Operator`. Оператор [Оператор Exit](/dotnet/visual-basic/language-reference/statements/exit-statement) не принимает ключевое слово `Operator`, и оператор `End Operator` не возвращает управление вызывающему коду.  
  
 **Идентификатор ошибки:** BC33008  
  
### Исправление ошибки  
  
-   Замените оператор `Exit Operator` на оператор `Return`.  
  
## См. также  
 [Процедуры операторов](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Оператор Operator](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [Практическое руководство. Определение оператора](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Практическое руководство. Определение оператора преобразования](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)