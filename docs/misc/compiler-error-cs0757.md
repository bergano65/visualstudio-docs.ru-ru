---
title: "Ошибка компилятора CS0757 | Microsoft Docs"
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
  - "CS0757"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0757"
ms.assetid: ba093570-306d-4b7b-aad5-1a3855ad6776
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0757
Разделяемый метод не может иметь несколько реализующих объявлений.  
  
 Разделяемый метод состоит из определяющего объявления \(сигнатуры\) и необязательного реализующего объявления \(тела\). Не допускаются несколько реализующих объявлений для одних и тех же определяющих объявлений. Разделяемые методы можно перегружать, и каждая перегруженная версия может иметь не более одного реализующего объявления.  
  
### Исправление ошибки  
  
1.  Удалите все определяющие объявления для разделяемого метода, кроме одного.  
  
## Пример  
 В следующем примере возникает ошибка CS0757:  
  
```  
// cs0757.cs using System; public partial class C { // Defining declaration. partial void Part(); // Implementing declaration. partial void Part() { //...Do something. } // Second implementing declaration. partial void Part() // CS0757 { //...Do something. } public static int Main() { return 1; } }  
```  
  
## См. также  
 [Разделяемые классы и методы](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)