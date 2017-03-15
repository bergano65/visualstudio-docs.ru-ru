---
title: "Ошибка компилятора CS1940 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1940"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1940"
ms.assetid: 546e9bba-725d-4ea9-826f-37ec9d832add
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1940
Обнаружено несколько реализаций шаблона запроса для типа источника "тип". Неоднозначный вызов метода "метод".  
  
 Эта ошибка возникает в том случае, если определено несколько реализаций метода запроса, и компилятор не может выбрать, какой из них лучше всего использовать для запроса. В следующем примере обе версии `Select` имеют одинаковые сигнатуры, так как они принимают одно значение `int` в качестве входного параметра и имеют `int` в качестве возвращаемого значения.  
  
### Исправление ошибки  
  
1.  Предоставьте только одну реализацию для каждого метода.  
  
## Пример  
 Следующий код приводит к возникновению ошибки CS1940:  
  
```  
// cs1940.cs using System; //must include explicitly for types defined in 3.5 class Test { public delegate int Dele(int x); int num = 0; public int Select(Func<int, int> d) { return d(this.num); } public int Select(Dele d) // CS1940 { return d(this.num) + 1; } public static void Main() { var q = from x in new Test() select x; } }  
```  
  
## См. также  
 [Standard Query Operators Overview](../Topic/Standard%20Query%20Operators%20Overview.md)