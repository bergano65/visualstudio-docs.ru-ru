---
title: "Для Option Strict On необходимо, чтобы каждый параметр лямбда-выражения объявлялся с конструкцией As, если его тип не удается вывести. | Microsoft Docs"
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
  - "bc36642"
  - "vbc36642"
helpviewer_keywords: 
  - "BC36642"
ms.assetid: 2aaa62b8-49c9-4ae8-b0f5-08e3f0b5ad10
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Для Option Strict On необходимо, чтобы каждый параметр лямбда-выражения объявлялся с конструкцией As, если его тип не удается вывести.
Параметр в лямбда\-выражении был объявлен без использования предложения `As`, с `Option Strict` on.  
  
```  
' Not valid when Option Strict is on. ' Dim increment1 = Function (n) n + 1  
```  
  
 Предыдущее объявление допустимо, если тип `n` может быть определен. Например, если предыдущее лямбда\-выражение назначается делегату функции `Del`:  
  
```  
Delegate Function Del(ByVal p As Integer) As Integer  
```  
  
 Теперь тип `n` может быть выведен из параметра `p`:  
  
```  
Dim increment2 as Del = Function(n) n + 1  
```  
  
 **Идентификатор ошибки:** BC36642  
  
### Исправление ошибки  
  
-   Добавьте предложение `As` в объявление параметра:  
  
    ```  
    Dim increment3 = Function (n As Integer) n + 1  
    ```  
  
## См. также  
 [Лямбда\-выражения](/dotnet/visual-basic/programming-guide/language-features/procedures/lambda-expressions)