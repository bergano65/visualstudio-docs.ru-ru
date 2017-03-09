---
title: "Case Else может использоваться только в теле оператора Select Case  | Microsoft Docs"
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
  - "bc30071"
  - "vbc30071"
helpviewer_keywords: 
  - "BC30071"
ms.assetid: 9a4f8ccb-717a-4d18-91b4-4a373202c38a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Case Else может использоваться только в теле оператора Select Case 
Оператор `Case Else` находится за пределами блока `Select`. Оператор `Case Else` можно использовать только между оператором `Select` или `Select Case` и его соответствующим оператором `End Select`.  
  
 **Идентификатор ошибки:** BC30071  
  
### Исправление ошибки  
  
-   Удалите оператор `Case Else` или переместите его в блок `Select`.  
  
## См. также  
 [Оператор Select...Case](/dotnet/visual-basic/language-reference/statements/select-case-statement)