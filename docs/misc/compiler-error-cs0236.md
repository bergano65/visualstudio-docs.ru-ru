---
title: "Ошибка компилятора CS0236 | Microsoft Docs"
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
  - "CS0236"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0236"
ms.assetid: 1522c421-744f-441f-9e05-6bb31311ab2a
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0236
Инициализатор поля не может обращаться к нестатическому полю, методу или свойству "поле"  
  
 Поля экземпляра не могут использоваться для инициализации других полей экземпляра за пределами метода. При попытке инициализировать переменную за пределами метода выполняйте инициализацию в конструкторе класса. Для получения дополнительной информации см. [Методы](/dotnet/csharp/programming-guide/classes-and-structs/methods).  
  
 В следующем примере происходит ошибка CS0236:  
  
```  
// CS0236.cs public class MyClass { public int i = 5; public int j = i;  // CS0236 public int k;      // initialize in constructor MyClass() { k = i; } public static void Main() { } }  
```