---
title: "&quot;End RemoveHandler&quot; должно предшествовать соответствующее объявление &quot;RemoveHandler&quot; | Microsoft Docs"
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
  - "vbc31125"
  - "bc31125"
helpviewer_keywords: 
  - "BC31125"
ms.assetid: 754a0017-ec55-4d62-a7bd-c84ece058455
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;End RemoveHandler&quot; должно предшествовать соответствующее объявление &quot;RemoveHandler&quot;
Оператор `End RemoveHandler` используется без соответствующего оператора `RemoveHandler`. Оператору `End RemoveHandler` должен предшествовать соответствующий оператор `RemoveHandler`.  
  
 **Идентификатор ошибки:** BC31125  
  
### Исправление ошибки  
  
-   Убедитесь в том, что предшествующий оператор `RemoveHandler` допустим и правильно написан.  
  
## См. также  
 [Оператор RemoveHandler](/dotnet/visual-basic/language-reference/statements/removehandler-statement)   
 [Оператор Event](/dotnet/visual-basic/language-reference/statements/event-statement)