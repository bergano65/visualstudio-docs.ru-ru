---
title: "Ошибка компилятора CS0156 | Microsoft Docs"
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
  - "CS0156"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0156"
ms.assetid: 32026b1b-bcd7-4464-b63f-3b38c00452a6
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0156
Недопустимо использовать оператор throw без аргументов в предложении finally, которая находится в ближайшем вложенном предложении catch.  
  
 Оператор [throw](/dotnet/csharp/language-reference/keywords/throw) без параметров может использоваться только в предложении **catch**, которое не принимает параметров.  
  
 Дополнительные сведения см. в разделах [Операторы обработки исключений](/dotnet/csharp/language-reference/keywords/exception-handling-statements) и [Исключения и обработка исключений](/dotnet/csharp/programming-guide/exceptions/exceptions-and-exception-handling).  
  
 Следующий пример приводит к возникновению ошибки CS0156.  
  
```  
// CS0156.cs using System; namespace MyNamespace { public class MyClass2 : Exception { } public class MyClass { public static void Main() { try { throw;   // CS0156 } catch(MyClass2) { throw;   // this throw is valid } } } }  
```