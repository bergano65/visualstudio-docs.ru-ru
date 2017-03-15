---
title: "Ошибка компилятора CS0764 | Microsoft Docs"
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
  - "CS0764"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0764"
ms.assetid: 76a64149-49d8-40ea-a976-03835d8fb7eb
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0764
Либо оба объявления разделяемого метода должны иметь модификаторы unsafe, либо ни одно из объявлений не должно иметь модификатора unsafe.  
  
 Разделяемый метод состоит из определяющего объявления \(сигнатуры\) и необязательного реализующего объявления \(тела\). Если определяющее объявление содержит модификатор `unsafe`, этот модификатор должен содержаться и в реализующем объявлении. И наоборот, если реализующее объявление содержит модификатор `unsafe`, этот модификатор должен содержаться и в определяющем объявлении.  
  
### Исправление ошибки  
  
1.  Если определяющее объявление не содержит ошибок, добавьте или удалите модификатор `unsafe` в реализующем объявлении для соответствия с определяющим объявлением.  
  
## Пример  
  
```  
// cs0764.cs //  Compile with: /target:library /unsafe public partial class C { partial void Part(); unsafe partial void Part() //CS0764 { } public static int Main() { return 1; } }  
```  
  
## См. также  
 [Разделяемые классы и методы](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)