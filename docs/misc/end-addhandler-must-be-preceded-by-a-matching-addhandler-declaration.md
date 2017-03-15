---
title: "Оператору End AddHandler должно предшествовать соответствующее объявление AddHandler | Microsoft Docs"
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
  - "bc31124"
  - "vbc31124"
helpviewer_keywords: 
  - "BC31124"
ms.assetid: c667fecb-163a-49ca-b416-e1070f4fab1d
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Оператору End AddHandler должно предшествовать соответствующее объявление AddHandler
Оператор `End AddHandler` используется без соответствующего оператора `AddHandler`. Оператору `End AddHandler` должен предшествовать соответствующий оператор `AddHandler`.  
  
 **Идентификатор ошибки:** BC31124  
  
### Исправление ошибки  
  
-   Убедитесь, что предшествующий оператор `AddHandler` допустим и правильно написан.  
  
## См. также  
 [Оператор AddHandler](/dotnet/visual-basic/language-reference/statements/addhandler-statement)   
 [Оператор Event](/dotnet/visual-basic/language-reference/statements/event-statement)