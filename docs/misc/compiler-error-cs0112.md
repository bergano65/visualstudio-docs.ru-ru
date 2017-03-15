---
title: "Ошибка компилятора CS0112 | Microsoft Docs"
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
  - "CS0112"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0112"
ms.assetid: 6741c7c4-8553-4bbe-b950-4f908e8d9ba3
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0112
Статический член "функция" не может быть помечен как override, virtual или abstract  
  
 Любое объявление метода, которое использует ключевое слово `override`, **virtual** или **abstract**, не может использовать ключевое слово **static**.  
  
 Дополнительные сведения см. в разделе [Методы](/dotnet/csharp/programming-guide/classes-and-structs/methods).  
  
 При компиляции следующего примера возникнет ошибка CS0112:  
  
```  
// CS0112.cs namespace MyNamespace { abstract public class MyClass { public abstract void Foo(); } public class MyClass2 : MyClass { override public static void Foo()   // CS0112, remove static keyword { } public static int Main() { return 0; } } }  
```