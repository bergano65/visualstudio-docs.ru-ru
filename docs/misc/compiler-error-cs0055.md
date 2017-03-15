---
title: "Ошибка компилятора CS0055 | Microsoft Docs"
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
  - "CS0055"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0055"
ms.assetid: 4d98abf3-2690-4418-8fd0-50c0e67d0a4a
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0055
Несогласованность по доступности: доступность типа параметра "тип" ниже доступности индексатора "индексатор"  
  
 Открытая конструкция должна возвращать общедоступный объект. Дополнительные сведения см. в разделе [Модификаторы доступа](/dotnet/csharp/programming-guide/classes-and-structs/access-modifiers).  
  
 В следующем примере возникает ошибка CS0055:  
  
```  
// CS0055.cs class MyClass //defaults to private accessibility // try the following line instead // public class MyClass { } public class MyClass2 { public int this[MyClass myClass]   // CS0055 { get { return 0; } } } public class MyClass3 { public static void Main() { } }  
```