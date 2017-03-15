---
title: "Case может использоваться только в теле оператора Select Case | Microsoft Docs"
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
  - "vbc30072"
  - "bc30072"
helpviewer_keywords: 
  - "BC30072"
ms.assetid: da808bc3-f154-444a-b547-3cf55beff8a9
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Case может использоваться только в теле оператора Select Case
Оператор `Case` находится за пределами блока `Select`. Оператор `Case` можно использовать только между оператором `Select` или `Select Case` и его соответствующим оператором `End Select`.  
  
 **Идентификатор ошибки:** BC30072  
  
### Исправление ошибки  
  
-   Удалите оператор `Case` или переместите его в блок `Select`.  
  
## См. также  
 [Оператор Select...Case](/dotnet/visual-basic/language-reference/statements/select-case-statement)