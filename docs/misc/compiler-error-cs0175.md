---
title: "Ошибка компилятора CS0175 | Microsoft Docs"
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
  - "CS0175"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0175"
ms.assetid: cedd769d-8258-4235-a321-362981b9f84b
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0175
Использование ключевого слова "base" в этом контексте не допускается.  
  
 Для указания определенного члена базового класса необходимо использовать ключевое слово [базовые](/dotnet/csharp/language-reference/keywords/base). Для получения дополнительной информации см. [Конструкторы](/dotnet/csharp/programming-guide/classes-and-structs/constructors).  
  
 Следующий пример приводит к возникновению ошибки CS0175:  
  
```  
// CS0175.cs using System; class BaseClass { public int TestInt = 0; } class MyClass : BaseClass { public static void Main() { MyClass aClass = new MyClass(); aClass.BaseTest(); } public void BaseTest() { Console.WriteLine(base); // CS0175 // Try the following line instead: // Console.WriteLine(base.TestInt); base = 9;   // CS0175 // Try the following line instead: // base.TestInt = 9; } }  
```