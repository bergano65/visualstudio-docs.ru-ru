---
title: "Операторы и метки между &quot;Select Case&quot; и первым блоком &quot;Case&quot; недопустимы. | Microsoft Docs"
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
  - "bc30058"
  - "vbc30058"
helpviewer_keywords: 
  - "BC30058"
ms.assetid: 399b4659-f7df-4377-80be-43019f1e6206
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Операторы и метки между &quot;Select Case&quot; и первым блоком &quot;Case&quot; недопустимы.
Оператор, не являющийся комментарием, указывается между открывающим оператором `Select` или `Select Case` и его первым оператором `Case`.  
  
 **Идентификатор ошибки:** BC30058  
  
### Исправление ошибки  
  
-   Если промежуточный оператор является комментарием, вставьте перед ним разделитель комментария \(`'` или `REM`\). В противном случае переместите или удалите этот оператор.  
  
## См. также  
 [Оператор Select...Case](/dotnet/visual-basic/language-reference/statements/select-case-statement)