---
title: "Ошибка компилятора CS0622 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0622"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0622"
ms.assetid: aef77a69-d8b7-41f8-9539-258deaef5cc4
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0622
Для назначения типов массивов можно использовать только выражения инициализатора массивов. Попробуйте использовать новое выражение.  
  
 В объявлении типов, отличных от типа массива, использовался синтаксис, применяемый для инициализации массива.  
  
## Пример  
 В следующем примере возникает ошибка CS0622:  
  
```  
// CS0622.cs using System; public class Test { public static void Main () { Test t = { new Test() };   // CS0622 // Try the following instead: // Test[] t = { new Test() }; } }  
```