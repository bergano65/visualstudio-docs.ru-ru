---
title: "Ошибка компилятора CS1951 | Microsoft Docs"
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
  - "CS1951"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1951"
ms.assetid: 799ba212-a000-44d9-b7da-a8c00eae63fa
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1951
Дерево лямбда\-выражения не может содержать параметры с ключевыми словами out и ref.  
  
 Дерево выражений лишь представляет выражения в виде структур данных. В нем не предусмотрен способ представления определенных мест в памяти, что необходимо при передаче параметра по ссылке.  
  
### Исправление ошибки  
  
1.  Единственная возможность устранить эту ошибку состоит в удалении модификатора `ref` в определении делегата и передаче параметра по значению.  
  
## Пример  
 Следующий пример приводит к возникновению ошибки CS1951:  
  
```  
// cs1951.cs using System.Linq; public delegate int TestDelegate(ref int i); class Test { static void Main() { System.Linq.Expressions.Expression<TestDelegate> tree1 = (ref int x) => x; // CS1951 } }  
```  
  
## См. также  
 [Деревья выражений](../Topic/Expression%20Trees%20\(C%23%20and%20Visual%20Basic\).md)