---
title: "Многомерный массив нельзя преобразовать в дерево выражений | Microsoft Docs"
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
  - "bc36603"
  - "vbc36603"
helpviewer_keywords: 
  - "BC36603"
ms.assetid: 65eefab7-c7ad-4dcd-bebf-2d16fba9f28f
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Многомерный массив нельзя преобразовать в дерево выражений
Большинство выражений можно преобразовать в деревья выражений, за исключением многомерных массивов. Например, следующий код вызывает эту ошибку:  
  
```vb#  
Module Module1 Sub Main() '' A multi-dimensional array cannot be converted. 'Dim expTree As Expressions.Expression(Of Func(Of Object)) = _ '    Function() New Integer(1, 1) {{1, 2}, {2, 3}} ' A one-dimensional array can be converted. Dim expTree2 As Expressions.Expression(Of Func(Of Object)) = _ Function() New Integer() {1, 2, 3} End Sub End Module  
```  
  
 **Идентификатор ошибки:** BC36603  
  
## См. также  
 [НЕ В СБОРКЕ. Деревья выражений в LINQ](http://msdn.microsoft.com/ru-ru/1a2e8e74-4bbc-45ab-9a46-2b6cfce3bcb2)   
 [Практическое руководство. Использование деревьев выражений для построения динамических запросов](../Topic/How%20to:%20Use%20Expression%20Trees%20to%20Build%20Dynamic%20Queries%20\(C%23%20and%20Visual%20Basic\).md)   
 [НЕ В СБОРКЕ. Многомерные массивы в Visual Basic](http://msdn.microsoft.com/ru-ru/d92cad25-07e2-4d79-8ea4-ab269700f5de)