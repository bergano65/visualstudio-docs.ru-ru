---
title: "Ошибка компилятора CS0460 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0460"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0460"
ms.assetid: 98d39ded-d3f9-4520-b912-892e574c056b
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0460
Ограничения для переопределения и явной реализации методов интерфейса унаследованы от базового метода, поэтому они не могут быть указаны явно  
  
 Если универсальный метод, который является частью производного класса, переопределяет метод базового класса, для переопределяющего метода нельзя указывать ограничения. Переопределяющий метод в производном классе наследует ограничения от метода базового класса.  
  
## Пример  
 При компиляции следующего примера возникнет ошибка CS0460.  
  
```  
// CS0460.cs // compile with: /target:library class BaseClass { BaseClass() { } } interface I { void F1<T>() where T : BaseClass; void F2<T>() where T : struct; void F3<T>() where T : BaseClass; } class ExpImpl : I { void I.F1<T>() where T : BaseClass {}   // CS0460 void I.F2<T>() where T : class {}  // CS0460 }  
```