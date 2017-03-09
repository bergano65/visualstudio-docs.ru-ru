---
title: "Атрибуты не могут применяться к параметрам лямбда-выражений | Microsoft Docs"
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
  - "vbc36634"
  - "bc36634"
helpviewer_keywords: 
  - "BC36634"
ms.assetid: ed751d8d-11b7-4210-97e0-0319edff8c34
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Атрибуты не могут применяться к параметрам лямбда-выражений
Атрибут был применен к параметру в определении лямбда\-выражения, что не поддерживается. Приведенный ниже код вызывает эту ошибку.  
  
```vb#  
Sub LambaAttribute()  
    ' Not valid.  
    Dim add1 = _  
    Function(<System.Runtime.InteropServices.InAttribute()> m As Integer) _  
                   m + 1  
End Sub  
```  
  
 **Идентификатор ошибки:** BC36634  
  
### Исправление ошибки  
  
-   Удалите атрибут или исправьте код, заменив лямбда\-выражение на обычную функцию.  
  
## См. также  
 <xref:System.Runtime.InteropServices.InAttribute>   
 [Лямбда\-выражения](/dotnet/visual-basic/programming-guide/language-features/procedures/lambda-expressions)   
 [НЕ В СБОРКЕ. Атрибуты в Visual Basic](http://msdn.microsoft.com/ru-ru/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)