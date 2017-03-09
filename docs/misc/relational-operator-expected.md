---
title: "Требуется оператор отношения | Microsoft Docs"
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
  - "bc30239"
  - "vbc30239"
helpviewer_keywords: 
  - "BC30239"
ms.assetid: c5701568-77a1-441b-a0f7-f7b36cbd17e3
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Требуется оператор отношения
Оператор `Case` содержит предложение `Is`, но не содержит оператор сравнения, например `=` или `>`. Если оператор `Case` не включает какой\-либо оператор, предполагается использование `=`, а `Is` не используется.  
  
 **Идентификатор ошибки:** BC30239  
  
### Исправление ошибки  
  
-   Удалите ключевое слово `Is` или дополните его оператором сравнения.  
  
## См. также  
 [Оператор Select...Case](/dotnet/visual-basic/language-reference/statements/select-case-statement)   
 [Операторы сравнения в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators)   
 [Операторы сравнения](/dotnet/visual-basic/language-reference/operators/comparison-operators)