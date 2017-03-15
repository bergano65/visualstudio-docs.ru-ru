---
title: "Требуется Into. | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc36615"
  - "vbc36615"
helpviewer_keywords: 
  - "BC36615"
ms.assetid: 24062dd9-a973-43b6-88d3-c11adc5a3736
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Требуется Into.
Предложение `Aggregate`, `Group By` или `Group Join` было указано без оператора `Into`. Оператор `Into` используется для идентификации агрегатных функций, которые должны применяться к результатам запроса, и для определения члена типа результата запроса, который должен содержать сгруппированные результаты \(с помощью агрегатной функции `Group`\).  
  
 **Идентификатор ошибки:** BC36615  
  
### Исправление ошибки  
  
1.  Добавьте оператор `Into` в предложение `Aggregate`, `Group By` или `Group Join`. Ниже представлен пример такого кода.  
  
    ```vb#  
    Dim orders = From order In orderList _ Order By order.OrderDate _ Group By OrderDate = order.OrderDate _ Into OrdersByDate = Group  
    ```  
  
## См. также  
 [Предложение Aggregate](/dotnet/visual-basic/language-reference/queries/aggregate-clause)   
 [Предложение Group By](/dotnet/visual-basic/language-reference/queries/group-by-clause)   
 [Предложение Group Join](/dotnet/visual-basic/language-reference/queries/group-join-clause)   
 [Знакомство с LINQ в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [LINQ](/dotnet/visual-basic/programming-guide/language-features/linq/index)