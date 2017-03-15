---
title: "Ошибка компилятора CS1642 | Microsoft Docs"
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
  - "CS1642"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1642"
ms.assetid: 2efeedf1-1839-485d-8b8c-9045df1951f0
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1642
Поля буферов фиксированного размера могут быть только членами структур.  
  
 Эта ошибка возникает, если поле буфера фиксированного размера используется в `class`, а не в `struct`. Чтобы устранить эту ошибку, измените `class` на `struct` или объявите это поле как обычный массив.  
  
## Пример  
 Следующий пример приводит к возникновению ошибки CS1642.  
  
```  
// CS1642.cs // compile with: /unsafe /target:library unsafe class C { fixed int a[10];   // CS1642 } unsafe struct D { fixed int a[10]; } unsafe class E { public int[] a = null; }  
```