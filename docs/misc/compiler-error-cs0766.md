---
title: "Ошибка компилятора CS0766 | Microsoft Docs"
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
  - "CS0766"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0766"
ms.assetid: 4574e30b-3e76-42cd-90e8-31c72126a08c
caps.latest.revision: 4
caps.handback.revision: 4
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0766
Разделяемые методы должны иметь тип возвращаемого значения void.  
  
 Разделяемый метод не может возвращать значение. Его типом возврата должен быть void.  
  
### Исправление ошибки  
  
1.  Присвойте разделяемому методу тип возврата void или преобразуйте метод в обычный \(не разделяемый\) метод.  
  
## Пример  
 В следующем примере возникает ошибка CS0766:  
  
```  
// cs0766.cs using System; public partial class C { partial int Part(); // CS0766 // Typically the implementing declaration // is contained in a separate file. partial int Part() //CS0766 { } public static int Main() { return 1; } }  
```  
  
## См. также  
 [Разделяемые классы и методы](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)