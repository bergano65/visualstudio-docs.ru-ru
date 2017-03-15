---
title: "Ошибка компилятора CS1520 | Microsoft Docs"
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
  - "CS1520"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1520"
ms.assetid: 1aeeee83-52a6-45dc-b197-a9a6de3a220c
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1520
Метод должен иметь тип возвращаемого значения  
  
 Метод, объявленный в классе, структуре или интерфейсе, должен иметь явный тип возврата. В следующем примере метод Square имеет возвращаемое значение [string](/dotnet/csharp/language-reference/keywords/string):  
  
```  
class Test { string IntToString(int i) { return i.ToString(); } }  
```  
  
 Следующий пример приводит к возникновению ошибки CS1520:  
  
```  
// CS1520a.cs public class x { // Method declaration missing a return type MyMethod()   // CS1520 {} // Add the desired return type: // void MyMethod2() // { } public static void Main() { } }  
```  
  
 Кроме того, эта ошибка может возникать, когда регистр имени конструктора отличается от регистра объявления класса или структуры, как в следующем примере. Поскольку имя не точно совпадает с именем класса, компилятор интерпретирует его как обычный метод, а не конструктор, и в результате возникает ошибка:  
  
```  
// CS1520b.cs public class Class1 { // Should be Class1, not class1 public class1()   // CS1520 { } static void Main() { } }  
```  
  
## См. также  
 [Методы](/dotnet/csharp/programming-guide/classes-and-structs/methods)   
 [Конструкторы](/dotnet/csharp/programming-guide/classes-and-structs/constructors)