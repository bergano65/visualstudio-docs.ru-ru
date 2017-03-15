---
title: "Ошибка компилятора CS0756 | Microsoft Docs"
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
  - "CS0756"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0756"
ms.assetid: 847b20b0-bbf0-43a2-8728-4b54cb3d9cd6
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0756
Разделяемый метод не может иметь несколько определяющих объявлений.  
  
 В определяющем объявлении разделяемого метода определяется сигнатура метода, но не его реализация \(тело метода\). Для каждой уникальной сигнатуры разделяемый метод должен содержать одно и только одно определяющее объявление. Каждая перегруженная версия разделяемого метода должна содержать собственное определяющее объявление.  
  
### Исправление ошибки  
  
1.  Удалите все определяющие объявления разделяемого метода, кроме одного.  
  
## Пример  
  
```  
// cs0756.cs using System; public partial class C { partial void Part(); partial void Part(); // CS0756 public static int Main() { return 1; } }  
```  
  
## См. также  
 [Разделяемые классы и методы](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)