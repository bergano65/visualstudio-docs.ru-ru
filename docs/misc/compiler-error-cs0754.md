---
title: "Ошибка компилятора CS0754 | Microsoft Docs"
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
  - "CS0754"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0754"
ms.assetid: c83e04b5-6ab5-45c2-805e-0ba4f041d506
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0754
Разделяемый метод не может явно реализовывать метод интерфейса  
  
 Разделяемый метод не может быть объявлен в качестве явной реализации метода, определенного в интерфейсе.  
  
### Исправление ошибки  
  
1.  Удалите явную квалификацию интерфейса из объявления метода.  
  
## Пример  
 При компиляции следующего кода возникнет ошибка CS0754:  
  
```  
// cs0754.cs using System; public interface IF { void Part(); } public partial class C : IF { partial void IF.Part(); //CS0754 public static int Main() { return 1; } }  
```  
  
## См. также  
 [Явная реализация интерфейса](/dotnet/csharp/programming-guide/interfaces/explicit-interface-implementation)   
 [Разделяемые классы и методы](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)