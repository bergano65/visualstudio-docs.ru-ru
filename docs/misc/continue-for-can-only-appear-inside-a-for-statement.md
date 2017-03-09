---
title: "Continue For может присутствовать только в операторе For | Microsoft Docs"
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
  - "bc30783"
  - "vbc30783"
helpviewer_keywords: 
  - "BC30783"
ms.assetid: 70891018-27c8-4d36-b168-8cc7177d70cb
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Continue For может присутствовать только в операторе For
Оператор `Continue For` может присутствовать только в цикле `For...Next`.  
  
 **Идентификатор ошибки:** BC30783  
  
### Исправление ошибки  
  
1.  Если оператор `Continue For` находится в цикле `Do...Loop`, измените оператор на `Continue Do`.  
  
     —или—  
  
     Если оператор `Continue For` находится в цикле `While...End While`, измените оператор на `Continue While`.  
  
2.  В противном случае удалите оператор `Continue For`.  
  
## См. также  
 [Оператор Continue](/dotnet/visual-basic/language-reference/statements/continue-statement)   
 [Оператор For...Next](/dotnet/visual-basic/language-reference/statements/for-next-statement)