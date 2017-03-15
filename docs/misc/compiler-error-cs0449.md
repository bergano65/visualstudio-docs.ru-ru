---
title: "Ошибка компилятора CS0449 | Microsoft Docs"
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
  - "CS0449"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0449"
ms.assetid: 32c07a2c-4c48-4d07-b643-72422a6b9fac
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0449
Все другие ограничения должны следовать после ограничения "class" или "struct".  
  
 Ограничения параметра общего типа или метода должны применяться в следующем порядке: сначала `class` или `struct` \(если таковые имеются\), затем все ограничения интерфейса, и наконец — все ограничения конструктора. Эта ошибка возникает в том случае, когда ограничение `class` или `struct` следует не первым. Чтобы устранить эту ошибку, измените порядок предложений ограничений.  
  
## Пример  
 Следующий пример приводит к возникновению ошибки CS0449:  
  
```  
// CS0449.cs // compile with: /target:library interface I {} public class C4 { public void F1<T>() where T : class, struct, I {}   // CS0449 public void F2<T>() where T : I, struct {}   // CS0449 public void F3<T>() where T : I, class {}   // CS0449 // OK public void F4<T>() where T : class {} public void F5<T>() where T : struct {} public void F6<T>() where T : I {} }  
```