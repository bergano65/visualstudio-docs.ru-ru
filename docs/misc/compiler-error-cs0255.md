---
title: "Ошибка компилятора CS0255 | Microsoft Docs"
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
  - "CS0255"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0255"
ms.assetid: b45f5d5a-1923-4fe1-a858-e5ef5590a108
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0255
stackalloc не может использоваться в блоке catch или в блоке finally.  
  
 Ключевое слово [stackalloc](/dotnet/csharp/language-reference/keywords/stackalloc) не может использоваться в блоке [catch](/dotnet/csharp/language-reference/keywords/try-catch) или в блоке [finally](/dotnet/csharp/language-reference/keywords/try-catch-finally). Для получения дополнительной информации см. [Исключения и обработка исключений](/dotnet/csharp/programming-guide/exceptions/exceptions-and-exception-handling).  
  
 В следующем примере возникает ошибка CS0255:  
  
```  
// CS0255.cs // compile with: /unsafe using System; public class TestTryFinally { public static unsafe void Test() { int i = 123; string s = "Some string"; object o = s; try { // Conversion is not valid; o contains a string not an int i = (int) o; } finally { Console.Write("i = {0}", i); int* fib = stackalloc int[100];   // CS0255 } } public static void Main() { } }  
```