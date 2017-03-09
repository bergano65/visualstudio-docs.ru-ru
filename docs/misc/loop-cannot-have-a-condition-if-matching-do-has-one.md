---
title: "Оператор &quot;Loop&quot; не может содержать условие, если соответствующий оператор &quot;Do&quot; содержит условие | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30238"
  - "bc30238"
helpviewer_keywords: 
  - "BC30238"
ms.assetid: 81513cb5-69e7-4d62-b33e-e54cb8c5e8bf
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Оператор &quot;Loop&quot; не может содержать условие, если соответствующий оператор &quot;Do&quot; содержит условие
Оператор `Loop` содержит предложение `While` или `Until`. Соответствующий оператор `Do` также содержит такое предложение. Лишь один из операторов `Do` или `Loop` может содержать в цикле условие.  
  
 **Идентификатор ошибки:** BC30238  
  
### Исправление ошибки  
  
-   Удалите предложение `While` или `Until` из оператора `Do` или `Loop`.  
  
## См. также  
 [Оператор Do...Loop](/dotnet/visual-basic/language-reference/statements/do-loop-statement)