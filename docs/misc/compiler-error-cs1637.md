---
title: "Ошибка компилятора CS1637 | Microsoft Docs"
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
  - "CS1637"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1637"
ms.assetid: 95aa82ab-bd52-4def-b5f3-d65e6dcb3855
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1637
Итераторы не могут иметь небезопасные параметры или типы yield.  
  
 Проверьте список аргументов итератора и тип операторов yield, чтобы убедиться, что не используются никакие небезопасные типы.  
  
## Пример  
 Следующий пример приводит к возникновению ошибки CS1637:  
  
```  
// CS1637.cs // compile with: /unsafe using System.Collections; public unsafe class C { public IEnumerator Iterator1(int* p)  // CS1637 { yield return null; } }  
```