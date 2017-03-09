---
title: "В операторе &quot;Select&quot; блок &quot;Case&quot; не может задаваться после &quot;Case Else&quot; | Microsoft Docs"
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
  - "bc30321"
  - "vbc30321"
helpviewer_keywords: 
  - "BC30321"
ms.assetid: eeedbceb-2c8d-4acb-b84c-8b42c058f083
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# В операторе &quot;Select&quot; блок &quot;Case&quot; не может задаваться после &quot;Case Else&quot;
Оператор `Case Else` представляет операторы для выполнения, если не найдено соответствие для первоначального `Case`. Оператор `Case` обнаружен после `Case Else` в том же блоке `Select`.  
  
 **Идентификатор ошибки:** BC30321  
  
### Исправление ошибки  
  
-   Переместите оператор `Case Else` в соответствующее место после оператора `Case`.  
  
## См. также  
 [Оператор Select...Case](/dotnet/visual-basic/language-reference/statements/select-case-statement)