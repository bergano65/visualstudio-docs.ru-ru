---
title: "Ошибка компилятора CS0430 | Microsoft Docs"
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
  - "CS0430"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0430"
ms.assetid: b63c4f9a-b1cd-41d2-a02e-2ed0f177450f
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0430
В параметре \/reference не задан внешний псевдоним "псевдоним"  
  
 Эта ошибка возникает, если обнаружен внешний псевдоним, но псевдоним не был указан как ссылка в командной строке. Чтобы устранить ошибку CS0430, выполните компиляцию с параметром **\/reference**.  
  
## Пример  
  
```  
// CS0430_a.cs // compile with: /target:library public class MyClass {}  
```  
  
## Пример  
 При компиляции с параметром **\/reference:MyType\=cs0430\_a.dll** для ссылки на библиотеку DLL, созданную в предыдущем примере, эта ошибка устраняется. Следующий пример приводит к возникновению ошибки CS0430.  
  
```  
// CS0430_b.cs extern alias MyType;   // CS0430 public class Test { public static void Main() {} }  
  
```