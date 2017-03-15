---
title: "Ошибка компилятора CS2007 | Microsoft Docs"
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
  - "CS2007"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS2007"
ms.assetid: 9be20e8e-2424-4435-9371-778fb12823c0
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS2007
Нераспознанный параметр командной строки: "параметр"  
  
 Компилятору передана строка, которая не является [параметром компилятора](/dotnet/csharp/language-reference/compiler-options/index), хотя и начинается со знака косой черты \(\/\).  
  
 Следующий пример приводит к возникновению ошибки CS2007:  
  
```  
// CS2007.cs // compile with: /recur // CS2007 expected class x { public static void Main() {} }  
```