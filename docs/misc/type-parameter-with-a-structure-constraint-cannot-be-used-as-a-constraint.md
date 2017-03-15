---
title: "Параметр типа с ограничением &quot;Structure&quot; нельзя использовать в качестве ограничения. | Microsoft Docs"
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
  - "vbc32114"
  - "bc32114"
helpviewer_keywords: 
  - "BC32114"
ms.assetid: 442b2048-9dc4-4223-bcfc-4d96bf8d14de
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Параметр типа с ограничением &quot;Structure&quot; нельзя использовать в качестве ограничения.
Параметр типа с ограничением `Structure` используется в качестве ограничения для другого параметра типа.  
  
 Ограничение `Structure` требует, чтобы аргумент типа, переданный в его параметр типа, был типом значения. Однако тип значения не может быть реализован или унаследован, поэтому нет смысла использовать его в качестве ограничения, для которого потребуется другой параметр типа для реализации или наследования от него.  
  
 Единственное осмысленное толкование этой ситуации заключается в том, что оба аргумента типа должны быть точно того же типа. Если это так, то универсальному типу требуется только один параметр типа.  
  
 Эту ошибку может вызвать следующая инструкция:  
  
 `Class c1(Of t1 As Structure, t2 As t1)`  
  
 Тип, передаваемый `t2`, не может реализовывать или наследовать тип, передаваемый в `t1`, поскольку тип, передаваемый в `t1`, должен быть типом значения.  
  
 **Идентификатор ошибки:** BC32114  
  
### Исправление ошибки  
  
-   Удалите параметр типа, ограниченный до `Structure`, из списка ограничений в другом параметре типа.  
  
-   Если оба параметра типа требуют одинаковый тип значения, определите универсальный тип с помощью только одного параметра типа.  
  
## См. также  
 [Универсальные типы в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Список типов](/dotnet/visual-basic/language-reference/statements/type-list)   
 [Структура \(Visual Basic\)](http://msdn.microsoft.com/ru-ru/263ce115-ac36-4c05-8cb7-0e0eead5c6d0)   
 [Типы значений и ссылочные типы](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)