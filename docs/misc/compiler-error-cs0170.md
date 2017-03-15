---
title: "Ошибка компилятора CS0170 | Microsoft Docs"
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
  - "CS0170"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0170"
ms.assetid: ba881e38-2abf-4a5f-b9e6-28d26a5bd235
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0170
Использование поля "поле", которому, возможно, не присвоено значение.  
  
 Поле в структуре было использовано без предварительной инициализации. Чтобы решить эту проблему, сначала определите, какое поле не было инициализировано, а затем инициализируйте его, прежде чем пытаться получить к нему доступ. Дополнительные сведения об инициализации структур см. в разделах [Структуры](/dotnet/csharp/programming-guide/classes-and-structs/structs) и [Использование структур](/dotnet/csharp/programming-guide/classes-and-structs/using-structs).  
  
 Следующий пример приводит к возникновению ошибки CS0170:  
  
```  
// CS0170.cs public struct error { public int i; } public class MyClass { public static void Main() { error e; // uncomment the next line to resolve this error // e.i = 0; System.Console.WriteLine( e.i );   // CS0170 because //e.i was never assigned } }  
```