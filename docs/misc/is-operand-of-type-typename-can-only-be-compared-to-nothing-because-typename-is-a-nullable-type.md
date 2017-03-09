---
title: "Операнд Is типа &quot;имя_типа&quot; может сравниваться только с Nothing, так как &quot;имя_типа&quot; является типом, допускающим значение null | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32127"
  - "bc32127"
helpviewer_keywords: 
  - "BC32127"
ms.assetid: 68b745b5-8605-4bf3-a6ec-69e67b3cff2d
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Операнд Is типа &quot;имя_типа&quot; может сравниваться только с Nothing, так как &quot;имя_типа&quot; является типом, допускающим значение null
Переменная, объявленная как допускающая значение null, сравнивалась с выражением, отличным от `Nothing`, с помощью оператора `Is`.  
  
 **Идентификатор ошибки:** BC32127  
  
### Исправление ошибки  
  
1.  Чтобы сравнить тип, допускающий значение null, с выражением, отличным от `Nothing`, с помощью оператора `Is`, вызовите метод `GetType` для типа, допускающего значение null, и сравните результат с выражением, как показано в следующем примере.  
  
    ```vb#  
    Dim number? As Integer = 5 If number IsNot Nothing Then If number.GetType() Is Type.GetType("System.Int32") Then End If End If  
    ```  
  
## См. также  
 [Типы значения, допускающие Null](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types)   
 [Оператор Is](/dotnet/visual-basic/language-reference/operators/is-operator)