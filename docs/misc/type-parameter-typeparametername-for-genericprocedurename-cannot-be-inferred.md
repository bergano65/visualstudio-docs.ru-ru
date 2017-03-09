---
title: "Параметр типа &quot;&lt;имя_параметра_типа&gt;&quot; для &quot;&lt;имя_универсальной_процедуры&gt;&quot; не может быть выведен | Microsoft Docs"
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
  - "vbc32050"
  - "bc32050"
helpviewer_keywords: 
  - "BC32050"
ms.assetid: e4a69ffb-0764-4e5a-8de1-40f881a3f4fb
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Параметр типа &quot;&lt;имя_параметра_типа&gt;&quot; для &quot;&lt;имя_универсальной_процедуры&gt;&quot; не может быть выведен
Универсальная процедура вызывается без указания списка аргументов типов, и для одного из аргументов типа не удается вывести тип.  
  
 Как правило, при вызове универсальной процедуры указывается аргумент типа для каждого параметра типа, определяемого этой процедурой. Тем не менее, существует возможность полностью опустить список аргументов типов. При этом компилятор пытается определить тип каждого аргумента типа из контекста вызова. Дополнительные сведения см. в разделе "Определение типа" статьи [Универсальные процедуры в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures).  
  
 Одной из возможных причин сбоя определения типа является несоответствие ранга параметра типа и вызываемого типа. Это проиллюстрировано в следующем коде.  
  
```  
Public Sub displayLargest(Of t As IComparable)(ByVal arg() As t) ' Insert code to find and display the largest element of arg(). End Sub Public Sub callGenericSub() Dim testValue As Integer findLargest(testValue) Dim testMatrix(,) As Integer findLargest(testMatrix) End Sub  
```  
  
 В приведенном выше коде оба вызова `findLargest` вызывают эту ошибку, поскольку параметр типа `t` запрашивает одномерный массив, тогда как аргументы типа, которые компилятор выводит из вызовов, являются скаляром \(`testValue`\) и двумерным массивом \(`testMatrix`\).  
  
 **Идентификатор ошибки:** BC32050  
  
### Исправление ошибки  
  
-   Убедитесь, что типы нормальных аргументов таковы, что определение типа согласуется с параметрами типов, объявленными для универсальной процедуры.  
  
     \-или\-  
  
-   Вызовите универсальную процедуру с полным списком аргументов типов, чтобы определение типа не требовалось.  
  
## См. также  
 [Универсальные типы в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Список типов](/dotnet/visual-basic/language-reference/statements/type-list)   
 [Универсальные процедуры в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)