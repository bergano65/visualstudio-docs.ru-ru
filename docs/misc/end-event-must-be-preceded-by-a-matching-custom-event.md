---
title: "Оператору End Event должен предшествовать соответствующий ему оператор Custom Event | Microsoft Docs"
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
  - "vbc31123"
  - "bc31123"
helpviewer_keywords: 
  - "BC31123"
ms.assetid: 8dbffccc-c1ba-45f5-a1b4-90889bb0a3fd
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Оператору End Event должен предшествовать соответствующий ему оператор Custom Event
Оператор `End Event` не имеет соответствующего оператора `Custom Event`. Оператору `End Event` должен предшествовать соответствующий оператор `Custom Event`.  
  
 **Идентификатор ошибки:** BC31123  
  
### Исправление ошибки  
  
-   Убедитесь, что предшествующий оператор `Custom Event` допустим и правильно написан.  
  
## См. также  
 [Оператор Event](/dotnet/visual-basic/language-reference/statements/event-statement)