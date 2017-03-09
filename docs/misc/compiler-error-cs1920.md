---
title: "Ошибка компилятора CS1920 | Microsoft Docs"
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
  - "CS1920"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1920"
ms.assetid: efb4782f-a222-4fb5-9e79-8bd2d380520b
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1920
Инициализатор элемента не может быть пустым.  
  
 Инициализатор коллекции состоит из последовательности инициализаторов элементов. Инициализаторы элементов не требуется заключать в фигурные скобки, если они не содержат выражение назначения. Однако если вы указали фигурные скобки, они не могут быть пустыми. Если инициализатор элемента является инициализатором объекта, фигурные скобки могут быть пустыми, пока инициализатор содержит выражение создания нового объекта.  
  
### Исправление ошибки  
  
-   Добавьте отсутствующее выражение между фигурными скобками.  
  
-   Если выражение предназначено быть инициализатором объектов, добавьте выражение создания нового объекта перед фигурными скобками.  
  
## Пример  
 Следующий пример приводит к возникновению ошибки CS1920:  
  
```  
// cs1920.cs using System.Collections.Generic; public class Test { public static int Main() { // Error. Empty initializer // for inner list. List<List<int>> collection = new List<List<int>>() { { } }; // CS1920 // OK. No initializer for inner list. List<List<int>> collection2 = new List<List<int>>() {  }; // OK. Inner list is initialized // to one List<int> with zero elements. List<List<int>> collection3 = new List<List<int>>() { new List<int> { } }; return 0; } }  
```  
  
## См. также  
 [Инициализаторы объектов и коллекций](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers)