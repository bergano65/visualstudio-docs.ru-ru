---
title: "Структуры не могут содержать операторов &quot;Inherits&quot; | Microsoft Docs"
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
  - "vbc30628"
  - "bc30628"
helpviewer_keywords: 
  - "BC30628"
ms.assetid: 131ecce1-6378-43fb-af0b-cdf5a0350cec
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Структуры не могут содержать операторов &quot;Inherits&quot;
В отличие от классов, структуры не поддерживают наследование.  
  
 **Идентификатор ошибки:** BC30628  
  
### Исправление ошибки  
  
-   Удалите оператор `Inherits` из структуры.  
  
-   Измените приложение так, чтобы в нем использовались классы вместо структур.  
  
## См. также  
 [Структуры](/dotnet/visual-basic/programming-guide/language-features/data-types/structures)   
 [Структуры и классы](/dotnet/visual-basic/programming-guide/language-features/data-types/structures-and-classes)