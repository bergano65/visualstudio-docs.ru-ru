---
title: "Ошибка компилятора CS0641 | Microsoft Docs"
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
  - "CS0641"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0641"
ms.assetid: 5bcdb11a-fefd-4c71-9b31-4c4f719633f3
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0641
Атрибут "атрибут" допустим только в классах, производных от System.Attribute  
  
 Применялся атрибут, который может использоваться только для класса, производного от **System.Attribute**.  
  
 Следующий пример приводит к возникновению ошибки CS0641:  
  
```  
// CS0641.cs using System; [AttributeUsage(AttributeTargets.All)] public class NonAttrClass   // CS0641 // try the following line instead // public class NonAttrClass : Attribute { } class MyClass { public static void Main() { } }  
```