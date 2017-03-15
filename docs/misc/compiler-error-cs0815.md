---
title: "Ошибка компилятора CS0815 | Microsoft Docs"
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
  - "CS0815"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0815"
ms.assetid: 8f055d34-9ee4-482e-9e79-8b3698c55cb4
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0815
Невозможно назначить "выражение" неявно типизированной локальной переменной  
  
 Выражение, которое используется в качестве инициализатора для неявно типизированной переменной, должно иметь тип. Поскольку выражения анонимных функций, выражения групп методов и выражение литерала null не имеют типа, они не используются в качестве инициализаторов. Нельзя инициализировать неявно типизированную переменную со значением null в ее объявлении, хотя потом ей можно назначить значение null.  
  
### Исправление ошибки  
  
1.  Предоставьте явный тип для переменной.  
  
## Пример  
 Следующий код приводит к возникновению ошибки CS0815:  
  
```  
// cs0815.cs class Test { public static int Main() { var d = s => -1; // CS0815 var e = (string s) => 0; // CS0815 var p = null;//CS0815 var del = delegate(string a) { return -1; };// CS0815 return -1; } }  
```  
  
## См. также  
 [Неявно типизированные локальные переменные](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)