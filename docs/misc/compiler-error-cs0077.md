---
title: "Ошибка компилятора CS0077 | Microsoft Docs"
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
  - "CS0077"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0077"
ms.assetid: 55d3d290-d172-41a3-b326-ebf5a0a7e81f
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0077
Оператор as необходимо использовать с типом ссылки или типом, допускающим значение null \(int является типом, не допускающим значение null\).  
  
 В оператор [as](/dotnet/csharp/language-reference/keywords/as) был передан [тип значения](/dotnet/csharp/language-reference/keywords/value-types). Поскольку `as` может возвращать [null](/dotnet/csharp/language-reference/keywords/null), в него можно передавать только [ссылочные типы](/dotnet/csharp/language-reference/keywords/reference-types) или тип, допускающий значение null. Дополнительные сведения о типах, допускающих значение null, см. в разделе [Типы, допускающие значения NULL](/dotnet/csharp/programming-guide/nullable-types/index).  
  
 Следующий пример приводит к возникновению ошибки CS0077:  
  
```  
// CS0077.cs using System; class C { } struct S { } class M { public static void Main() { object o1, o2; C c; S s; o1 = new C(); o2 = new S(); s = o2 as S;  // CS0077, S is not a reference type. // try the following line instead // c = o1 as C; } }  
```