---
title: "Ошибка компилятора CS0179 | Microsoft Docs"
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
  - "CS0179"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0179"
ms.assetid: bef000ca-64d7-4809-b2a0-de6927b04b0d
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0179
Член "член" не может иметь модификатор extern и объявлять тело.  
  
 Если член класса помечен как [extern](/dotnet/csharp/language-reference/keywords/extern), это означает, что определение этого члена находится в другом файле. Таким образом член класса, помеченный как **extern** , не может быть определен в классе. Удалите ключевое слово `extern` или удалите определение. Для получения дополнительной информации см. [Методы](/dotnet/csharp/programming-guide/classes-and-structs/methods).  
  
 Следующий пример приводит к возникновению ошибки CS0179:  
  
```  
// CS0179.cs public class MyClass { public extern int ExternMethod(int aa)   // CS0179 { return 0; } // try the following line instead // public extern int ExternMethod(int aa); public static void Main() { } }  
```