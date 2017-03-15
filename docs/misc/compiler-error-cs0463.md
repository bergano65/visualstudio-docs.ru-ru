---
title: "Ошибка компилятора CS0463 | Microsoft Docs"
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
  - "CS0463"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0463"
ms.assetid: 0cb4be4e-86ea-4ade-8817-b17d4cacd4d5
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0463
Ошибка при вычислении выражения с десятичной константой: "ошибка"  
  
 Эта ошибка происходит в случае переполнения десятичного константного выражения во время компиляции.  
  
 Обычно ошибки переполнения происходят во время выполнения. В этом случае константное выражение определено таким образом, что компилятор может оценить результат и установить, что произойдет переполнение.  
  
## Пример  
 Приведенный ниже код вызывает ошибку CS0463.  
  
```  
// CS0463.cs using System; class MyClass { public static void Main() { const decimal myDec = 79000000000000000000000000000.0m + 79000000000000000000000000000.0m; // CS0463 Console.WriteLine(myDec.ToString()); } }  
```