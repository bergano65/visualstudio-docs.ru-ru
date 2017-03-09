---
title: "Ошибка компилятора CS0199 | Microsoft Docs"
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
  - "CS0199"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0199"
ms.assetid: 9eede3f2-b55a-4b85-a05d-6bf177e1c602
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0199
Поля доступного только для чтения статического поля "имя" могут передаваться как параметры с ключевым словом ref или out только в статическом конструкторе  
  
 Переменная, помеченная модификатором [readonly](/dotnet/csharp/language-reference/keywords/readonly), должна содержать тот же модификатор использования [static](/dotnet/csharp/language-reference/keywords/static), что и конструктор, в который ее необходимо передать в качестве параметра [ref](/dotnet/csharp/language-reference/keywords/ref) или [out](/dotnet/csharp/language-reference/keywords/out). Дополнительные сведения см. в разделе [Передача параметров](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters).  
  
## Пример  
 Следующий пример приводит к возникновению ошибки CS0199:  
  
```  
// CS0199.cs class MyClass { public static readonly int TestInt = 6; static void TestMethod(ref int testInt) { testInt = 0; } MyClass() { TestMethod(ref TestInt);   // CS0199, TestInt is static } public static void Main() { } }  
```