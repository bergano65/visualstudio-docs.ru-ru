---
title: "Ошибка компилятора CS0820 | Microsoft Docs"
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
  - "CS0820"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0820"
ms.assetid: 38c05162-ef20-42a8-9611-02698360dec5
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0820
Невозможно присвоить инициализатор массива неявно типизированной локальной переменной  
  
 Неявно типизированный массив — это массив, тип элементов которого выводится компилятором. Такой массив должен инициализироваться с помощью модификатора `new`\[\], как показано в приведенном ниже примере.  
  
### Исправление ошибки  
  
-   Используйте модификатор `new`\[\] с инициализатором массива.  
  
-   Не используйте неявно типизированную локальную переменную.  
  
## Пример  
 Приведенный ниже код приводит к возникновению ошибки CS0820 и демонстрирует правильный способ инициализации неявно типизированного массива.  
  
```  
//cs0820.cs class G { public static int Main() { var a = { 1,2,3}; //CS0820 // Try using one of the following lines instead. // var b = new[] { 1, 2, 3 }; //int[] b = {1, 2, 3}; return -1; } }  
```  
  
## См. также  
 [Неявно типизированные локальные переменные](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)