---
title: "События не могут иметь тип возврата | Microsoft Docs"
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
  - "bc30032"
  - "vbc30032"
helpviewer_keywords: 
  - "BC30032"
ms.assetid: 4cd3bffc-b5b2-4000-bfb9-7d6968e6fc62
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# События не могут иметь тип возврата
События могут принимать аргументы, но не могут возвращать значения напрямую.  
  
 **Идентификатор ошибки:** BC30032  
  
### Исправление ошибки  
  
-   Удалите тип возврата из оператора `Event`.  
  
## См. также  
 [Оператор Event](/dotnet/visual-basic/language-reference/statements/event-statement)