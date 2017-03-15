---
title: "Ошибка компилятора CS0180 | Microsoft Docs"
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
  - "CS0180"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0180"
ms.assetid: a21bf0a2-ed5a-4ddd-88d3-240babc5888a
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0180
"член" не может одновременно быть внешним и абстрактным  
  
 Ключевые слова [abstract](/dotnet/csharp/language-reference/keywords/abstract) и [extern](/dotnet/csharp/language-reference/keywords/extern) являются взаимоисключающими. Ключевое слово `extern` означает, что член определен за пределами файла, а ключевое слово **abstract** указывает на то, что реализация предоставлена в производном классе. Дополнительные сведения см. в разделе [Методы](/dotnet/csharp/programming-guide/classes-and-structs/methods).  
  
 Следующий пример приводит к возникновению ошибки CS0180:  
  
```  
// CS0180.cs namespace MyNamespace { public class MyClass { public extern abstract int Foo(int a);   // CS0180 public static void Main() { } } }  
```