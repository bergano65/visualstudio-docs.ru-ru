---
title: "Ошибка компилятора CS0080 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0080"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0080"
ms.assetid: 99035371-37d1-48b2-a8b9-e8a1ebd04f0f
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0080
Ограничения не разрешены в объявлениях, не являющихся универсальными.  
  
 Обнаруженный синтаксис может использоваться только в универсальном объявлении для применения ограничений к параметру типа. Дополнительные сведения см. в разделе [Универсальные шаблоны](/dotnet/csharp/programming-guide/generics/index).  
  
 При компиляции следующего примера возникнет ошибка CS0080, так как MyClass не является универсальным классом, а Foo — универсальным методом.  
  
```  
namespace MyNamespace { public class MyClass where MyClass : System.IDisposable // CS0080    //the following line shows an example of correct syntax //public class MyClass<T> where T : System.IDisposable { public void Foo() where Foo : new() // CS0080 //the following line shows an example of correct syntax //public void Foo<U>() where U : struct { } } public class Program { public static void Main() { } } }  
```