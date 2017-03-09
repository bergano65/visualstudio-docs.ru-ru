---
title: "Ошибка компилятора CS1105 | Microsoft Docs"
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
  - "CS1105"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1105"
ms.assetid: fcbd91ad-a76a-4b22-868d-16824fa96f85
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1105
Методы расширения должны быть статическими.  
  
 Методы расширения должны объявляться как статические методы в неуниверсальном статическом классе.  
  
## Пример  
 В следующем примере возникает ошибка CS1105, поскольку `Test` не является статическим.  
  
```  
// cs1105.cs // Compile with: /target:library public class Extensions { // Single type parameter. public void Test<T>(this System.String s) {} //CS1105 }  
```  
  
## См. также  
 [Методы расширения](/dotnet/csharp/programming-guide/classes-and-structs/extension-methods)   
 [статический](/dotnet/csharp/language-reference/keywords/static)