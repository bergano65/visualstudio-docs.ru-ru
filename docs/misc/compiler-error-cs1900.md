---
title: "Ошибка компилятора CS1900 | Microsoft Docs"
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
  - "CS1900"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1900"
ms.assetid: 08141138-bfea-4af3-a9a0-ec54cf2caa13
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1900
Уровень предупреждений должен быть в диапазоне 0–4.  
  
 Параметр компилятора [\/warn](/dotnet/csharp/language-reference/compiler-options/warn-compiler-option) принимает только одно из пяти возможных значений \(0, 1, 2, 3 или 4\). При передаче параметру **\/warn** любого другого значения происходит ошибка CS1900.  
  
 Следующий пример приводит к возникновению ошибки CS1900:  
  
```  
// CS1900.cs // compile with: /W:5 // CS1900 expected class x { public static void Main() { } }  
```