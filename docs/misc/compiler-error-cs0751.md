---
title: "Ошибка компилятора CS0751 | Microsoft Docs"
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
  - "CS0751"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0751"
ms.assetid: 2ebaed5f-d3ca-452f-8fce-f3299b84360a
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0751
Разделяемый метод должен быть объявлен в разделяемом классе или разделяемой структуре  
  
 Невозможно объявить [разделяемый](/dotnet/csharp/language-reference/keywords/partial-method) метод, если он не инкапсулирован в разделяемом классе или разделяемой структуре.  
  
### Исправление ошибки  
  
1.  Удалите модификатор `partial` из метода и предоставьте реализацию или добавьте модификатор `partial` во включающий класс или структуру.  
  
## Пример  
 В следующем примере возникает ошибка CS0751:  
  
```  
// cs0751.cs using System; public class C { partial void Part(); // CS0751 public static int Main() { return 1; } }  
```  
  
## См. также  
 [Разделяемые классы и методы](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)