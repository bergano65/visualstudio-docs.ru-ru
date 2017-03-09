---
title: "Ошибка компилятора CS0822 | Microsoft Docs"
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
  - "CS0822"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0822"
ms.assetid: 519091be-2332-4df4-acd9-e3b633966b3d
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0822
Неявно типизированные локальные переменные не могут быть константами.  
  
 Неявно типизированные локальные переменные необходимы только для хранения анонимных типов. Во всех остальных случаях они применяются только для удобства. Если значение переменной никогда не изменяется, просто задайте ей явный тип. Попытка использовать модификатор `readonly` с неявно типизированной локальной переменной вызовет ошибку CS0106.  
  
### Исправление ошибки  
  
1.  Если требуется, чтобы переменная была константой или `readonly`, задайте ей явный тип.  
  
## Пример  
 Следующий код приводит к возникновению ошибки CS0822:  
  
```  
// cs0822.cs class A { public static int Main() { const var x = 0; // CS0822.cs return -1; } }  
```  
  
## См. также  
 [Неявно типизированные локальные переменные](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)