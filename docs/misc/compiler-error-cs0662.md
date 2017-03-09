---
title: "Ошибка компилятора CS0662 | Microsoft Docs"
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
  - "CS0662"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0662"
ms.assetid: 836fa15e-3bf3-4af5-8acf-072d7d731dcd
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0662
"метод" не может задавать для параметра ref только атрибут Out. Используйте атрибуты In и Out вместе или не используйте их.  
  
 Метод интерфейса имеет параметр, который использует [ref](/dotnet/csharp/language-reference/keywords/ref) только с атрибутом [Out](frlrfSystemRuntimeInteropServicesOutAttributeClassTopic). Параметр `ref`, который использует атрибут **Out**, должен также использовать атрибут [In](frlrfSystemRuntimeInteropServicesInAttributeClassTopic).  
  
 Следующий пример приводит к возникновению ошибки CS0662:  
  
```  
// CS0662.cs using System.Runtime.InteropServices; interface I { void method([Out] ref int i);   // CS0662 // try one of the following lines instead // void method(ref int i); // void method([Out, In]ref int i); } class test { public static void Main() { } }  
```