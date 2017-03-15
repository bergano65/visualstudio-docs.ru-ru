---
title: "Ошибка компилятора CS0217 | Microsoft Docs"
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
  - "CS0217"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0217"
ms.assetid: ede61095-6e11-4f4a-8e7d-85e7a3f4fc3d
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0217
При использовании определенного пользователем логического оператора \("оператор"\) как отладочного тип значения, возвращаемого этим оператором, должен совпадать с типом обоих его параметров.  
  
 Если вы задаете оператор для определяемого пользователем типа, а затем пытаетесь использовать его как оператор краткой записи, определяемый пользователем оператор должен иметь параметры и возвращаемые значения того же типа. Дополнительные сведения об операторах краткой записи см. в разделах [Оператор &&](/dotnet/csharp/language-reference/operators/conditional-and-operator) и [Оператор &#124;&#124;](../Topic/%7C%7C%20Operator%20\(C%23%20Reference\).md).  
  
 Следующий пример приводит к возникновению ошибки CS0217:  
  
```  
// CS0217.cs using System; public class MyClass { public static bool operator true (MyClass f) { return false; } public static bool operator false (MyClass f) { return false; } public static implicit operator int(MyClass x) { return 0; } public static int operator & (MyClass f1, MyClass f2)   // CS0217 // try the following line instead // public static MyClass operator & (MyClass f1, MyClass f2) { return new MyClass(); } public static void Main() { MyClass f = new MyClass(); int i = f && f; } }  
```  
  
## См. также  
 [Перегружаемые операторы](/dotnet/csharp/programming-guide/statements-expressions-operators/overloadable-operators)