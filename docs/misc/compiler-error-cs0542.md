---
title: "Ошибка компилятора CS0542 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0542"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0542"
ms.assetid: 68a89948-8b56-4cd5-95e2-0df7fcad50ac
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0542
"определенный пользователем тип": имена членов не могут совпадать с именем типа, в который они входят  
  
 Члены класса или структуры не могут иметь то же имя, что у класса или структуры, если член не является конструктором.  
  
 Следующий пример приводит к возникновению ошибки CS0542:  
  
```c#  
// CS0542.cs class C { public int C; }  
```  
  
 Эта ошибка может возникнуть, если вы случайно задали для конструктора тип возвращаемого значения, что фактически превращает его в обычный метод. Следующий пример приводит к возникновению ошибки CS0542, так как `F` является методом, а не конструктором, поскольку имеет тип возвращаемого значения:  
  
```c#  
// CS0542.cs class F { // Remove void from F() to resolve the problem. void F()   // CS0542, same name as the class { } } class MyClass { public static void Main() { } }  
```  
  
 Эта ошибка может возникнуть, если ваш класс называется Item и содержит индексатор, объявленный как `this`. Индексатору по умолчанию дается имя Item в порожденном коде, что создает конфликт.  
  
```c#  
// CS0542b.cs class Item { public int this[int i]  // CS0542 { get { return 0; } } } class CMain { public static void Main() { } }  
```