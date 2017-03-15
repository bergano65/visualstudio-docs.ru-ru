---
title: "Ошибка компилятора CS0663 | Microsoft Docs"
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
  - "CS0663"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0663"
ms.assetid: 9f96c42b-dcc8-4a0f-8404-289fc88dba5e
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0663
Не может определять перегруженные методы, которые различаются только параметрами ref и out  
  
 Не допускается применять методы, которые отличаются только использованием модификаторов [ref](/dotnet/csharp/language-reference/keywords/ref) и [out](/dotnet/csharp/language-reference/keywords/out) в параметре.  
  
 Следующий пример приводит к возникновению ошибки CS0663:  
  
```  
// CS0663.cs class TestClass { public static void Main() { } public void Test(ref int i) { } public void Test(out int i)   // CS0663 { } }  
```