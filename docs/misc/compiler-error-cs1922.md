---
title: "Ошибка компилятора CS1922 | Microsoft Docs"
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
  - "CS1922"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1922"
ms.assetid: a4098a25-6581-4966-b61d-318cd12f76d3
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1922
Для реализации интерфейса System.Collections.IEnumerable инициализатору коллекции требуется тип "тип".  
  
 Чтобы использовать инициализатор коллекции с типом, этот тип должен реализовывать интерфейс `IEnumerable`. Эта ошибка может возникать, если вместо синтаксиса инициализатора объекта вы случайно используете синтаксис инициализатора коллекции.  
  
### Исправление ошибки  
  
-   Если тип не представляет коллекцию, то вместо синтаксиса инициализатора коллекции следует использовать синтаксис инициализатора объекта.  
  
-   Если тип представляет коллекцию, измените его, чтобы он реализовал интерфейс `IEnumerable`, прежде чем использовать инициализаторы коллекции для инициализации объектов этого типа.  
  
-   Если тип представляет коллекцию, но его исходный код недоступен, просто инициализируйте элементы этого типа с помощью конструкторов их класса или других методов инициализации.  
  
## Пример  
 Приведенный ниже код приводит к возникновению ошибки CS1922.  
  
```  
// cs1922.cs public class Test { public static void Main() { // Collection initializer. var tc = new TestClass  {1,"hello"} ; // CS1922 // Object initalizer. var tc2 = new TestClass { memberA = 1, memberB = "hello" }; // OK } } public class TestClass { public int memberA { get; set; } public string memberB { get; set; } }  
  
```  
  
## См. также  
 [Инициализаторы объектов и коллекций](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers)