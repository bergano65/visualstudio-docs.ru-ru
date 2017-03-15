---
title: "Ошибка компилятора CS1611 | Microsoft Docs"
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
  - "CS1611"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1611"
ms.assetid: 48bfba77-6be2-4242-b1d2-98bf471b6d1e
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1611
Параметр params не может объявляться как параметр с ключевым словом ref или out.  
  
 Ключевые слова [ref](/dotnet/csharp/language-reference/keywords/ref) или [out](/dotnet/csharp/language-reference/keywords/out) не могут использоваться с ключевым словом [params](/dotnet/csharp/language-reference/keywords/params).  
  
 В следующем примере возникает ошибка CS1611:  
  
```  
// CS1611.cs public class MyClass { public static void Test(params ref int[] a)   // CS1611, remove ref { } public static void Main() { Test(1); } }  
```