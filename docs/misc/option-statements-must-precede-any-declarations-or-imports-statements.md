---
title: "Оператор Option должен находиться перед объявлениями и операторами Imports | Microsoft Docs"
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
  - "vbc30627"
  - "bc30627"
helpviewer_keywords: 
  - "BC30627"
ms.assetid: 2ce0fcf2-80f4-47d3-a394-44e0aed456db
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Оператор Option должен находиться перед объявлениями и операторами Imports
Операторы `Option` должны быть первыми операторами без комментариев в исходном коде.  
  
 **Идентификатор ошибки:** BC30627  
  
### Исправление ошибки  
  
-   Переместите операторы `Option` в начало исходного кода, сразу после операторов `Imports` и `Namespace`.  
  
## См. также  
 [Оператор Option \<ключевое\_слово\>](../Topic/Option%20%3Ckeyword%3E%20Statement.md)   
 [Оператор Option Compare](/dotnet/visual-basic/language-reference/statements/option-compare-statement)   
 [Оператор Option Explicit](/dotnet/visual-basic/language-reference/statements/option-explicit-statement)   
 [Option Infer \- оператор](/dotnet/visual-basic/language-reference/statements/option-infer-statement)   
 [Оператор Option Strict](/dotnet/visual-basic/language-reference/statements/option-strict-statement)