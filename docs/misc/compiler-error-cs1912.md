---
title: "Ошибка компилятора CS1912 | Microsoft Docs"
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
  - "CS1912"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1912"
ms.assetid: 6205420e-01b9-4470-89f9-5924f1e49108
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1912
Повторная инициализация члена "имя".  
  
 Инициализатор объектов может инициализировать каждый член только один раз.  
  
### Исправление ошибки  
  
1.  Удалите вторую инициализацию члена в инициализаторе объекта.  
  
## Пример  
 В следующем коде возникает ошибка CS1912, так как `memberA` инициализируется дважды:  
  
```  
// cs1912.cs using System.Linq; public class TestClass { public int memberA { get; set; } public int memberB { get; set; } } public class Test { static void Main() { TestClass tc = new TestClass() { memberA = 5, memberA = 6, memberB = 2}; // CS1912 } }  
```  
  
## См. также  
 [Инициализаторы объектов и коллекций](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers)