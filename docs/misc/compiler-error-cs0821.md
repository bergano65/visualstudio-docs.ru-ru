---
title: "Ошибка компилятора CS0821 | Microsoft Docs"
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
  - "CS0821"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0821"
ms.assetid: ef449115-93e8-4fa5-848a-d30dc7f68ddf
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0821
Неявно типизированные локальные переменные не могут быть фиксированными  
  
 Неявно типизированные локальные переменные и анонимные типы не поддерживаются в контексте `fixed`.  
  
### Исправление ошибки  
  
1.  Либо удалите модификатор `fixed` из переменной, либо задайте для переменной явный тип.  
  
## Пример  
 В следующем коде возникает ошибка CS0821:  
  
```  
class A { static int x; public static int Main() { unsafe { fixed (var p = &x) { } } return -1; } }  
```  
  
## См. также  
 [Неявно типизированные локальные переменные](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)