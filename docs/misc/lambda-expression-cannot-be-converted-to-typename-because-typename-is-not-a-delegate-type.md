---
title: "Лямбда-выражение не может быть преобразовано в тип &quot;&lt;имя_типа&gt;&quot;, так как &quot;&lt;имя_типа&gt;&quot; не является типом делегата. | Microsoft Docs"
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
  - "bc36625"
  - "vbc36625"
helpviewer_keywords: 
  - "BC36625"
ms.assetid: c03634d4-d831-4f8c-b6ab-566465968e4d
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Лямбда-выражение не может быть преобразовано в тип &quot;&lt;имя_типа&gt;&quot;, так как &quot;&lt;имя_типа&gt;&quot; не является типом делегата.
Лямбда\-выражения можно использовать, когда делегаты являются допустимыми. Их можно преобразовывать в совместимые типы делегатов, но не в какой\-либо другой тип. Например, можно определить тип делегата и присвоить ему лямбда\-выражение или отправить лямбда\-выражение в качестве аргумента в параметр <xref:System.Func%601>. Эти примеры показаны в приведенном ниже коде.  
  
```vb#  
Module Module1 Delegate Function FunDel(ByVal m As Integer) As Boolean Sub Main() ' Assign a lambda expression to a function delegate. Dim negative As FunDel = Function(n As Integer) n < 0 Console.WriteLine(negative(-3)) ' Send a lambda as the argument to a delegate parameter. Dim numbers() As Integer = {3, 4, 2, 8, 1, 0, 9, 13, 42} Dim evens = numbers.Where(Function(n) n Mod 2 = 0) For Each even In evens Console.WriteLine(even) Next End Sub End Module  
```  
  
 **Идентификатор ошибки:** BC36625  
  
## См. также  
 [Лямбда\-выражения](/dotnet/visual-basic/programming-guide/language-features/procedures/lambda-expressions)