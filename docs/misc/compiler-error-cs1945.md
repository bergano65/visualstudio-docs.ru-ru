---
title: "Ошибка компилятора CS1945 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1945"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1945"
ms.assetid: 787f61b0-4767-451c-8c78-8e456b5057eb
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1945
Дерево выражения не может содержать выражение анонимного метода  
  
 Деревья выражений могут содержать только выражения. Анонимные методы могут представлять только операторы.  
  
### Исправление ошибки  
  
1.  Не пытайтесь создать дерево выражений с помощью оператора.  
  
## Пример  
 Следующий код приводит к возникновению ошибки CS1945:  
  
```  
// cs1945.cs using System; using System.Linq.Expressions; public delegate void D(); class Test { static void Main() { Expression<Func<int, Func<int, bool>>> tree = (x => delegate(int i) { return true; }); // CS1945 } }  
```  
  
## См. также  
 [Деревья выражений](../Topic/Expression%20Trees%20\(C%23%20and%20Visual%20Basic\).md)   
 [Инструкции, выражения и операторы](/dotnet/csharp/programming-guide/statements-expressions-operators/index)