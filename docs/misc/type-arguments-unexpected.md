---
title: "Непредвиденные аргументы типа | Microsoft Docs"
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
  - "vbc32088"
  - "bc32088"
helpviewer_keywords: 
  - "BC32088"
ms.assetid: a0918e90-e7ad-4edc-81e1-584e6174bb6c
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Непредвиденные аргументы типа
Предложение `Implements` предоставляет аргументы типа для члена интерфейса, который оно реализует.  
  
 Предложение `Implements` должно определять только тот интерфейс и член, который оно реализует. Это означает, что если объявляется универсальная процедура, предложение `Of` и аргументы типа должны находиться в основной части объявления так же, как если бы процедура интерфейса не реализовывалась.  
  
 Приведенный ниже код может вызвать эту ошибку.  
  
```  
Public Interface testInterface Sub testSub(Of t)() End Interface Public Class testClass Implements testInterface Public Sub testSub() Implements testInterface.testSub(Of t)() End Sub End Class  
```  
  
 Объявление, предшествующее предложению `Implements`, должно выглядеть как определение интерфейса, за исключением возможного добавления модификатора доступа или процедуры. Приведенный ниже код позволяет избежать ошибки.  
  
```  
Public Sub testSub(Of t)() Implements testInterface.testSub  
```  
  
 **Идентификатор ошибки:** BC32088  
  
### Исправление ошибки  
  
-   Удалите список аргументов типа из предложения `Implements`.  
  
-   При реализации универсального члена интерфейса поместите список аргументов типа в основную часть объявления, предшествующую ключевому слову `Implements`.  
  
## См. также  
 [Implements](/dotnet/visual-basic/language-reference/statements/implements-clause)   
 [НЕ В СБОРКЕ. ключевое слово Implements и оператор Implements](http://msdn.microsoft.com/ru-ru/b96560f7-6413-480f-a1e2-f80253bab5be)   
 [Универсальные типы в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Универсальные процедуры в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Список типов](/dotnet/visual-basic/language-reference/statements/type-list)