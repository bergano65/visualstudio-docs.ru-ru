---
title: "Ошибка компилятора CS0192 | Microsoft Docs"
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
  - "CS0192"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0192"
ms.assetid: d3fb6d18-dbf3-42c3-a280-afe55b97c2d1
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0192
Поля доступного только для чтения статического поля "имя" могут передаваться как параметры с ключевым словом ref или out только в статическом конструкторе  
  
 Поле \(переменная\), помеченная ключевым словом [readonly](/dotnet/csharp/language-reference/keywords/readonly), не может быть передано параметру с ключевым словом [ref](/dotnet/csharp/language-reference/keywords/ref) или [out](/dotnet/csharp/language-reference/keywords/out), кроме как внутри конструктора. Для получения дополнительной информации см. [Поля](/dotnet/csharp/programming-guide/classes-and-structs/fields).  
  
 Ошибка CS0192 также возникает, если поле `readonly` является [static](/dotnet/csharp/language-reference/keywords/static) \(статическим\), а конструктор не помечен как `static`.  
  
## Пример  
 Следующий пример приводит к возникновению ошибки CS0192:  
  
```  
// CS0192.cs class MyClass { public readonly int TestInt = 6; static void TestMethod(ref int testInt) { testInt = 0; } MyClass() { TestMethod(ref TestInt);   // OK } public void PassReadOnlyRef() { TestMethod(ref TestInt);   // CS0192 } public static void Main() { } }  
```