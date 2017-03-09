---
title: "Ошибка компилятора CS0828 | Microsoft Docs"
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
  - "CS0828"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0828"
ms.assetid: e18ffe72-2fcc-436d-be7f-8c8365b86129
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0828
Невозможно присвоить "выражение" свойству анонимного типа.  
  
 Анонимный тип нельзя инициализировать значением NULL, небезопасным типом, группой методов или анонимной функцией.  
  
### Исправление ошибки  
  
1.  Либо добавьте объявление типа слева от присвоения, либо измените выражение справа на допустимый тип.  
  
## Пример  
 Так как член анонимного типа нельзя инициализировать значением NULL, в приведенном ниже коде возникает ошибка CS0828.  
  
```  
// cs0828.cs using System; public class C { public static int Main() { var a = 1; var c = new { p1 = null }; // CS0828 return 1; } }  
```  
  
## См. также  
 [Неявно типизированные локальные переменные](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)