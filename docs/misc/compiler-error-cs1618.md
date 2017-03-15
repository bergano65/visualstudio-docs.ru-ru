---
title: "Ошибка компилятора CS1618 | Microsoft Docs"
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
  - "CS1618"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1618"
ms.assetid: e046d402-208e-48fd-8ff3-bb03044036c4
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1618
Невозможно создать делегат с "метод", так как он имеет атрибут Conditional  
  
 Невозможно создать делегат с помощью условного метода, так как метод может отсутствовать в некоторых сборках.  
  
 Следующий пример приводит к возникновению ошибки CS1618:  
  
```  
// CS1618.cs using System; using System.Diagnostics; delegate void del(); class MakeAnError { public static void Main() { del d = new del(ConditionalMethod);   // CS1618 // Invalid because on builds where DEBUG is not set, // there will be no "ConditionalMethod". } // To fix the error, remove the next line: [Conditional("DEBUG")] public static void ConditionalMethod() { Console.WriteLine("Do something only in debug"); } }  
```