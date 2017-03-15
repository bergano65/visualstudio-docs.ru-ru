---
title: "Методы, объявленные как &quot;Overrides&quot;, не могут объявляться как &quot;Overridable&quot;, так как возможность их переопределения подразумевается | Microsoft Docs"
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
  - "bc30730"
  - "vbc30730"
helpviewer_keywords: 
  - "BC30730"
ms.assetid: cc892f81-eb1f-42a9-8f54-eff352adb5dd
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Методы, объявленные как &quot;Overrides&quot;, не могут объявляться как &quot;Overridable&quot;, так как возможность их переопределения подразумевается
В отличие от большинства методов, методы, помеченные модификатором `Overrides`, являются переопределяемыми по умолчанию.  
  
 **Идентификатор ошибки:** BC30730  
  
### Исправление ошибки  
  
-   Не указывайте модификатор `Overridable` в методах, помеченных модификатором `Overrides`.  
  
## См. также  
 [Overrides](/dotnet/visual-basic/language-reference/modifiers/overrides)   
 [Overridable](/dotnet/visual-basic/language-reference/modifiers/overridable)