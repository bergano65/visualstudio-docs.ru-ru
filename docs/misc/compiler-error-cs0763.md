---
title: "Ошибка компилятора CS0763 | Microsoft Docs"
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
  - "CS0763"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0763"
ms.assetid: 940870ba-1250-4365-acaa-7f968ee96c5b
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0763
Оба объявления разделяемого метода должны быть статическими, или ни одно из объявлений не должно быть статическим.  
  
 Объявление разделяемого метода не может иметь одну часть статическую, а другую часть не статическую.  
  
### Исправление ошибки  
  
1.  Сделайте обе части либо статическими, либо не статическими.  
  
## Пример  
 В следующем коде возникает ошибка CS0763:  
  
```  
// cs0763.cs using System; public partial class C { static partial void Part(); partial void Part() // CS0763 { } public static int Main() { return 1; } }  
```  
  
## См. также  
 [Разделяемые классы и методы](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)   
 [статический](/dotnet/csharp/language-reference/keywords/static)