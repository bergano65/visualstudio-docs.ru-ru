---
title: "Ошибка компилятора CS0191 | Microsoft Docs"
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
  - "CS0191"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0191"
ms.assetid: 512479e4-656e-4dcb-8d71-801541d72dcd
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0191
Невозможно присвоить значение свойству или индексатору "имя" — доступ только для чтения  
  
 Поле [readonly](/dotnet/csharp/language-reference/keywords/readonly) принимает назначение только в конструкторе или в объявлении. Дополнительные сведения см. в разделе [Конструкторы](/dotnet/csharp/programming-guide/classes-and-structs/constructors).  
  
 Ошибка CS0191 также возникает, если поле `readonly` является [static](/dotnet/csharp/language-reference/keywords/static) \(статическим\), а конструктор не помечен как `static`.  
  
## Пример  
 В следующем примере возникает ошибка CS0191:  
  
```  
// CS0191.cs class MyClass { public readonly int TestInt = 6;  // OK to assign to readonly field in declaration MyClass() { TestInt = 11; // OK to assign to readonly field in constructor } public void TestReadOnly() { TestInt = 19;                  // CS0191 } public static void Main() { } }  
```