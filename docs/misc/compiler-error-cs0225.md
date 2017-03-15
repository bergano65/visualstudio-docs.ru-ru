---
title: "Ошибка компилятора CS0225 | Microsoft Docs"
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
  - "CS0225"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0225"
ms.assetid: 0b0cd72b-c47a-44d1-9b27-d1a1fad06807
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0225
Параметр params должен быть одномерным массивом.  
  
 При использовании ключевого слова [params](/dotnet/csharp/language-reference/keywords/params) необходимо указать одномерный массив типа данных. Дополнительные сведения см. в разделе [Методы](/dotnet/csharp/programming-guide/classes-and-structs/methods).  
  
## Пример  
 Следующий пример приводит к возникновению ошибки CS0225:  
  
```  
// CS0225.cs public class MyClass { public static void TestParams(params int a)   // CS0225 // try the following line instead // public static void TestParams(params int[] a) { } public static void Main() { TestParams(1); } }  
```