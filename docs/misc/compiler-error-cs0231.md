---
title: "Ошибка компилятора CS0231 | Microsoft Docs"
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
  - "CS0231"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0231"
ms.assetid: e5e6a8e1-6c9f-4a88-8935-7bedfba88f8c
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0231
Параметр params должен быть указан последним в списке формальных параметров.  
  
 Параметр [params](/dotnet/csharp/language-reference/keywords/params) поддерживает переменное число аргументов и должен указываться после всех остальных параметров. Для получения дополнительной информации см. [Методы](/dotnet/csharp/programming-guide/classes-and-structs/methods).  
  
 Следующий пример приводит к возникновению ошибки CS0231:  
  
```  
// CS0231.cs class Test { public void TestMethod(params int[] p, int i) {} // CS0231 // To resolve the error, use the following line instead: // public void TestMethod(int i, params int[] p) {} static void Main() { } }  
```