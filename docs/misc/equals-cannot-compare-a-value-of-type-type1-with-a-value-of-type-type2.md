---
title: "Equals не может сопоставлять значение типа &quot;&lt;тип1&gt;&quot; со значением типа &quot;&lt;тип2&gt;&quot;. | Microsoft Docs"
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
  - "vbc36621"
  - "bc36621"
helpviewer_keywords: 
  - "BC36621"
ms.assetid: bd40bf57-3a12-407a-8622-7e428850c77c
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Equals не может сопоставлять значение типа &quot;&lt;тип1&gt;&quot; со значением типа &quot;&lt;тип2&gt;&quot;.
Оператор `Equals` в предложении `Join` или `Group Join` пытался сравнить один тип данных в другой способом, который не определен. Примером этого является сравнение значения `Boolean` с типом `Date`.  
  
 **Идентификатор ошибки:** BC36621  
  
### Исправление ошибки  
  
-   Убедитесь, что значения с каждой стороны оператора `Equals` можно преобразовать в общий тип данных. Далее приведены несколько вариантов, как можно это выполнить.  
  
    -   Используйте функцию `CType` для преобразования одного или нескольких значений в определенный тип.  
  
    -   Используйте класс <xref:System.Convert> или методы преобразования для преобразования одного или нескольких значений к общему неизменяемому типу.  
  
    -   Преобразуйте значения в строки с помощью метода `ToString`.  
  
## См. также  
 [Функция CType](/dotnet/visual-basic/language-reference/functions/ctype-function)   
 [Преобразование типов в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/type-conversions)   
 [Предложение Join](/dotnet/visual-basic/language-reference/queries/join-clause)   
 [Предложение Group Join](/dotnet/visual-basic/language-reference/queries/group-join-clause)   
 [Знакомство с LINQ в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [LINQ](/dotnet/visual-basic/programming-guide/language-features/linq/index)