---
title: "Continue While может появляться только в операторе While | Microsoft Docs"
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
  - "vbc30784"
  - "bc30784"
helpviewer_keywords: 
  - "BC30784"
ms.assetid: b26c77b2-36ae-4dce-b048-f7c4b196faa4
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Continue While может появляться только в операторе While
Оператор `Continue While` может присутствовать только в цикле `For...Next`.  
  
 **Идентификатор ошибки:** BC30784  
  
### Исправление ошибки  
  
1.  Если оператор `Continue While` находится в цикле `Do...Loop`, измените оператор на `Continue Do`.  
  
2.  Если оператор `Continue While` находится в цикле `For...Next`, измените оператор на `Continue For`.  
  
3.  В противном случае удалите оператор `Continue While`.  
  
## См. также  
 [Оператор Continue](/dotnet/visual-basic/language-reference/statements/continue-statement)   
 [Оператор While...End While](/dotnet/visual-basic/language-reference/statements/while-end-while-statement)