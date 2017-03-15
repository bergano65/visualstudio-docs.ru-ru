---
title: "Ошибка компилятора CS0081 | Microsoft Docs"
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
  - "CS0081"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0081"
ms.assetid: a5649abc-89ea-4f64-8c3c-eb36df926561
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0081
Объявление параметра\-типа должно быть идентификатором, а не типом.  
  
 При объявлении универсального метода или типа следует указать параметр типа как идентификатор, например Т или inputType. При вызове метода клиентский код предоставляет тип, который заменяет каждое вхождение идентификатора в теле метода или класса. Дополнительные сведения см. в разделе [Параметры универсального типа](/dotnet/csharp/programming-guide/generics/generic-type-parameters).  
  
```  
// CS0081.cs class MyClass { public void F<int>() {}   // CS0081 public void F<T>(T input) {}   // OK public static void Main() { MyClass a = new MyClass(); a.F<int>(2); a.F<double>(.05); } }  
```  
  
## См. также  
 [Универсальные шаблоны](/dotnet/csharp/programming-guide/generics/index)