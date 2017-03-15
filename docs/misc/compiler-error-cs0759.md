---
title: "Ошибка компилятора CS0759 | Microsoft Docs"
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
  - "CS0759"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0759"
ms.assetid: 96f0e178-adbf-4327-8934-ac282c428184
caps.latest.revision: 4
caps.handback.revision: 4
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0759
Отсутствует определяющее объявление для реализующего объявления разделяемого метода "метод".  
  
 Разделяемый метод должен иметь определяющее объявление, которое определяет сигнатуру метода \(имя, тип возвращаемого значения и параметры\). Реализация тела метода необязательна.  
  
### Исправление ошибки  
  
1.  Укажите определяющее объявление разделяемого метода в другой части разделяемого класса или структуры.  
  
## Пример  
 При компиляции следующего примера возникнет ошибка CS0759:  
  
```  
// cs0759.cs using System; public partial class C { partial void Part() // CS0759 { } public static int Main() { return 1; } }  
```  
  
## См. также  
 [Разделяемые классы и методы](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)