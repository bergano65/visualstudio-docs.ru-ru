---
title: "Инициализатор массива не может указываться для переменной размерности; используйте пустой инициализатор &quot;{}&quot;. | Microsoft Docs"
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
  - "vbc30949"
  - "bc30949"
helpviewer_keywords: 
  - "BC30949"
ms.assetid: b3d27d9c-7a1f-4bac-ad71-388b24b807b3
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Инициализатор массива не может указываться для переменной размерности; используйте пустой инициализатор &quot;{}&quot;.
Массив инициализирует размерность, неизвестную во время компиляции.  
  
 Следующий код вызывает эту ошибку.  
  
```  
Dim j As Integer Dim intArray As Integer = New Integer(1, j) {{0, 100}, {1,101}}  
```  
  
 Следующий код позволяет избежать этой ошибки.  
  
```  
Dim intArray As Integer = New Integer(1, j) {} For i As Integer = 0 To j intArray(0, i) = i intArray(1, i) = 100 + i Next i  
```  
  
 **Идентификатор ошибки:** BC30949  
  
### Исправление ошибки  
  
-   Если это возможно, укажите постоянную размерность в объявлении массива.  
  
-   Если вы не можете указать постоянную размерность, необходимо инициализировать массив с помощью цикла, когда переменная размерность становится известной.  
  
## См. также  
 [Оператор For Each...Next](/dotnet/visual-basic/language-reference/statements/for-each-next-statement)   
 [НЕ В СБОРКЕ. Обзор массивов в Visual Basic](http://msdn.microsoft.com/ru-ru/ca50e2f2-b4d2-4c57-9169-9abbcc3392d8)   
 [Практическое руководство. Инициализация переменной массива в Visual Basic](../Topic/How%20to:%20Initialize%20an%20Array%20Variable%20in%20Visual%20Basic.md)   
 [НЕ В СБОРКЕ. Практическое руководство. Инициализация многомерного массива](http://msdn.microsoft.com/ru-ru/502dcf8b-d86c-46f1-ad7d-3ce809645774)