---
title: "Continue Do может присутствовать только в операторе Do | Microsoft Docs"
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
  - "vbc30782"
  - "bc30782"
helpviewer_keywords: 
  - "BC30782"
ms.assetid: c6b35e63-4d84-449d-9685-41a1bc0a7f35
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Continue Do может присутствовать только в операторе Do
Оператор `Continue Do` может присутствовать только в цикле `Do...Loop`.  
  
 **Идентификатор ошибки:** BC30782  
  
### Исправление ошибки  
  
1.  Если оператор `Continue Do` находится в цикле `For...Next`, измените оператор на `Continue For`.  
  
2.  Если оператор `Continue Do` находится в цикле `While...End While`, измените оператор на `Continue While`.  
  
3.  В противном случае удалите оператор `Continue Do`.  
  
## См. также  
 [Оператор Continue](/dotnet/visual-basic/language-reference/statements/continue-statement)   
 [Оператор Do...Loop](/dotnet/visual-basic/language-reference/statements/do-loop-statement)