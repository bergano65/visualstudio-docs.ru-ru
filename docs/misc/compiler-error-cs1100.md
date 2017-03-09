---
title: "Ошибка компилятора CS1100 | Microsoft Docs"
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
  - "CS1100"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1100"
ms.assetid: ea233371-36b6-49ae-a98c-a00ee3b79e53
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1100
Метод "имя" имеет модификатор параметра this, который не находится в первом параметре метода.  
  
 Модификатор `this` разрешен только в первом параметре метода, который сообщает компилятору, что метод является методом расширения.  
  
### Исправление ошибки  
  
1.  Удалите модификатор `this` из всех параметров метода, кроме первого.  
  
## Пример  
 В следующем коде возникает ошибка CS1100, поскольку параметр `this`  изменяет второй параметр:  
  
```  
// cs1100.cs static class Test { static void ExtMethod(int i, this Test c) // CS1100 { } }  
```  
  
## См. также  
 [Методы расширения](/dotnet/csharp/programming-guide/classes-and-structs/extension-methods)