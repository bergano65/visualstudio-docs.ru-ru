---
title: "Ошибка компилятора CS1623 | Microsoft Docs"
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
  - "CS1623"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1623"
ms.assetid: e52bc2d6-5116-40a2-90bc-23a3fa2c73e7
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1623
Итераторы не могут иметь параметры с ключевым словом ref или out.  
  
 Эта ошибка возникает, когда метод итератора принимает параметр `ref` или `out`. Чтобы избежать этой ошибки, удалите ключевое слово `ref` или `out` из сигнатуры метода.  
  
## Пример  
 Следующий пример приводит к возникновению ошибки CS1623:  
  
```  
// CS1623.cs using System.Collections; class C : IEnumerable { public IEnumerator GetEnumerator() { yield return 0; } // To resolve the error, remove ref public IEnumerator GetEnumerator(ref int i)  // CS1623 { yield return i; } // To resolve the error, remove out public IEnumerator GetEnumerator(out float f)  // CS1623 { f = 0.0F; yield return f; } }  
```