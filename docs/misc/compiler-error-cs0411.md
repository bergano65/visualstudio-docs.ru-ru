---
title: "Ошибка компилятора CS0411 | Microsoft Docs"
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
  - "CS0411"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0411"
ms.assetid: 290947c9-10d0-427e-99f2-bff20299d533
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0411
Аргументы типа для метода "метод" не могут выводиться из использования. Попробуйте указать аргументы типа явным образом.  
  
 Эта ошибка возникает, если универсальный метод вызывается без явного предоставления аргументов типа, и компилятор не может определить, какие аргументы типа имеются в виду. Чтобы избежать этой ошибки, добавьте предполагаемые аргументы типа в угловых скобках.  
  
## Пример  
 Следующий пример приводит к возникновению ошибки CS0411:  
  
```  
// CS0411.cs class C { void G<T>() { } public static void Main() { G();  // CS0411 // Try this instead: // G<int>(); } }  
```  
  
## Пример  
 Также эта ошибка может возникать, например, когда параметр — `null`, который не имеет сведений о типе:  
  
```  
// CS0411b.cs class C { public void F<T>(T t) where T : C { } public static void Main() { C c = new C(); c.F(null);  // CS0411 } }  
```