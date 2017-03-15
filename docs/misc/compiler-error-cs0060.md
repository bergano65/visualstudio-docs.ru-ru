---
title: "Ошибка компилятора CS0060 | Microsoft Docs"
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
  - "CS0060"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0060"
ms.assetid: ae6d4fb7-5ff9-4883-82c3-f55b190f439a
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0060
Несогласованность по доступности: доступность базового класса "класс1" ниже доступности класса "класс2"  
  
 Доступность класса должна быть согласованной между базовым классом и унаследованным классом.  
  
 Следующий пример приводит к возникновению ошибки CS0060:  
  
```  
// CS0060.cs class MyClass // try the following line instead // public class MyClass { } public class MyClass2 : MyClass   // CS0060 { public static void Main() { } }  
```  
  
## См. также  
 [Модификаторы доступа](/dotnet/csharp/programming-guide/classes-and-structs/access-modifiers)