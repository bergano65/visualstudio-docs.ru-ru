---
title: "Ошибка компилятора CS1929 | Microsoft Docs"
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
  - "CS1929"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1929"
ms.assetid: effdd5d4-e156-418b-9d45-4ca194ab4319
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1929
Аргумент экземпляра: невозможно преобразовать из "типа A" в "тип B".  
  
 Эта ошибка возникает при попытке вызвать метод расширения из класса, который он не расширяет. В приведенном здесь примере метод расширения определен для производного класса `A`, но не для базового класса `B`.  
  
### Исправление ошибки  
  
1.  Создайте новый метод расширения для типа, где необходимо вызвать его, или переместите вызов в объект типа, который расширяет существующий метод.  
  
## Пример  
 Следующий код приводит к возникновению ошибок CS1928 и CS1929:  
  
```  
// cs1929.cs using System.Linq; using System.Collections; static class Ext { public static void ExtMethod(this A a) { } } class A : B { } class B { static void Main() { B b = new B(); b.ExtMethod(); // CS1929 } }  
```  
  
## См. также  
 [Методы расширения](/dotnet/csharp/programming-guide/classes-and-structs/extension-methods)