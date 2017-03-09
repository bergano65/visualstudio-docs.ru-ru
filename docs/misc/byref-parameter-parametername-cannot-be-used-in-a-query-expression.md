---
title: "Параметр ByRef &quot;&lt;имя_параметра&gt;&quot; нельзя использовать в выражении запроса | Microsoft Docs"
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
  - "vbc36533"
  - "bc36533"
helpviewer_keywords: 
  - "BC36533"
ms.assetid: 8067ac87-dd6b-4869-87d0-8a4ce272de41
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Параметр ByRef &quot;&lt;имя_параметра&gt;&quot; нельзя использовать в выражении запроса
Параметр, входящий в запрос LINQ, имеет тип указателя. Параметры, используемые в выражениях запроса, не могут передаваться по ссылке.  
  
 **Идентификатор ошибки:** BC36533  
  
### Исправление ошибки  
  
1.  Объявите новую переменную и присвойте ее значение копии передаваемого по ссылке значения. Используйте в запросе LINQ скопированную переменную. Ниже представлен пример такого кода.  
  
    ```vb#  
    Sub RunQuery(ByVal collection As List(Of Integer), _  
                 ByRef filterValue As Integer)  
        Dim fv = filterValue  
        Dim queryResult = From num In collection _  
                          Where num < fv  
    End Sub  
    ```  
  
### Исправление ошибки  
  
1.  Для параметра, используемого в запросе, замените ключевое слово `ByRef` ключевым словом `ByVal`.  
  
## См. также  
 [Различия между передачей аргумента по значению и по ссылке](/dotnet/visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference)   
 [Знакомство с LINQ в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [LINQ](/dotnet/visual-basic/programming-guide/language-features/linq/index)