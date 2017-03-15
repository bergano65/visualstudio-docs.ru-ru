---
title: "Ошибка компилятора CS1106 | Microsoft Docs"
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
  - "CS1106"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1106"
ms.assetid: 3585600a-6b2c-47aa-a418-ef049f07c107
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1106
Методы расширения должны быть определены в неуниверсальном статическом классе  
  
 Методы расширения должны быть определены как статические методы в неуниверсальном статическом классе.  
  
## Пример  
 В приведенном ниже примере возникает ошибка CS1106, так как класс `Extensions` не определен как `static`.  
  
```  
// cs1106.cs public class Extensions // CS1106 { public  static void Test<T>(this System.String s) {} }  
```  
  
## См. также  
 [Методы расширения](/dotnet/csharp/programming-guide/classes-and-structs/extension-methods)   
 [статический](/dotnet/csharp/language-reference/keywords/static)