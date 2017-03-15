---
title: "Ошибка компилятора CS0819 | Microsoft Docs"
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
  - "CS0819"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0819"
ms.assetid: a5369e03-eb7d-4c88-b390-51304bd8d1ae
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0819
Неявно типизированные локальные переменные не могут быть многократно объявлены.  
  
 В объявлениях, в которых тип задается явным образом, можно использовать несколько операторов объявления, однако в случае неявно типизированных переменных этого делать нельзя.  
  
### Исправление ошибки  
  
1.  Объявите каждую неявно типизированную локальную переменную и присвойте ей значение в отдельной строке.  
  
## Пример  
 Следующий код приводит к возникновению ошибки CS0819:  
  
```  
// cs0819.cs class A { public static int Main() { var a = 3, b = 2; // CS0819 return -1; } }  
```  
  
## См. также  
 [Неявно типизированные локальные переменные](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)