---
title: "Операнды If не могут быть именованными аргументами | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc33105"
  - "vbc33105"
helpviewer_keywords: 
  - "BC33105"
ms.assetid: 596baeb6-a44f-4d92-beb7-06624b60c00d
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Операнды If не могут быть именованными аргументами
Использование именованных аргументов в операндах оператора `If` недопустимо. Следующий код вызывает эту ошибку.  
  
```  
Dim i As Integer Dim result As String ' Not valid. ' result = (If(i > 0, TruePart:="positive", FalsePart:="not positive")  
```  
  
 Это отличается от функции `IIf`, которая разрешает именованные аргументов, как показано в следующем коде:  
  
```  
' Valid. IIf(i > 0, TruePart:="positive", FalsePart:="not positive")  
```  
  
 **Идентификатор ошибки:** BC33105  
  
### Исправление ошибки  
  
-   Удалите назначения имен из операндов, как показано в следующем коде.  
  
    ```  
    result = If(i > 0, "positive", "not positive")  
    ```  
  
## См. также  
 [Оператор If](/dotnet/visual-basic/language-reference/operators/if-operator)   
 [Передача аргументов по позиции и по имени](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name)