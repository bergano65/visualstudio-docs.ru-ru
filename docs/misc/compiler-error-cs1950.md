---
title: "Ошибка компилятора CS1950 | Microsoft Docs"
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
  - "CS1950"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1950"
ms.assetid: e37fb5b1-09e0-47a6-9db5-a48f90ea7bbb
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1950
Наиболее подходящий перегруженный метод Add "имя" для инициализатора коллекции содержит недопустимые аргументы.  
  
 Для поддержки инициализаторов коллекций класс должен реализовывать IEnumerable и иметь открытый метод `Add`. Для инициализации типа с помощью инициализатора коллекции входной параметр метода `Add` должен быть совместим с типом объекта, который вы пытаетесь добавить.  
  
### Исправление ошибки  
  
-   Используйте совместимый тип в инициализаторе коллекции.  
  
-   Измените входной параметр и\/или доступность метода `Add` в типе коллекции.  
  
-   Добавьте новый метод `Add` с входным параметром, соответствующим тому, что вы передаете.  
  
-   Сделайте ваш класс коллекции универсальным, чтобы он мог иметь метод `Add`, который принимает любой переданный в него тип.  
  
## Пример  
 Следующий пример приводит к возникновению ошибки CS1950:  
  
```  
// cs1950.cs using System.Collections; class TestClass : CollectionBase { public void Add(int c) { } } class Test { static void Main() { TestClass t = new TestClass { "hi" }; // CS1950 } }  
```  
  
## См. также  
 [Инициализаторы объектов и коллекций](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers)