---
title: "Локальные переменные в методах структур не могут объявляться как Static | Microsoft Docs"
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
  - "vbc31400"
  - "bc31400"
helpviewer_keywords: 
  - "BC31400"
ms.assetid: 38b8adee-3593-40fb-b0a4-e2a47599567f
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Локальные переменные в методах структур не могут объявляться как Static
Модификатор `Static` нельзя использовать с локальными переменными в структурах.  
  
 **Идентификатор ошибки:** BC31400  
  
### Исправление ошибки  
  
1.  Удалите модификатор `Static` из локальной переменной.  
  
2.  Объявите переменную как статическую с более широкой областью.  
  
## См. также  
 [Static](/dotnet/visual-basic/language-reference/modifiers/static)